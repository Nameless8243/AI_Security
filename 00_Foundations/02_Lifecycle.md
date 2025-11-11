---
id: 02_lifecycle
title: "02 – AI Lifecycle / AI életciklus"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "00_Foundations"
role: "lifecycle_analyst"
tags:
  - ai_security
  - foundations
  - underscore_slugs
---
🚨 COPY START 🚨
# AI System Lifecycle  
*Securing every stage of the model’s life — not just its code*  

---

## 🌍 Concept Overview  

**EN:**  
The **AI System Lifecycle** describes the continuous journey of an AI model — from **data collection** to **deployment**, **monitoring**, and eventually **retirement**. ♻️  
In classical IT, software is static once deployed. In AI, models evolve, degrade, and must be **constantly retrained and reassessed**.  
Security, therefore, cannot be a single phase — it must be an **embedded process across the entire lifecycle**.  

**HU:**  
Az **MI-rendszer életciklusa** (AI System Lifecycle) az a folyamat, amelyben egy MI-modell **megszületik, fejlődik, működik, majd elavul**. 🔄  
A hagyományos szoftverekkel ellentétben az MI nem statikus: a modellek **tanulnak, változnak, romlanak**, ezért folyamatos karbantartást és felügyeletet igényelnek.  
A biztonság tehát nem egyetlen fázis feladata — hanem **átfogó folyamat**, amely minden életciklus-szakaszt végigkísér.  

---

## 🧩 The Six Phases of the AI Lifecycle  

**EN:**  
While different frameworks define the stages differently (e.g., **NIST AI RMF**, **ISO/IEC 42001**, **EU AI Act**), the following six-phase structure captures the essence of secure lifecycle management:  

1. **Data Collection & Ingestion**  
2. **Model Design & Development**  
3. **Training & Validation**  
4. **Deployment & Integration**  
5. **Monitoring & Adaptation**  
6. **Decommissioning & Archival**  

**HU:**  
A különböző keretrendszerek (pl. **NIST AI RMF**, **ISO/IEC 42001**, **EU AI Act**) eltérően nevezik a fázisokat, de a biztonság szempontjából hat fő szakasz különíthető el:  

1. **Adatgyűjtés és beolvasás**  
2. **Modelltervezés és fejlesztés**  
3. **Tanítás és validálás**  
4. **Telepítés és integráció**  
5. **Megfigyelés és alkalmazkodás**  
6. **Kivezetés és archiválás**  

---

## 💡 Phase 1 – Data Collection & Ingestion  

**EN:**  
This phase defines **what the model will learn from**.  
Security controls focus on ensuring **data provenance**, **authenticity**, and **integrity**.  
Techniques like [[data_provenance|Data Provenance]], digital signatures, and schema validation prevent **[[data_poisoning|Data Poisoning]]** or **[[backdoor_and_trojan_attacks|Backdoor Attacks]]**.  

**HU:**  
Ez a fázis határozza meg, **miből tanul** a modell.  
A biztonság itt az **adatok eredetére, hitelességére és integritására** összpontosít.  
Az olyan technikák, mint a [[data_provenance|Data Provenance]], a digitális aláírás és a sémaellenőrzés megakadályozzák a **[[data_poisoning|Data Poisoning]]** vagy **[[backdoor_and_trojan_attacks|Backdoor Attacks]]** típusú támadásokat.  

---

## 🧠 Phase 2 – Model Design & Development  

**EN:**  
During model creation, engineers must consider **attack surfaces** such as overfitting, explainability leakage, or insecure architectures.  
Adopting secure design patterns and **[[threat_modeling_for_ai|Threat Modeling for AI]]** ensures that risks are identified early.  

**HU:**  
A modellfejlesztés során a mérnököknek figyelembe kell venniük a **támadási felületeket**, mint például a túltanulás, a magyarázhatósági szivárgás vagy a gyenge architektúra.  
A biztonságos tervezési minták és a **[[threat_modeling_for_ai|Threat Modeling for AI]]** alkalmazása már korai szakaszban azonosítja a kockázatokat.  

---

## ⚙️ Phase 3 – Training & Validation  

**EN:**  
Here, the model transforms raw data into learned parameters.  
Security must ensure that training occurs in a **controlled, auditable environment** (e.g., isolated compute nodes, signed model artifacts).  
This phase applies [[differential_privacy|Differential Privacy]], [[adversarial_training|Adversarial Training]], and integrity checks to prevent data leakage and [[membership_inference_attacks|Membership Inference]].  

**HU:**  
Ebben a fázisban a modell a nyers adatokat **tanult paraméterekké** alakítja.  
A biztonság szempontjából kulcsfontosságú, hogy a tanítás **ellenőrzött, auditálható környezetben** történjen (pl. izolált számítási környezet, aláírt modellfájlok).  
Itt használhatók a [[differential_privacy|Differential Privacy]], az [[adversarial_training|Adversarial Training]] és az integritás-ellenőrzések, hogy elkerülhető legyen az adat- vagy tagsági szivárgás.  

---

## 🛡️ Phase 4 – Deployment & Integration  

