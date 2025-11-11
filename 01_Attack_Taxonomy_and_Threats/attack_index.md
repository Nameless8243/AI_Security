---
version: "3.3"
section_type: "attack_index"
agent: "Index Architect"
---
🚨 COPY START 🚨
# AI Attack Taxonomy  
*Foundations of Adversarial Threats*

---

## 🌍 Introduction to AI Attack Taxonomy  

**EN:**  
Artificial Intelligence systems, like any complex software ecosystem, are vulnerable to a wide spectrum of attacks. But unlike classical cyberattacks that target operating systems or networks, AI attacks often exploit the *data, model, or learning process itself*. Understanding these categories systematically is essential for building a robust [[ai_security_framework|AI Security Framework]].  

**HU:**  
A mesterséges intelligencia rendszerek — akárcsak más szoftveres ökoszisztémák — számos támadástípusnak vannak kitéve. Azonban míg a hagyományos támadások az operációs rendszert vagy a hálózatot célozzák, az AI támadások magát az *adatot, a modellt vagy a tanulási folyamatot* támadják meg. E kategóriák rendszerezett megértése alapvető a robusztus [[ai_security_framework|AI biztonsági keretrendszer]] felépítéséhez.  

---

## 🧩 The Three Core Attack Surfaces  

**EN:**  
At a high level, we can divide AI threats into **three interconnected layers**, representing the attack surfaces:  

1. **Data Layer (Training + Input):** Attacks such as [[data_poisoning|Data Poisoning]] and [[adversarial_examples|Adversarial Examples]] inject malicious or misleading inputs to manipulate the model’s perception.  
2. **Model Layer:** Includes [[model_stealing_and_extraction|Model Extraction]], [[membership_inference_attacks|Membership Inference]], and [[model_evasion|Evasion Attacks]], where the adversary targets model parameters or predictions.  
3. **Pipeline & Infrastructure Layer:** Threats against deployment and supply chain, like [[model_backdoors|Backdoors]], [[ai_supply_chain_attacks|AI Supply Chain Attacks]], or compromised APIs.  

**HU:**  
Magas szinten az AI-támadások **három összekapcsolt rétegre** bonthatók, melyek az egyes támadási felületeket képviselik:  

1. **Adatszint (Tréning + Bemenet):** Olyan támadások, mint az [[data_poisoning|Adatmérgezés]] vagy az [[adversarial_examples|Ellenséges példák]], amelyek hamis adatokat fecskendeznek be a modell megtévesztésére.  
2. **Modellszint:** Ide tartozik a [[model_stealing_and_extraction|Modell-lopás]], a [[membership_inference_attacks|Tagsági következtetés]] vagy a [[model_evasion|Elkerülési támadások]], ahol a támadó a modell paramétereit vagy kimeneteit célozza.  
3. **Infrastruktúra és pipeline szint:** A telepítési és ellátási láncot támadó módszerek, mint a [[model_backdoors|Hátsó kapuk]], az [[ai_supply_chain_attacks|Ellátási lánc támadások]] vagy a veszélyeztetett API-k.  

---

## ⚙️ How AI Attacks Differ from Classical Cyberattacks  

**EN:**  
Traditional cybersecurity assumes *fixed logic* — but AI systems *learn* and thus are *mutable by data*. Attackers can subtly alter the training or inference environment, causing the model to behave maliciously or reveal sensitive information. This mutability makes the attack surface fundamentally different: attacks can be enacted by influencing data, not only by compromising code or infrastructure.

**HU:**  
A hagyományos kiberbiztonság *fix logikával* dolgozik, míg az AI rendszerek *tanulnak*, így *adat által módosíthatók*. A támadók képesek apró változtatásokkal befolyásolni a tanulási vagy inferencia-környezetet, hogy a modell hibásan viselkedjen vagy érzékeny információt „kiszivárogtasson”. Ez a rugalmasság alapvetően más támadási felületet eredményez: a támadásokat gyakran az adaton keresztül viszik véghez, nem csak kód vagy infrastruktúra kompromittálásával.

Mathematically, a canonical adversarial perturbation can be written in raw LaTeX form so it remains visible and portable in Obsidian:

$$
x' = x + \epsilon \cdot \mathrm{sign}(\nabla_x L(\theta, x, y))
$$

This shows how a small, carefully chosen vector \(\epsilon\) — imperceptible to humans in many domains — can change the model's prediction because it follows the loss gradient direction.

---

## 💡 Why Taxonomy Matters  

**EN:**  
Taxonomies help standardize understanding. By classifying attacks under clear categories — *data, model, pipeline* — defenders can design layered mitigations aligned with the [[nist_ai_rmf|NIST AI RMF]] and [[mitre_atlas|MITRE ATLAS]] frameworks. A clear taxonomy drives threat modeling, test-case creation, and compliance mapping: it tells you *where* to instrument logging, *what* to fuzz, and *which* tests must be part of CI.

**HU:**  
A taxonómia segíti a rendszerezett gondolkodást. A támadások világos kategóriákba sorolásával — *adat, modell, pipeline* — a védelmi rétegek összehangolhatók a [[nist_ai_rmf|NIST AI RMF]] és a [[mitre_atlas|MITRE ATLAS]] keretrendszerekkel. A jól meghatározott taxonómia irányt ad a fenyegetésmodellezéshez, a tesztesetek kialakításához és a megfelelőségi térképezéshez: megmutatja, *hol* kell naplózni, *mit* kell fuzzerelni, és *mely* teszteket kell CI-be beépíteni.

