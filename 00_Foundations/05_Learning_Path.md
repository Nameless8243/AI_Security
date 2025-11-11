---
id: 05_learning_path
title: "05 – Learning Path / Tanulási útvonal"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "00_Foundations"
role: "learning_mentor"
tags:
  - ai_security
  - foundations
  - underscore_slugs
---
🚨 COPY START 🚨
# AI Security Learning Path  
*From curiosity to mastery — building your foundation, one layer at a time*  

---

## 🌍 Overview  

**EN:**  
The **AI Security Learning Path** provides a structured roadmap for developing deep, practical expertise in protecting machine learning systems.  
It aligns theoretical foundations, hands-on projects, and governance understanding into a unified progression.  

Think of this as a *spiral staircase* 🌀 — each loop revisits familiar topics (like [[data_poisoning|Data Poisoning]] or [[zero_trust_for_ai|Zero Trust for AI]]), but at higher levels of sophistication.  

**HU:**  
Az **AI Security Learning Path** egy strukturált útmutató az MI-biztonság elsajátításához, amely **elméleti tudást, gyakorlati tapasztalatot és irányítási szemléletet** épít egymásra.  
Olyan, mint egy *spirál lépcső* 🌀 — minden szinten visszatérünk a korábbi témákhoz (pl. [[data_poisoning|Data Poisoning]] vagy [[zero_trust_for_ai|Zero Trust for AI]]), de egyre mélyebb szinten értjük meg őket.  

---

## 🧱 Stage 1 – Foundations (Understanding the Building Blocks)  

**EN:**  
At this stage, the goal is to understand **how AI works** and **why it needs security**.  
Focus areas include:  

- [[core_concepts|Core Concepts]] – how trust, data, and governance intersect  
- [[lifecycle|AI System Lifecycle]] – where security fits in each phase  
- [[explainability|Explainability]] and [[interpretability|Interpretability]]  
- Basic adversarial concepts (noise, perturbations, misclassification)  
- Reading: NIST AI RMF (Map + Govern)  

By the end, you should recognize vulnerabilities in **data**, **models**, and **pipelines** — the triad of AI risk.  

**HU:**  
Ebben a szakaszban a cél az, hogy megértsd, **hogyan működik az MI**, és **miért van szükség biztonságra**.  
Fókuszterületek:  

- [[core_concepts|Core Concepts]] – bizalom, adat és irányítás összefüggései  
- [[lifecycle|AI System Lifecycle]] – a biztonság helye az életciklusban  
- [[explainability|Explainability]] és [[interpretability|Interpretability]]  
- Alapvető adverszáriális fogalmak (zaj, perturbáció, félreosztályozás)  
- Olvasmány: NIST AI RMF (Map + Govern részek)  

A végére képes leszel felismerni az **adat-, modell- és folyamat-szintű** sebezhetőségeket.  

---

## ⚙️ Stage 2 – Attacks and Threats  

**EN:**  
This phase builds intuition around how AI systems **can be attacked or manipulated**.  
You begin to see models as *targets* within a larger threat landscape.  

Core areas:  
- [[data_poisoning|Data Poisoning]] and [[backdoor_and_trojan_attacks|Backdoor Attacks]]  
- [[membership_inference_attacks|Membership Inference]] and [[model_stealing|Model Stealing]]  
- [[adversarial_example_attacks|Adversarial Example Attacks]]  
- [[prompt_injection|Prompt Injection]] and indirect instruction hijacking  
- AI threat modeling: STRIDE, ATT&CK, MITRE ATLAS  

**HU:**  
Ebben a fázisban megismered, hogyan **támadhatók meg vagy manipulálhatók** az MI-rendszerek.  
Megtanulod a modelleket *célpontként* látni a teljes fenyegetési környezetben.  

Fő témák:  
- [[data_poisoning|Data Poisoning]] és [[backdoor_and_trojan_attacks|Backdoor Attacks]]  
- [[membership_inference_attacks|Membership Inference]] és [[model_stealing|Model Stealing]]  
- [[adversarial_example_attacks|Adversarial Example Attacks]]  
- [[prompt_injection|Prompt Injection]] és indirekt utasítás-eltérítés  
- AI fenyegetésmodellezés: STRIDE, ATT&CK, MITRE ATLAS  

---

## 🛡️ Stage 3 – Defenses and Mitigations  

**EN:**  
Now, you shift from breaking to **protecting**.  
This stage teaches how to build resilience across the ML pipeline using layered defense principles.  

Learn to implement:  
- [[input_restoration|Input Restoration]]  
- [[adversarial_training|Adversarial Training]]  
- [[runtime_isolation_and_sandboxing|Runtime Isolation]]  
- [[zero_trust_for_ai|Zero Trust for AI]]  
- [[observability_and_monitoring|Observability and Monitoring]]  

Mathematically, defense can be viewed as minimizing **expected loss under attack distribution** \( Q(x) \):  

$$
\min_\theta \; \mathbb{E}_{x \sim Q}[L(f_\theta(x), y)]
$$  

**HU:**  
Mostantól a cél már nem a feltörés, hanem a **védelem megvalósítása**.  
Megtanulod, hogyan lehet rétegezett védelmet kialakítani a teljes MI-folyamat mentén.  

