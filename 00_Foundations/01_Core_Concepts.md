---
id: 01_core_concepts
title: "01 – Core Concepts / Alap fogalmak"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "00_Foundations"
role: "core_concepts"
tags:
  - ai_security
  - foundations
  - underscore_slugs
---
🚨 COPY START 🚨
# Core Concepts  
*The pillars that define how AI systems can be trusted, attacked, or defended*  

---

## 🌍 Overview  

**EN:**  
Core Concepts represent the **theoretical backbone** of AI Security — the essential principles that describe how machine learning systems function, where they fail, and how they can be protected.  
They form the *bridge between AI science and cybersecurity engineering*. 🧠🛡️  

Understanding these concepts is crucial because AI systems do not operate like traditional IT assets.  
They evolve, adapt, and sometimes behave unpredictably. Security, therefore, must account for **data dynamics**, **model behavior**, and **ethical context** — not just code or firewalls.  

**HU:**  
A **Core Concepts** az MI-biztonság **elméleti gerincét** alkotják – azok az alapelvek, amelyek leírják, hogyan működnek, hol hibázhatnak és hogyan védhetők meg a gépi tanulási rendszerek. 🧩  
Ezek képezik a **híd** szerepét az MI-tudomány és a kiberbiztonsági mérnöki gyakorlat között.  

Az MI-rendszerek nem működnek úgy, mint a hagyományos informatikai eszközök – **változnak, tanulnak, néha kiszámíthatatlanul viselkednek**.  
Ezért az MI-biztonság nemcsak kódról vagy tűzfalakról szól, hanem az **adatdinamikáról, a modellviselkedésről és az etikai kontextusról** is.  

---

## 🧩 1. Data Integrity and Provenance  

**EN:**  
Every AI system is only as trustworthy as its data.  
**Data Integrity** ensures that inputs are unaltered, consistent, and authentic.  
**Data Provenance** tracks *where* data comes from and *how* it has been transformed — the foundation of accountability.  

Drift, poisoning, or unauthorized manipulation of data can silently erode security guarantees.  
That’s why data must be continuously verified through hashing, digital signatures, and lineage tracking.  

**HU:**  
Minden MI-rendszer annyira megbízható, amennyire az adatai azok.  
A **Data Integrity** biztosítja, hogy a bemenetek változatlanok, konzisztenssek és hitelesek legyenek.  
A **Data Provenance** pedig nyomon követi, *honnan* származnak az adatok és *hogyan* alakultak át – ez az elszámoltathatóság alapja.  

Az adatok elcsúszása, megmérgezése vagy jogosulatlan módosítása **csendesen alááshatja** a biztonságot.  
Ezért elengedhetetlen a folyamatos ellenőrzés hash-ekkel, digitális aláírásokkal és adatvonal-követéssel.  

---

## 💡 2. Model Reliability and Drift  

**EN:**  
Models are **dynamic entities**, not static code. Their reliability depends on how well they generalize beyond training data.  
When real-world conditions evolve, **[[model_drift|Model Drift]]** emerges — causing the model’s predictions to deviate from truth.  

The security implication: drift can mask adversarial manipulation or cause unnoticed failures in automated pipelines.  
Continuous retraining, validation, and drift detection are therefore part of every secure AI lifecycle.  

**HU:**  
A modellek **dinamikus rendszerek**, nem statikus programok. Megbízhatóságuk azon múlik, mennyire képesek általánosítani a tanítóadatokon túl.  
Ha a valóság megváltozik, megjelenik a **[[model_drift|Model Drift]]**, amely eltéríti az előrejelzéseket a valóságtól.  

Biztonsági szempontból ez veszélyes: a drift **elfedheti az adverszáriális manipulációt** vagy rejtett hibákat okozhat az automatizált rendszerekben.  
Ezért az újratanítás, validáció és drift-megfigyelés minden biztonságos MI-életciklus része.  

---

