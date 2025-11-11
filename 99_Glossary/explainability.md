---
id: explainability
title: "Explainability / Magyarázhatóság"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "01_Glossary"
agent: "Core Concepts Engineer"
tags:
  - ai_security
  - glossary
  - underscore_slug
---
🚨 COPY START 🚨
# Explainability  
*Understanding the "why" behind AI decisions*

---

## 🌍 Concept Overview

**EN:**  
Explainability refers to the ability to **understand, interpret, and communicate** how an AI system arrives at a particular output or decision. In essence, it answers the question: _“Why did the model make this choice?”_ 🧠  
In security terms, explainability is vital for **trust, validation, and accountability**. Without it, you cannot verify whether a system behaves safely, fairly, or according to policy — nor detect manipulation or hidden bias.  
Explainability bridges the technical and ethical layers of AI: it connects raw computation to human reasoning.  

**HU:**  
Az **magyarázhatóság** (explainability) azt jelenti, hogy **érthetővé és követhetővé** tesszük, miként hoz döntést egy mesterséges intelligencia-rendszer. 🧩  
Másképp fogalmazva: _„Miért döntött így a modell?”_  
Biztonsági szempontból ez kulcsfontosságú a **bizalom, az ellenőrizhetőség és az elszámoltathatóság** szempontjából.  
Magyarázhatóság nélkül sem a torzítások, sem a támadások, sem a hibás viselkedések nem ismerhetők fel időben.

---

## 💡 Explainability vs Interpretability

**EN:**  
Although they are often used interchangeably, **[[explainability|Explainability]]** and **[[interpretability|Interpretability]]** describe two different goals.  
- *Interpretability* focuses on how directly we can understand the internal mechanisms of a model.  
- *Explainability* focuses on how well we can **communicate** those mechanisms to humans.  

For example, a linear model is interpretable because we can inspect its weights.  
A deep neural network, however, requires post-hoc **explainability methods** such as **LIME**, **SHAP**, or **Integrated Gradients** to approximate human understanding.

**HU:**  
A **magyarazhatóság** és az **értelmezhetőség** nem ugyanaz, bár gyakran összekeverik őket.  
- Az *értelmezhetőség* (interpretability) azt jelenti, mennyire látható közvetlenül, mi történik a modell belsejében.  
- A *magyarázhatóság* (explainability) pedig azt, mennyire tudjuk **emberi nyelven elmagyarázni** a modell működését.  

Egy lineáris modell például önmagában értelmezhető, míg egy mély neurális hálóhoz már utólagos technikákra van szükség (pl. **LIME**, **SHAP**, **Integrated Gradients**).

---

## 🛡️ Security and Risk Perspective

**EN:**  
From the viewpoint of **AI Security**, explainability serves as a **defensive control**. It enables anomaly detection, auditability, and model assurance.  
However, it also opens potential **attack surfaces**. For instance, too much transparency may leak proprietary parameters or enable **[[model_stealing|Model Stealing]]** and **[[membership_inference_attacks|Membership Inference Attacks]]**.  
Balancing openness and protection is therefore a central tension in modern AI governance.

**HU:**  
A **magyarázhatóság** a mesterséges intelligencia-biztonságban **védelmi eszközként** is működik:  
segít a rendellenességek észlelésében, az auditálhatóságban és a megbízhatóság biztosításában.  
Ugyanakkor új **támadási felületeket** is megnyithat — például túl nagy átláthatóság esetén a támadók visszafejthetik a modell logikáját vagy adatmintákat azonosíthatnak (**[[model_stealing|Model Stealing]]**, **[[membership_inference_attacks|Membership Inference Attacks]]**).  
A cél tehát az **egyensúly** az átláthatóság és a védelem között. ⚖️

---

## ⚙️ Techniques and Mathematical Foundations

**EN:**  
Explainability can be formalized through the lens of **feature attribution** and **gradient analysis**.  
For instance, **Integrated Gradients** attribute the importance of each input feature by integrating gradients along a path from a baseline input \( x' \) to the actual input \( x \):

$$
\mathrm{IG}_i(x) = (x_i - x'_i) \times \int_{\alpha=0}^{1} \frac{\partial F(x' + \alpha(x - x'))}{\partial x_i} \, d\alpha
$$

This method ensures that each feature’s contribution is both mathematically consistent and visually interpretable.

**HU:**  
A magyarázhatóság matematikai alapja gyakran a **jellemző-attribúció** és a **gradiens-elemzés**.  
Az **Integrated Gradients** például minden bemeneti jellemző fontosságát a kiindulási ponttól \( x' \) a tényleges bemenetig \( x \) tartó út mentén integrált gradiens alapján számítja:

$$
\mathrm{IG}_i(x) = (x_i - x'_i) \times \int_{\alpha=0}^{1} \frac{\partial F(x' + \alpha(x - x'))}{\partial x_i} \, d\alpha
$$

Így minden jellemző hozzájárulása **matematikailag következetes és vizuálisan értelmezhető** lesz.

---

## 🤖 Governance and Compliance Implications

**EN:**  
In frameworks such as **[[ai_governance|AI Governance]]** and **[[nist_ai_rmf|NIST AI RMF]]**, explainability is classified as a **trustworthiness dimension**.  
It enables human oversight, policy validation, and incident review.  
Explainable AI (XAI) is now a requirement in several jurisdictions (e.g., EU AI Act), linking transparency directly to legal compliance and human rights.

**HU:**  
A **[[ai_governance|AI Governance]]** és a **[[nist_ai_rmf|NIST AI RMF]]** keretrendszerekben a magyarázhatóság a **megbízhatóság egyik pillére**.  
Lehetővé teszi az emberi felügyeletet, a szabályzatok érvényesítését és az incidensek utólagos elemzését.  
Az ún. **magyarázható MI (XAI)** már jogi követelmény több régióban (pl. EU AI Act), így a **transzparencia** a **jogi megfelelés** és az **emberi jogok** részévé vált.

---

## 🧩 Related Vault Topics

- [[interpretability|Interpretability]]  
- [[fairness|Fairness]]  
- [[ai_governance|AI Governance]]  
- [[model_drift|Model Drift]]  
- [[model_stealing|Model Stealing]]  
- [[membership_inference_attacks|Membership Inference Attacks]]  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. **EN:** How does explainability differ from interpretability, and why is that distinction important in AI security?  
   **HU:** Miben különbözik a magyarázhatóság az értelmezhetőségtől, és miért fontos ez a különbség az MI-biztonságban?

2. **EN:** What types of attacks can exploit excessive transparency in explainable AI systems?  
   **HU:** Milyen támadások használhatják ki a túlzott átláthatóságot a magyarázható MI rendszerekben?

3. **EN:** Describe how Integrated Gradients quantifies feature importance mathematically.  
   **HU:** Magyarázd el, hogyan számítja az Integrated Gradients módszer a jellemzők fontosságát matematikailag.

4. **EN:** Why is explainability considered essential for regulatory compliance under the EU AI Act?  
   **HU:** Miért kulcsfontosságú a magyarázhatóság a jogi megfelelés (pl. EU AI Act) szempontjából?

5. **EN:** How does explainability contribute to detecting bias, drift, or manipulation in AI models?  
   **HU:** Hogyan segíti a magyarázhatóság a torzítások, elcsúszások vagy manipulációk felismerését?

---

> “Transparency is not only about seeing through systems — it’s about making them worthy of being seen.” 💬

🚨 COPY END 🚨