Kiemelt technikák:  
- [[input_restoration|Input Restoration]]  
- [[adversarial_training|Adversarial Training]]  
- [[runtime_isolation_and_sandboxing|Runtime Isolation]]  
- [[zero_trust_for_ai|Zero Trust for AI]]  
- [[observability_and_monitoring|Observability and Monitoring]]  

Matematikailag a védelem célja, hogy **minimalizálja a várható veszteséget** a támadási eloszlás \( Q(x) \) alatt:  

$$
\min_\theta \; \mathbb{E}_{x \sim Q}[L(f_\theta(x), y)]
$$  

---

## 🧠 Stage 4 – Governance and Ethics  

**EN:**  
At this level, security expands beyond code and algorithms — it integrates into **organizational trust, risk, and compliance**.  

Key frameworks and focus areas:  
- [[ai_governance|AI Governance]] and NIST AI RMF  
- [[fairness|Fairness]] and bias mitigation  
- [[data_provenance|Data Provenance]] and auditability  
- [[ai_risk_management_and_assurance|AI Risk Management]]  
- Regulations: **EU AI Act**, **ISO/IEC 42001**, **OECD AI Principles**  

**HU:**  
Ezen a szinten a biztonság túllép a kódon és az algoritmusokon – **szervezeti bizalom, kockázat és megfelelés** részévé válik.  

Fő keretrendszerek és témák:  
- [[ai_governance|AI Governance]] és NIST AI RMF  
- [[fairness|Fairness]] és bias-csökkentés  
- [[data_provenance|Data Provenance]] és auditálhatóság  
- [[ai_risk_management_and_assurance|AI Risk Management]]  
- Szabályozások: **EU AI Act**, **ISO/IEC 42001**, **OECD AI Principles**  

---

## 🔬 Stage 5 – Advanced and Emerging Topics  

**EN:**  
Finally, you move toward *cutting-edge AI security research*.  
This level integrates cryptography, automation, and novel AI architectures.  

Advanced topics:  
- [[zero_knowledge_proofs_for_ai|Zero-Knowledge Proofs for AI]]  
- [[pqc_and_quantum_resistant_ai|Post-Quantum Cryptography in AI]]  
- [[ai_security_metrics_and_kpis|AI Security Metrics and KPIs]]  
- [[ai_supply_chain_security|AI Supply Chain Security]]  
- [[ai_security_automation|AI Security Automation and CI/CD Integration]]  

**HU:**  
A végső szakaszban a *kutatási szintű* MI-biztonsági témák következnek.  
Itt az elmélet, a kriptográfia és az automatizálás találkozik.  

Haladó területek:  
- [[zero_knowledge_proofs_for_ai|Zero-Knowledge Proofs for AI]]  
- [[pqc_and_quantum_resistant_ai|Post-Quantum Cryptography in AI]]  
- [[ai_security_metrics_and_kpis|AI Security Metrics and KPIs]]  
- [[ai_supply_chain_security|AI Supply Chain Security]]  
- [[ai_security_automation|AI Security Automation and CI/CD Integration]]  

---

## ⚖️ Progression Philosophy  

**EN:**  
The goal is **not to rush**, but to build *conceptual density* — mastering each topic until it feels intuitive.  
In AI Security, depth always outweighs speed.  
You are not memorizing; you are constructing a mental model that connects data, trust, and defense.  

**HU:**  
A cél nem a gyorsaság, hanem a **mélység**.  
Addig kell tanulni egy témát, amíg az **intuitívvá válik**.  
Az MI-biztonságban a megértés értékesebb, mint a sebesség: itt **gondolati modellt** építesz, amely összekapcsolja az adatot, a bizalmat és a védelmet.  

---

## 🧩 Related Vault Topics  

- [[core_concepts|Core Concepts]]  
- [[lifecycle|AI System Lifecycle]]  
- [[ai_governance|AI Governance]]  
- [[ai_security_metrics_and_kpis|AI Security Metrics and KPIs]]  
- [[ai_security_automation|AI Security Automation and Metrics]]  

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. **EN:** Why should AI Security learning follow a lifecycle structure similar to AI systems themselves?  
   **HU:** Miért kell az MI-biztonsági tanulásnak az MI-életciklushoz hasonló szerkezetet követnie?  

2. **EN:** How do attack and defense stages reinforce each other conceptually?  
   **HU:** Hogyan erősítik egymást elméletben a támadási és védelmi szakaszok?  

3. **EN:** Which stage introduces governance and compliance principles, and why are they essential?  
   **HU:** Melyik szakaszban jelenik meg a governance és a megfelelés, és miért kulcsfontosságú?  

4. **EN:** How does Zero Trust evolve from a security framework to a personal learning principle?  
   **HU:** Hogyan válik a Zero Trust egy biztonsági keretrendszerből személyes tanulási elvvé?  

5. **EN:** What role do automation and metrics play at the final stage of AI Security learning?  
   **HU:** Milyen szerepet játszanak az automatizálás és a mérőszámok az MI-biztonsági tanulás utolsó szakaszában?  

---

> “Learning AI Security is not about defending machines — it’s about teaching yourself to think like one.” 🤖  

🚨 COPY END 🚨
