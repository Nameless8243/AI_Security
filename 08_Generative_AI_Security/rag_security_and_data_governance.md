---
version: "3.3"
section_type: "genai_security"
agent: "Core Concepts Engineer"
---
---
title: RAG Security and Data Governance / RAG-biztonság és adatirányítás
phase: Foundation
category: AI Architecture & Governance
difficulty: Advanced
related: [data_provenance_and_integrity, ai_governance_and_policy, security_as_code_and_ci_cd_integration, continuous_validation_and_review, model_alignment_and_red_teaming]
updated: 2025-11-11
---

## 🧩 RAG Security and Data Governance / RAG-biztonság és adatirányítás

**EN:**  
**Retrieval-Augmented Generation (RAG)** combines generative reasoning with external knowledge retrieval — allowing models to produce contextually accurate, up-to-date, and domain-specific outputs. However, RAG architectures also create new **attack surfaces** and **governance risks**, since retrieved data directly influences generated content.  

**HU:**  
A **Retrieval-Augmented Generation (RAG)** a generatív gondolkodást külső tudás-visszakereséssel ötvözi — lehetővé téve, hogy a modellek kontextusban pontos, naprakész és szakterületi kimeneteket hozzanak létre. A RAG-architektúrák azonban új **támadási felületeket** és **irányítási kockázatokat** is teremtenek, mivel a visszakeresett adatok közvetlenül befolyásolják a generált tartalmat.

---

## 💡 Concept Overview / Fogalmi áttekintés

**EN:**  
RAG security ensures that the retrieval layer — databases, vector stores, and API connectors — cannot be exploited for prompt injection, data exfiltration, or misinformation propagation. Data governance defines **who retrieves what, from where, and under what policy context**.  

**HU:**  
A RAG-biztonság biztosítja, hogy a visszakeresési réteg — adatbázisok, vektortárolók és API-kapcsolatok — ne legyen kihasználható prompt-injektálásra, adatkiszivárogtatásra vagy félretájékoztatás terjesztésére. Az adatirányítás meghatározza, **ki, mit, honnan és milyen szabályzati környezetben kereshet vissza**.

---

## 🧠 Core Idea / Alapgondolat

**EN:**  
RAG systems merge **knowledge retrieval** and **language generation**, so any compromise in one layer affects the other. Therefore, both data and model governance must operate in unison — ensuring retrieved information is trustworthy, non-toxic, and policy-compliant before it shapes the output.  

**HU:**  
A RAG-rendszerek a **tudás-visszakeresést** és a **nyelvi generálást** egyesítik, így bármelyik réteg kompromittálódása a másikat is érinti. Ezért az adat- és modellirányításnak összehangoltan kell működnie — biztosítva, hogy a visszakeresett információ megbízható, nem toxikus és szabályzat-kompatibilis legyen, mielőtt befolyásolja a kimenetet.

---

## ⚙️ RAG Architecture and Threat Surface / A RAG-architektúra és a támadási felület

**EN:**  
The RAG pipeline includes:  
1. **User query (prompt)** →  
2. **Retriever** (vector store, search API) →  
3. **Ranker/filter** (relevance and trust scoring) →  
4. **Generator** (LLM synthesis) →  
5. **Post-processing guardrails.**

Each stage introduces vulnerabilities — from malicious embeddings to poisoned document retrieval or unauthorized data exposure.  

**HU:**  
A RAG-folyamat elemei:  
1. **Felhasználói kérés (prompt)** →  
2. **Visszakereső modul** (vektortároló, kereső API) →  
3. **Rangsoroló/szűrő** (relevancia és bizalmi pontozás) →  
4. **Generátor** (LLM-szintézis) →  
5. **Utófeldolgozó védősínek.**

Minden szakasz sebezhetőségeket hordoz — a rosszindulatú embeddingektől a mérgezett dokumentum-visszakeresésig vagy az engedély nélküli adatfeltárásig.

---

## 🧮 RAG Trust Function / RAG bizalmi függvény

**EN:**  
RAG trust (**RT**) depends on data integrity (**D**), access control strength (**A**), and retrieval validation accuracy (**V**):  

$$
RT = f(D, A, V)
$$

A secure RAG system maintains **RT ≥ τ**, where τ is the minimum confidence threshold required for generation to proceed.  

**HU:**  
A RAG-bizalom (**RT**) az adatintegritás (**D**), a hozzáférés-ellenőrzés (**A**) és a visszakeresési érvényesítés (**V**) függvénye:  

$$
RT = f(D, A, V)
$$

A biztonságos RAG-rendszer fenntartja, hogy **RT ≥ τ**, ahol τ az a minimális bizalmi küszöb, amely felett a generálás engedélyezhető.

---

## 🔍 Key Threats / Fő fenyegetések

