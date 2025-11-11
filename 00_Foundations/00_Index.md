---
id: 00_index
title: "00 – Foundations Index"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "00_Foundations"
role: "index_architect"
tags:
  - ai_security
  - foundations
  - underscore_slugs
---
🚨 COPY START 🚨
# 00_Foundations – Index  
*Building the mental architecture of AI Security*  

---

## 🌍 Purpose of the Foundations Section  

**EN:**  
This section establishes the **core knowledge base** for understanding and securing Artificial Intelligence systems.  
Before analyzing complex attacks or defense strategies, one must understand the *foundations* — how models learn, how data flows, what trust means, and how security, privacy, and governance intersect. 🧠  

**HU:**  
Ez a fejezet az **alapvető ismereteket** foglalja össze, amelyek nélkül nem érthető meg a mesterséges intelligencia biztonsága.  
Mielőtt a támadásokat vagy védelmi módszereket tanulnánk, előbb meg kell érteni az **alapokat** – hogyan tanulnak a modellek, hogyan áramlik az adat, mit jelent a bizalom, és hogyan kapcsolódik össze a biztonság, az adatvédelem és az irányítás. 🔒  

---

## 🧩 Core Concepts  

**EN:**  
Each of the following glossary entries provides a conceptual brick in the foundation of AI Security.  
Together, they explain *how trust, control, and adaptation* define the resilience of AI systems:  

- [[explainability|Explainability]] 🧠 – understanding why the model makes a decision.  
- [[interpretability|Interpretability]] 🔍 – understanding how the model makes it.  
- [[input_restoration|Input Restoration]] 🧼 – purifying incoming data before it harms the model.  
- [[membership_inference_attacks|Membership Inference]] 🕵️‍♂️ – when outputs reveal who was part of training.  
- [[model_drift|Model Drift]] ⏳ – when a model loses alignment with reality.  
- [[prompt_injection|Prompt Injection]] 🧩 – when adversaries hijack the model’s instructions.  
- [[zero_trust_for_ai|Zero Trust for AI]] 🛡️ – trust nothing, verify everything.  
- [[data_provenance|Data Provenance]] 🗂️ – ensuring the authenticity and traceability of data.  
- [[fairness|Fairness]] ⚖️ – preventing bias in model decisions.  
- [[ai_governance|AI Governance]] 🏛️ – ensuring responsible, transparent oversight.  

**HU:**  
A következő fogalmak az MI-biztonság építőkockái, amelyek együtt meghatározzák a **bizalom, kontroll és alkalmazkodás** rendszerét:  

- [[explainability|Explainability]] 🧠 – miért dönt így a modell.  
- [[interpretability|Interpretability]] 🔍 – hogyan dönt a modell.  
- [[input_restoration|Input Restoration]] 🧼 – a bemeneti adatok megtisztítása a káros hatások előtt.  
- [[membership_inference_attacks|Membership Inference]] 🕵️‍♂️ – amikor a kimenetből kikövetkeztethető, ki szerepelt a tanítóhalmazban.  
- [[model_drift|Model Drift]] ⏳ – amikor a modell elcsúszik a valóságtól.  
- [[prompt_injection|Prompt Injection]] 🧩 – amikor a támadók átveszik az irányítást a modell utasításai felett.  
- [[zero_trust_for_ai|Zero Trust for AI]] 🛡️ – ne bízz meg semmiben, mindig ellenőrizz.  
- [[data_provenance|Data Provenance]] 🗂️ – az adatok eredetének és hitelességének biztosítása.  
- [[fairness|Fairness]] ⚖️ – az elfogultság elkerülése a modellek döntéseiben.  
- [[ai_governance|AI Governance]] 🏛️ – az MI rendszerek felelős és átlátható felügyelete.  

---

## 💡 How the Foundations Interconnect  

**EN:**  
These concepts form an **interdependent network**:  
- Without **Explainability**, you can’t audit decisions.  
- Without **Zero Trust**, you can’t secure the data or the model.  
- Without **Input Restoration**, you can’t rely on any analysis.  
- Without **Governance**, you can’t ensure accountability or compliance.  

