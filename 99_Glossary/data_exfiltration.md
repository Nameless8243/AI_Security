---
id: data_exfiltration
title: "Data Exfiltration / Adatszivárgás"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "01_Glossary"
agent: "Threat Mapper"
tags:
  - ai_security
  - glossary
  - underscore_slug
---
# Data Exfiltration

_How models — unintentionally or maliciously — leak sensitive information_

---

## 🌍 Introduction

**EN:**  
Data exfiltration in the AI context is the process by which sensitive information leaves a protected boundary via an AI system. This can happen intentionally (a compromised component sending secrets out) or unintentionally (a model that memorized and later reveals private training data). Modern systems — with APIs, logs, and user-facing completions — provide many channels for leakage. Understanding exfiltration means treating the model and its surrounding infra as potential _data egress vectors_, not just compute artifacts.

**HU:**  
Az adatkiszivárgás (data exfiltration) AI-környezetben azt jelenti, hogy érzékeny információ kerül ki egy védett határon keresztül az AI rendszer révén. Ez történhet szándékosan (kompromittált komponens szivárogtat) vagy véletlenül (a modell memorizált adatokat ad vissza). A mai rendszerek — API-k, logok, felhasználói válaszok — sok csatornát kínálnak a szivárgásra. Az exfiltráció megértése azt jelenti, hogy a modellt és a környezetét potenciális _kimeneti csatornákként_ kell kezelni, nem csak számítási egységekként.

---

## 🧠 Why AI Changes the Exfiltration Game

**EN:**  
AI systems blend storage, computation, and communication. Unlike traditional databases where leaks are obvious (files copied, DB dumps), models can _encode_ information in subtle ways — logits, completions, embeddings, or even timing differences. Moreover, attackers can manipulate inputs (prompt engineering, steganographic payloads) to coax models into producing sensitive content. The attacker’s toolbox includes both direct probes (query-response) and covert techniques (covert channels embedded in outputs).

**HU:**  
Az AI rendszerek tárolást, számítást és kommunikációt ötvöznek. Ellentétben a hagyományos adatbázisokkal, ahol a kiszivárgás egyértelmű (fájlok másolása, dump-ok), a modellek az információt finom módon _kódolhatják_ — logitek, kiegészítések, embeddingek vagy akár időzítési különbségek formájában. Ráadásul a támadók az inputok manipulálásával (prompt-engineering, steganográfiai payloadok) is kicsalhatják az érzékeny tartalmat. A támadók eszköztára közvetlen próbákat (lekérdezés-válasz) és covert csatornákat egyaránt tartalmaz.

---

## ⚙️ Main Exfiltration Channels

**EN:**

1. **Output Retrieval (Direct):** the model outputs memorized data verbatim (e.g., PII, API keys) when given certain prompts — overlaps with [[model_inversion|Model Inversion]] and [[membership_inference_attacks|Membership Inference]].
    
2. **Steganographic Outputs:** attackers design prompts that cause the model to embed data in innocuous-looking text or images (e.g., hidden base64 within prose).
    
3. **Embedding Leakage:** vector databases return embeddings or similarity scores that can be probed to reconstruct original documents or reveal membership.
    
4. **Side Channels:** timing, error messages, or resource-usage patterns reveal internal state or data about training/serving artifacts.
    
5. **Compromised Pipelines:** CI/CD, model registries, or dataset stores that are exfiltrated by malicious insiders or supply-chain compromises.
    

Each channel requires different defensive approaches — from output filtering to provenance and runtime isolation.

**HU:**

1. **Kimenet-alapú kinyerés (közvetlen):** a modell pontosan visszaadja a memorizált adatot (pl. személyes adatok, API-kulcsok) bizonyos promptokra — ez átfedés a [[model_inversion|modell-inverzió]] és a [[membership_inference_attacks|tagsági támadások]] területével.
    
2. **Szteganográfiai kimenetek:** a támadók olyan promptokat terveznek, amelyek a modellt ártalmatlan szövegbe vagy képekbe rejtett adatok beágyazására késztetik (pl. base64 kódok prózában).
    
3. **Embedding-szivárgás:** a vektoradatbázisokból visszakapott embeddingek vagy similarity score-ok vizsgálatával visszaállíthatók eredeti dokumentumdarabok vagy felfedhető a tagság.
    
4. **Oldalcsatornák:** időzítés, hibajelzések vagy erőforrás-használati mintázatok fedhetnek fel belső állapotokat vagy adatinformációt.
    