**EN:**  
When a model moves to production, it becomes exposed to real-world inputs — and attackers.  
This is where **[[zero_trust_for_ai|Zero Trust for AI]]** becomes critical:  
all APIs, prompts, and data channels must be authenticated, logged, and sandboxed.  
Any inference endpoint should apply **[[input_restoration|Input Restoration]]** to prevent **[[prompt_injection|Prompt Injection]]** or **[[adversarial_example_attacks|Adversarial Example Attacks]]**.  

**HU:**  
A modell éles környezetbe kerülésekor **valós adatoknak és támadóknak** van kitéve.  
Itt válik létfontosságúvá a **[[zero_trust_for_ai|Zero Trust for AI]]** megközelítés:  
minden API-t, promptot és adatcsatornát hitelesíteni, naplózni és sandboxban futtatni kell.  
Az értékelési végpontokon **[[input_restoration|Input Restoration]]** védi a modellt a **[[prompt_injection|Prompt Injection]]** és **[[adversarial_example_attacks|Adversarial Example Attacks]]** ellen.  

---

## 📊 Phase 5 – Monitoring & Adaptation  

**EN:**  
Once deployed, models begin to **drift** — either naturally or maliciously.  
Continuous **[[observability_and_monitoring|Observability]]** ensures that performance, fairness, and trust metrics are tracked in real time.  
A mathematical representation of performance decay over time can be modeled as:  

$$
P(t) = P_0 \cdot e^{-\lambda t}
$$  

where \( P(t) \) is accuracy at time \( t \), \( P_0 \) is initial performance, and \( \lambda \) is the drift rate.  

**HU:**  
A telepítés után a modellek **elcsúszhatnak** – természetes módon vagy szándékosan.  
A folyamatos **[[observability_and_monitoring|Observability]]** biztosítja, hogy a teljesítmény-, fairness- és bizalmi mutatók valós időben követhetők legyenek.  
A teljesítmény időbeli romlása modellezhető például így:  

$$
P(t) = P_0 \cdot e^{-\lambda t}
$$  

ahol \( P(t) \) az aktuális pontosság, \( P_0 \) a kezdeti teljesítmény, \( \lambda \) pedig a drift sebessége.  

---

## 🪦 Phase 6 – Decommissioning & Archival  

**EN:**  
Every model must eventually be **retired**, especially when it becomes outdated, untrustworthy, or legally non-compliant.  
Secure decommissioning includes:  
- deleting sensitive training data,  
- revoking model credentials,  
- and cryptographically archiving audit logs for traceability.  

**HU:**  
Minden modellt előbb-utóbb **ki kell vezetni**, különösen ha elavult, megbízhatatlan vagy nem felel meg a jogszabályoknak.  
A biztonságos kivezetés tartalmazza:  
- az érzékeny tanítóadatok törlését,  
- a modellhez tartozó hitelesítési kulcsok visszavonását,  
- és az auditnaplók **kriptográfiai archiválását** az átláthatóság érdekében.  

---

## ⚖️ Governance and Lifecycle Assurance  

**EN:**  
Lifecycle security aligns with governance frameworks like **[[ai_governance|AI Governance]]** and **NIST AI RMF**.  
Each phase must produce **evidence artifacts** — signed datasets, validation reports, risk registers — that prove compliance and integrity.  
Security is not a checkpoint; it’s a continuous thread woven through every lifecycle stage.  

**HU:**  
Az életciklus-biztonság összhangban van az olyan keretrendszerekkel, mint az **[[ai_governance|AI Governance]]** és a **NIST AI RMF**.  
Minden fázisnak **bizonyítékokat** kell termelnie – aláírt adatokat, validálási jegyzőkönyveket, kockázati nyilvántartásokat – amelyek igazolják a megfelelést és az integritást.  
A biztonság nem ellenőrzőpont, hanem **folyamatos szál**, amely átszövi az egész életciklust.  

---

## 🧩 Related Vault Topics  

- [[data_provenance|Data Provenance]]  
- [[model_drift|Model Drift]]  
- [[zero_trust_for_ai|Zero Trust for AI]]  
- [[input_restoration|Input Restoration]]  
- [[observability_and_monitoring|Observability and Monitoring]]  
- [[ai_governance|AI Governance]]  

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. **EN:** Why must AI security be embedded across all lifecycle phases instead of treated as a separate step?  
   **HU:** Miért kell az MI-biztonságot az egész életciklusba beépíteni, nem pedig külön szakaszként kezelni?  

2. **EN:** What are the primary risks during the data collection and training phases?  
   **HU:** Mik a legfőbb kockázatok az adatgyűjtés és tanítás fázisában?  

3. **EN:** How does Zero Trust apply to model deployment and API exposure?  
   **HU:** Hogyan alkalmazható a Zero Trust elv a modell telepítésére és az API-k biztonságára?  

4. **EN:** How can continuous observability detect malicious drift in production?  
   **HU:** Hogyan segít a folyamatos megfigyelés felismerni a rosszindulatú driftet az éles környezetben?  

5. **EN:** What are the key security tasks during model decommissioning?  
   **HU:** Mik a legfontosabb biztonsági feladatok a modell kivezetésekor?  

---

> “A secure AI is not born secure — it becomes secure through every stage of its life.” 🔁  

🚨 COPY END 🚨