## 🛡️ 3. Trust Boundaries and Zero Trust  

**EN:**  
AI systems operate across multiple trust layers: users, data pipelines, APIs, and models.  
Each layer can be **compromised independently**, meaning that no single component should be implicitly trusted.  
This principle is formalized in **[[zero_trust_for_ai|Zero Trust for AI]]**, which enforces verification and authentication at every step.  

In practice, Zero Trust means:  
- never assuming an input is safe,  
- never assuming a model is unaltered, and  
- never assuming outputs are harmless.  

**HU:**  
Az MI-rendszerek több **bizalmi réteg** között működnek: felhasználók, adatfolyamok, API-k és modellek.  
Bármelyik réteg **önállóan is kompromittálódhat**, ezért semmit sem szabad implicit módon megbízottnak tekinteni.  
Ezt az elvet a **[[zero_trust_for_ai|Zero Trust for AI]]** foglalja rendszerbe, amely minden ponton hitelesítést és ellenőrzést követel.  

A gyakorlatban a Zero Trust azt jelenti:  
- soha ne feltételezd, hogy a bemenet biztonságos,  
- soha ne feltételezd, hogy a modell sértetlen,  
- és soha ne feltételezd, hogy a kimenet ártalmatlan.  

---

## ⚙️ 4. Explainability and Interpretability  

**EN:**  
A secure AI is not only one that resists attacks — it is one that can be **understood and verified**.  
**[[explainability|Explainability]]** and **[[interpretability|Interpretability]]** transform opaque black-box behavior into something traceable and auditable.  

For example, the contribution of each feature can be expressed using *Integrated Gradients*:  