5. **Kompromittált pipeline-ok:** CI/CD, modellregiszterek vagy adattárolók, amelyeket rosszindulatú belső szereplők vagy ellátási lánc támadások használnak exfiltrációra.
    

Minden csatornához más-más védekezési stratégiák szükségesek — a kimenetszűréstől a provenance-ig és a futtatási izolációig.

---

## 🧩 Concrete Attack Patterns

**EN:**

- **Prompt-based retrieval:** craft a prompt that includes a guessed prefix of a secret; model completes the secret.
    
- **Split-query reconstruction:** submit overlapping prompts and stitch completions to recover longer secrets.
    
- **Embedding inversion:** use many queries to a vector store to approximate and reconstruct source text from embeddings.
    
- **Covert channel via formatting:** request outputs with specific whitespace/formatting patterns that encode bits of a secret.
    
- **Insider exfiltration:** a developer with access to model registries or training data exfiltrates artifacts via private endpoints.
    

These patterns may combine: a prompt-engineered probe can use embeddings and then text prompts to refine and reconstruct data.

**HU:**

- **Prompt-alapú kinyerés:** olyan promptot készítenek, amely tartalmaz egy feltételezett titkos előtagot; a modell befejezi a titkot.
    
- **Felhasadó-lekérdezés (split-query):** átfedő promptokkal részleteket kérnek le, majd összeillesztik a részleteket hosszabb titkok visszaállításához.
    
- **Embedding-inverzió:** sok lekérdezéssel a vektor-adatbázisokból megközelítik és rekonstruálják a forrásszöveget az embeddingekből.
    
- **Covert csatorna formázással:** speciális szóközölési/formázási mintákat kérnek, amelyek bitként kódolnak információt.
    
- **Belső szereplő általi kiszivárogtatás:** olyan fejlesztő, aki hozzáfér a modellig vagy tréningadatokhoz, privát végpontokon keresztül viszi ki az artefaktokat.
    

Ezek a minták kombinálhatók: a prompt-engineeringes próba embeddingeket használva finomítható szöveges lekérdezésekké az adatrekonstrukció.

---

## 🛡️ Defensive Strategies

**EN:**  
Defending against exfiltration requires layered controls, policy, and runtime detection:

- **Strict output governance:** redact or filter PII, limit raw logits and full-text completions; return only top-k labels or paraphrased answers. Tie this to [[model_certification_and_testing|certified behavior]] requirements.
    
- **Query monitoring & anomaly detection:** detect probing patterns (repetitive overlap queries, high-entropy outputs) indicative of exfiltration attempts.
    
- **Rate limiting & client authentication:** throttle suspicious clients and require strong identity for high-volume access. Integrate with [[zero_trust_for_ai|Zero Trust for AI]].
    
- **Embedding controls:** avoid returning raw embeddings; use hashed or tokenized similarity services, or perform similarity-only operations server-side without exposing vectors.
    
- **Provenance & SBOM:** track dataset and model lineage so you can quickly identify which artifact could contain leaked material (→ [[ai_sbom_and_mbom_management|AI SBOM]]).
    
- **Differential privacy & memorization checks:** train with privacy guarantees and run membership/memorization audits before deployment (refer to [[membership_inference_attacks|Membership Inference]]).
    
- **Runtime isolation & sandboxing:** isolate untrusted user code or third-party adapters to prevent lateral movement.
    
- **Logging & encrypted telemetry:** capture detailed audit trails (while protecting logs themselves) to support forensic analysis.
    

**HU:**  
Az exfiltráció elleni védelem rétegzett kontrollt, szabályzatot és futtatás közbeni detektálást igényel:

- **Szigorú kimenet-irányítás:** személyes adatok redakálása, nyers logitek és teljes szöveges kimenetek korlátozása; csak top-k címkék vagy parafrázis visszaadása. Kapcsold ezeket a [[model_certification_and_testing|tanúsított viselkedési]] követelményekhez.
    
- **Lekérdezés-monitorozás és anomália-észlelés:** felismerni a módszeres faggató mintákat (ismétlődő, átfedő lekérdezések, magas entrópiájú kimenetek) mint exfiltrációs kísérletek.
    
- **Rate limiting és kliens-hitelesítés:** gyanús klienslekérdezések lassítása, nagy forgalom esetén erős identitáskövetelmény. Integráld a [[zero_trust_for_ai|Zero Trust]] elvekkel.
    