This foundation therefore serves as both the *educational entry point* and the *philosophical spine* of the entire Vault.  

**HU:**  
Ezek a fogalmak **összefüggő hálózatot** alkotnak:  
- **Explainability** nélkül nem lehet auditálni a döntéseket.  
- **Zero Trust** nélkül nem biztosítható sem az adat, sem a modell.  
- **Input Restoration** nélkül semmilyen elemzés nem megbízható.  
- **Governance** nélkül nincs elszámoltathatóság vagy megfelelés.  

Ez a fejezet tehát egyszerre **tanulási belépőpont** és az egész Vault **filozófiai gerince**.  

---

## ⚙️ Mathematical and Logical Foundations  

**EN:**  
Many foundational concepts of AI Security are grounded in mathematics and logic — they define what “trust” means in quantifiable terms.  

For example, drift or model decay can be represented as a distance metric \( D \) between training and production distributions:  

$$
D = \lVert P_{\text{train}}(X, Y) - P_{\text{prod}}(X, Y) \rVert
$$  

Similarly, Zero Trust confidence scores evolve according to observed anomalies \( A_t \):  

$$
T_{t+1} = T_t \cdot e^{-\lambda A_t}
$$  

**HU:**  
Az MI-biztonság alapfogalmai **matematikai és logikai elveken** nyugszanak – számszerűsítik a „bizalmat”.  

Például a drift (modell elcsúszás) mérhető a tanító és éles eloszlás közti távolsággal \( D \):  

$$
D = \lVert P_{\text{train}}(X, Y) - P_{\text{prod}}(X, Y) \rVert
$$  

Hasonlóan, a Zero Trust bizalmi érték időben változik az anomáliák függvényében \( A_t \):  

$$
T_{t+1} = T_t \cdot e^{-\lambda A_t}
$$  

---

## 🧠 Why “Foundations” Matter in AI Security  

**EN:**  
In AI security, failure rarely begins with a hack — it begins with **a wrong assumption**.  
Foundational understanding eliminates these weak assumptions by making every concept explicit, measurable, and traceable.  
It connects the human mindset (ethics, governance) with the machine logic (models, data, and trust).  

**HU:**  
Az MI-biztonságban a hibák ritkán valódi hackeléssel kezdődnek — általában egy **rossz feltételezéssel**.  
Az alapok megértése megszünteti ezeket a gyenge pontokat azáltal, hogy minden fogalmat **kifejezetté, mérhetővé és visszakövethetővé** tesz.  
Összekapcsolja az emberi gondolkodást (etika, irányítás) a gépi logikával (modellek, adatok, bizalom).  

---

## 🧩 Related Vault Topics  

- [[01_Attack_Taxonomy_and_Threats/00_index|Attack Taxonomy and Threats – Index]]  
- [[02_Defenses_and_Mitigations/00_index|Defenses and Mitigations – Index]]  
- [[05_AI_Risk_Management_and_Assurance/00_index|AI Risk Management and Assurance – Index]]  
- [[06_AI_Safety_and_Ethical_Assurance/00_index|AI Safety and Ethics – Index]]  

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. **EN:** Why must every AI security study begin with the foundational concepts?  
   **HU:** Miért kell az MI-biztonság tanulását az alapfogalmaknál kezdeni?  

2. **EN:** How do explainability and interpretability complement each other?  
   **HU:** Hogyan egészíti ki egymást az explainability és az interpretability?  

3. **EN:** Why is Zero Trust considered the “security philosophy” of AI systems?  
   **HU:** Miért tekintik a Zero Trust-ot az MI-rendszerek „biztonsági filozófiájának”?  

4. **EN:** How does model drift demonstrate the need for continuous monitoring?  
   **HU:** Hogyan szemlélteti a modelldrift a folyamatos megfigyelés szükségességét?  

5. **EN:** What connects fairness, governance, and trust in AI Security foundations?  
   **HU:** Mi köti össze a fairness, governance és trust fogalmakat az MI-biztonság alapjaiban?  

---

> “Strong systems are built on clear concepts. Weak ones are built on assumptions.” 🧱  

🚨 COPY END 🚨