**EN:**  
- **Data poisoning:** malicious content embedded in vector stores.  
- **Prompt leakage:** sensitive retrieval instructions exposed through outputs.  
- **Cross-tenant inference:** data contamination between user spaces.  
- **Retrieval drift:** outdated or irrelevant data retrieved due to embedding decay.  

**HU:**  
- **Adatmérgezés:** rosszindulatú tartalom beillesztése a vektortárolóba.  
- **Prompt-szivárgás:** érzékeny lekérdezési utasítások kiszivárgása a kimenetekben.  
- **Bérlők közötti inferencia:** adat-szennyeződés a felhasználói környezetek között.  
- **Visszakeresési eltolódás:** elavult vagy irreleváns adatok visszahívása az embedding-változása miatt.

---

## 🔐 Data Governance Controls / Adatirányítási kontrollok

**EN:**  
Governance in RAG enforces:  
1. **Access segmentation:** least-privilege permissions per index.  
2. **Data provenance tracking:** recording every document’s origin and license.  
3. **Embedding verification:** ensuring no hidden or adversarial payloads.  
4. **Policy-based filtering:** excluding unverified or non-compliant data sources.  

**HU:**  
A RAG-irányítás biztosítja:  
1. **Hozzáférés-szegmentálás:** legkisebb jogosultság elve indexenként.  
2. **Adatszármazás-követés:** minden dokumentum eredetének és licencének naplózása.  
3. **Embedding-ellenőrzés:** rejtett vagy adverzáriális tartalmak kizárása.  
4. **Szabályzati szűrés:** nem hitelesített vagy nem megfelelős adatforrások kizárása.

---

## 🧠 Integration with Governance and CI/CD / Integráció az irányítással és CI/CD-vel

**EN:**  
[[security_as_code_and_ci_cd_integration]] pipelines automate RAG validation. Each retrieval endpoint is tested for access compliance and poisoning resistance. [[ai_governance_and_policy]] ensures data retrieval aligns with organizational classification levels.  

**HU:**  
A [[security_as_code_and_ci_cd_integration]] pipeline-ok automatizálják a RAG-validációt. Minden visszakeresési végpont hozzáférési megfelelőségre és mérgezés-ellenállásra van tesztelve. Az [[ai_governance_and_policy]] gondoskodik arról, hogy a visszakeresés a szervezeti adatosztályozási szintekkel összhangban történjen.

---

## ⚖️ Ethical and Privacy Considerations / Etikai és adatvédelmi megfontolások

**EN:**  
RAG systems often mix public and private data sources. [[ethical_ai_policy]] requires transparent disclosure when retrieved information affects the generated output, and mandates privacy preservation through anonymization and consent logging.  

**HU:**  
A RAG-rendszerek gyakran vegyítik a nyilvános és privát adatforrásokat. Az [[ethical_ai_policy]] előírja az átlátható közlést, amikor a visszakeresett információ befolyásolja a generált kimenetet, és megköveteli az anonimizálást és a beleegyezés-naplózást az adatvédelem biztosításához.

---

## 🧾 Monitoring and Continuous Validation / Monitorozás és folyamatos validáció

**EN:**  
[[continuous_validation_and_review]] connects telemetry from RAG pipelines with governance dashboards — tracking retrieval anomalies, poisoning indicators, and data freshness scores. Deviations below policy thresholds automatically trigger audits or re-indexing.  

**HU:**  
A [[continuous_validation_and_review]] a RAG-pipeline-ok telemetriáját összekapcsolja az irányítási irányítópultokkal — követve a visszakeresési anomáliákat, mérgezés-indikátorokat és az adatfrissességi pontszámokat. A szabályzati küszöb alá eső eltérések automatikusan auditot vagy újraindexelést indítanak.

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Future RAG security will adopt **policy-aware retrievers** and **confidential embeddings** — where every query is cryptographically signed, policy-checked, and privacy-preserving. Integration with [[ai_risk_assessment_methodology]] will allow probabilistic scoring of retrieval reliability and content trustworthiness in real time.  

**HU:**  
A jövő RAG-biztonsága **szabályzattudatos visszakeresőket** és **bizalmas embeddingeket** fog alkalmazni — ahol minden lekérdezés kriptográfiailag aláírt, szabályzati szinten ellenőrzött és adatvédelmet biztosító lesz. Az [[ai_risk_assessment_methodology]] integrációja lehetővé teszi a visszakeresési megbízhatóság és a tartalom-hitelesség valós idejű valószínűségi pontozását.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What makes RAG architectures more vulnerable than standalone models?  
2. How does the function RT = f(D, A, V) define RAG trust?  
3. What are the key attack vectors in RAG pipelines?  
4. How does data governance enforce provenance and access control?  
5. Why must CI/CD processes include RAG validation steps?  
6. What ethical risks arise from public–private data mixing?  
7. How can continuous validation detect retrieval poisoning or drift?  
8. What is the future role of policy-aware retrievers in AI security?

> “Knowledge retrieval without governance  
> is like memory without conscience — powerful, but dangerous.”