- **Embedding-kontrollok:** ne add vissza a nyers embeddingeket; használj meghatározott similarity API-kat, amelyek nem szolgáltatnak vektort, vagy hash-eld a vektorokat.
    
- **Eredetkövetés és SBOM:** kövesd a dataset- és modell-láncolatot, így gyorsan azonosítható, melyik artefaktum tartalmazhatott kiszivárgott anyagot (→ [[ai_sbom_and_mbom_management|AI SBOM]]).
    
- **Differenciális adatvédelem és memorizáció-ellenőrzés:** privát garanciával trenírozni és tagsági/memorizációs auditokat futtatni élesítés előtt (→ [[membership_inference_attacks|Tagsági támadások]]).
    
- **Futtatási izoláció és sandbox:** elkülöníteni a nem megbízható felhasználói kódot vagy harmadik féltől származó adaptereket a laterális mozgás megakadályozására.
    
- **Naplózás és titkosított telemetria:** részletes audit-pályák rögzítése (miközben a naplókat magukat is véded) a vizsgálatok támogatására.
    

---

## 🧩 Detection Signals & Incident Response

**EN:**  
Detection indicators include: unusual query patterns (systematic prefix probes), spikes in high-entropy completions, repeated queries that produce overlapping completions, or unexpected outbound traffic from model-serving nodes. Incident response should include: immediate throttling and blocking, forensic snapshot (model & dataset hashes, recent queries), rolling model rollback (if reversible), and regulatory/legal notification if PII is confirmed exfiltrated. Ensure playbooks include steps to preserve chain-of-custody for audits.

**HU:**  
Detektálási jelek lehetnek: szokatlan lekérdezési minták (rendszeres prefix-próbálkozások), magas entrópiájú kimenetek hirtelen megjelenése, ismétlődő lekérdezések amelyek átfedő befejezéseket adnak, vagy váratlan kimenő forgalom a modell-futtató csomópontokról. Az incidensre adott válasz tartalmazza: azonnali korlátozás/blokkolás, forenzikus pillanatfelvétel (modell- és adat-hash-ek, a legutóbbi lekérdezések), modell-visszaállítás (ha lehetséges), és szabályozói/jogi értesítés, ha személyként azonosítható adatok szivárogtak. A cselekvési tervekben szerepeljen a chain-of-custody megőrzése auditokhoz.

---

## ⚖️ Governance & Policy Controls

**EN:**  
Technical controls must be complemented by policy: data classification, least-privilege access to datasets and model artifacts, contractual controls with third-party model providers, and clear rules for redaction and retention. Make exfiltration risk part of model acceptance criteria: if a candidate model or dataset increases measurable exfiltration risk, it must be rejected or mitigated before deployment.

**HU:**  
A technikai kontrollokat politikai intézkedések egészítik ki: adat-osztályozás, legkisebb jogosultság elve a datasetekhez és modell-artefaktumokhoz, szerződéses záradékok harmadik fél modell-szolgáltatókkal, valamint világos szabályok a redakcióra és megőrzésre. Az exfiltrációs kockázat legyen része a modell-elfogadási kritériumoknak: ha egy modell vagy adatkészlet növeli a mérhető kiszivárgási kockázatot, el kell utasítani vagy elő kell készíteni a mitigációt élesítés előtt.

---

## 🔭 Research & Open Challenges

**EN:**  
Open problems include provable detection of covert channels in generative outputs, scalable privacy constraints for vector stores, and robust metrics for quantifying exfiltration risk across multimodal systems. Research into provable “machine forgetting,” encrypted inference, and verifiable computation promises new guardrails — but operationalizing them at scale remains a challenge.

**HU:**  
Nyitott problémák: provably detektálható covert csatornák a generatív kimenetekben, skálázható adatvédelmi korlátok vektoradatbázisokra, és robosztus metrikák az exfiltrációs kockázat mérésére multimodális rendszerekben. A „gépi felejtés”, titkosított inferencia és verifikálható számítás kutatása új védősávokat ígér, de ezek éles, nagy léptékű bevezetése még kihívás.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. Name five distinct channels through which AI systems can exfiltrate data.
    
2. How can embeddings lead to reconstruction of source text?
    
3. What runtime signals are typical for exfiltration attempts?
    
4. Why should model acceptance criteria include exfiltration risk assessment?
    
5. Describe one policy and one technical control that reduce exfiltration risk.
    

---

> _“Secrecy in AI is not a perimeter problem only — it is a behavior problem. Watch what it says, not just where it sits.”_