$$
\mathrm{IG}_i(x) = (x_i - x'_i) \times \int_{0}^{1} \frac{\partial F(x' + \alpha(x - x'))}{\partial x_i} \, d\alpha
$$  

Such transparency is essential for debugging, fairness analysis, and compliance with governance frameworks like **[[ai_governance|AI Governance]]**.  

**HU:**  
A biztonságos MI nem csak az, amely ellenáll a támadásoknak – hanem az is, amely **érthető és ellenőrizhető**.  
Az **[[explainability|Explainability]]** és az **[[interpretability|Interpretability]]** lehetővé teszik, hogy az átláthatatlan „fekete doboz” működés **vizsgálható és auditálható** legyen.  

Például a jellemzők hozzájárulása az alábbi *Integrated Gradients* képlettel írható le:  

$$
\mathrm{IG}_i(x) = (x_i - x'_i) \times \int_{0}^{1} \frac{\partial F(x' + \alpha(x - x'))}{\partial x_i} \, d\alpha
$$  

Ez a transzparencia elengedhetetlen a hibakereséshez, a fairness elemzéshez és az olyan irányítási keretek betartásához, mint az **[[ai_governance|AI Governance]]**.  

---

## 🔐 5. Privacy and Inference Control  

**EN:**  
AI systems often process personal or proprietary information.  
If not carefully designed, they can leak data through outputs — as in **[[membership_inference_attacks|Membership Inference]]** or **[[model_stealing|Model Stealing]]**.  

Privacy-enhancing methods such as **[[differential_privacy|Differential Privacy]]** inject statistical noise during training to obscure individual records:  

$$
P(f(D) \in S) \leq e^\epsilon \cdot P(f(D') \in S)
$$  

Here, \( \epsilon \) represents the *privacy budget*: smaller values mean stronger privacy but lower utility.  

**HU:**  
Az MI-rendszerek gyakran kezelnek személyes vagy tulajdonosi információkat.  
Ha nem megfelelően vannak megtervezve, **adatokat szivárogtathatnak** a kimeneteken keresztül – például **[[membership_inference_attacks|Membership Inference]]** vagy **[[model_stealing|Model Stealing]]** formájában.  

Az olyan adatvédelmi technikák, mint a **[[differential_privacy|Differential Privacy]]**, statisztikai zajt adnak a tanításhoz, hogy elrejtsék az egyedi rekordokat:  

$$
P(f(D) \in S) \leq e^\epsilon \cdot P(f(D') \in S)
$$  

Itt \( \epsilon \) az *adatvédelmi költségvetés*: minél kisebb, annál erősebb a védelem – de annál gyengébb az eredmény hasznossága.  

---

## 🧠 6. Governance, Ethics, and Accountability  

**EN:**  
Even the most secure AI can cause harm if deployed without ethical or legal oversight.  
**[[ai_governance|AI Governance]]** defines processes for transparency, fairness, and human control.  
It connects technical defenses with regulatory compliance and social responsibility.  

AI Security and AI Ethics must coexist — without governance, trust collapses; without security, governance is meaningless.  

**HU:**  
A legbiztonságosabb MI is okozhat kárt, ha **etikai vagy jogi felügyelet nélkül** működik.  
Az **[[ai_governance|AI Governance]]** szabályozza az átláthatóságot, a fairness-t és az emberi kontrollt, összekötve a technikai védelmet a jogi és társadalmi felelősséggel.  

Az MI-biztonság és az MI-etika **egymás nélkül értelmetlen**:  
irányítás nélkül a bizalom összeomlik, biztonság nélkül pedig az irányítás üres forma.  

---

## 📊 7. Continuous Assurance and Observability  

**EN:**  
Security is not a one-time state — it’s a continuous measurement.  
Through **[[observability_and_monitoring|Observability and Monitoring]]**, systems collect real-time metrics that indicate anomalies, drift, or attacks.  

The confidence in model safety can be dynamically updated based on detected anomalies \( A_t \):  

$$
T_{t+1} = T_t \cdot e^{-\lambda A_t}
$$  

Such adaptive assurance loops turn AI security into a *living system*, not a static control.  

**HU:**  
A biztonság nem egyszeri állapot – **folyamatos mérés**.  
Az **[[observability_and_monitoring|Observability and Monitoring]]** segítségével a rendszerek valós időben gyűjtenek adatokat az anomáliákról, drift-ről vagy támadásokról.  

A modell biztonságába vetett bizalom időben frissíthető a kimutatott anomáliák függvényében \( A_t \):  

$$
T_{t+1} = T_t \cdot e^{-\lambda A_t}
$$  

Ezáltal az MI-biztonság **élő rendszerré** válik, nem statikus kontrollfolyamattá.  

---

## 🧩 Related Vault Topics  

- [[data_provenance|Data Provenance]]  
- [[model_drift|Model Drift]]  
- [[zero_trust_for_ai|Zero Trust for AI]]  
- [[membership_inference_attacks|Membership Inference]]  
- [[ai_governance|AI Governance]]  
- [[observability_and_monitoring|Observability and Monitoring]]  

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. **EN:** Why must AI security address both technical and ethical layers simultaneously?  
   **HU:** Miért kell az MI-biztonságnak egyszerre a technikai és etikai rétegekre is kiterjednie?  

2. **EN:** How does model drift impact security and reliability?  
   **HU:** Hogyan befolyásolja a modelldrift a biztonságot és a megbízhatóságot?  

3. **EN:** What is the difference between Zero Trust and simple access control?  
   **HU:** Mi a különbség a Zero Trust és az egyszerű hozzáférés-vezérlés között?  

4. **EN:** How does differential privacy mathematically ensure that training data cannot be reidentified?  
   **HU:** Hogyan biztosítja matematikailag a differenciális adatvédelem, hogy a tanítóadatok ne legyenek visszafejthetők?  

5. **EN:** Why is continuous observability considered the “heartbeat” of AI Security?  
   **HU:** Miért nevezik a folyamatos megfigyelést az MI-biztonság „érrendszerének”?  

---

> “Security is not about defense alone — it’s about understanding what we are defending.” 💡  

🚨 COPY END 🚨