---

## 🧠 Example Scenario: Manipulating a Facial Recognition System  

**EN:**  
Imagine a facial recognition model trained on millions of images. A threat actor injects only 0.5% poisoned data during training, subtly blending their own face with that of a VIP target. During deployment, the model now *accepts the attacker as the VIP* when wearing specific accessories (e.g., sunglasses). This is a hybrid of [[data_poisoning|data poisoning]] and [[model_backdoors|backdoor attacks]].

Lifecycle view: injection → persistence (artifact in weights or preprocessing) → activation (trigger during inference). For defenders, map each lifecycle phase to controls: provenance collection at ingestion, anomaly detection on training set statistics, controlled retraining with verified datasets, and targeted red-team tests for trigger activation.

**HU:**  
Képzelj el egy arcfelismerő modellt, amely millió képen tanult. Egy rosszindulatú szereplő a tréningadatok közé csupán 0,5% mérgezett példát juttat be, finoman összekeverve a saját arcát egy VIP célpont képével. A kihelyezett rendszer ezután *a támadót VIP-ként azonosítja*, ha az bizonyos kiegészítőt visel (pl. napszemüveg). Ez az [[data_poisoning|adatmérgezés]] és a [[model_backdoors|hátsó kapu]] tipikus kombinációja.

A támadás életciklusa: befecskendezés → perzisztencia (súlyokban vagy előfeldolgozásban megmaradó artefaktum) → aktiválás (trigger az inferenciánál). A védelemhez rendeld a kontrollokat az életciklus fázisaihoz: provenance gyűjtés a beadásnál, anomália-detektálás a tréning statisztikákon, ellenőrzött újratanítás validált adatokkal, valamint célzott red-team tesztek a trigger aktiválására.

---

## 🛡️ Defense Context  

**EN:**  
Each layer in the taxonomy corresponds to its defense class:

- Data-level threats → [[data_validation_and_sanitization|Data Validation & Sanitization]], dataset provenance, input filtering, differential testing of preprocessing.
- Model-level threats → [[adversarial_training|Adversarial Training]], [[differential_privacy|Differential Privacy]], model hardening and robustness testing, membership inference audits.
- Pipeline-level threats → [[model_certification_and_testing|Model Certification]], signed artifacts, secure CI/CD, supply-chain audits, and [[zero_trust_for_ai|Zero Trust for AI]] principles.

Defenses are most effective when combined. For example, provenance + DP + adversarial testing reduces both leakage and poisoning risk. Always map mitigations to attack *phases* (reconnaissance, insertion, persistence, activation, exfiltration) and create CI gates that simulate realistic adversarial behaviors.

**HU:**  
A taxonómia minden rétegéhez külön védekezési osztály tartozik:

- Adatszintű fenyegetések → [[data_validation_and_sanitization|Adattisztítás és érvényesítés]], adatkészlet-provenance, bemenet-szűrés, előfeldolgozás differenciális tesztelése.
- Modellszintű fenyegetések → [[adversarial_training|Ellenséges tréning]], [[differential_privacy|Differenciális adatvédelem]], modell-megerősítés és robosztussági tesztelés, tagsági következtetés auditok.
- Pipeline-szintű fenyegetések → [[model_certification_and_testing|Modell-tanúsítás]], aláírt artefaktok, biztonságos CI/CD, ellátási lánc auditok és a [[zero_trust_for_ai|Zero Trust az AI-ban]] elvei.

A védekezések akkor működnek igazán jól, ha kombináljuk őket. Például provenance + DP + adversarial tesztelés egyszerre csökkenti az adat-szivárgást és az adatmérgezés kockázatát. Mindig rendeld a mitigációkat a támadás *fázisaihoz* (felderítés, befecskendezés, perzisztencia, aktiválás, adatlopás), és építs CI kapukat, amelyek valósághű ellenfeleket szimulálnak.

---

## ⚖️ Summary  

**EN:**  
The AI Attack Taxonomy is the foundation of understanding AI security. Every other defense, assurance, or governance mechanism builds on this structure — knowing *where* an attack happens defines *how* it must be mitigated. Use the taxonomy as the first column in threat models and as the organizing principle for red/blue team exercises.

**HU:**  
Az AI támadási taxonómia az AI-biztonság megértésének alapja. Minden más védekezési, ellenőrzési vagy irányítási megoldás erre a struktúrára épül — ha tudjuk, *hol* történik a támadás, azt is meghatározhatjuk, *hogyan* védekezzünk ellene. Használd ezt a taxonómiát a fenyegetésmodellezés első oszlopaként és rendezőelvként a red/blue team gyakorlatokhoz.

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. What are the three main layers of the AI attack taxonomy, and what kind of attacks belong to each?  
2. How does an adversarial example differ from a data poisoning attack, and why does the distinction matter for defenses?  
3. Explain why AI models can be more vulnerable than traditional software systems — give a concrete example and map mitigations to the attack phases.  
4. Show, using the raw LaTeX block format, how a small perturbation on input \(x\) can be written to demonstrate an adversarial example.  
5. Which industry frameworks align with this taxonomy, and how would you map one defense (e.g., adversarial training) to the taxonomy layers?

---

> *“To understand an adversary, you must first understand what your system believes.”*

---
🚨 COPY END 🚨
