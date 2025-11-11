---
version: "3.2"
section_type: "assurance"
agent: "Consistency Auditor"
---
---
title: Model Risk Management and Registers
phase: Governance
category: Risk Management & Assurance
difficulty: Advanced
related: [ai_risk_assessment_methodology, continuous_validation_and_review, audit_logging_and_traceability, ai_governance_and_policy, regulatory_and_legal_compliance]
updated: 2025-11-10
---

# ⚖️ Model Risk Management and Registers / Modellkockázat-kezelés és nyilvántartások

**EN:**  
Model Risk Management (MRM) is the structured discipline of identifying, assessing, mitigating, and monitoring **risks inherent to AI and ML models**.  
It provides the governance layer that ensures every model deployed in production is **transparent, explainable, and accountable**.  
The **Model Risk Register** is the living record of this discipline — a single source of truth documenting each model’s purpose, controls, and risk posture.  

**HU:**  
A modellkockázat-kezelés (MRM) egy strukturált megközelítés az **MI- és ML-modellekben rejlő kockázatok azonosítására, értékelésére, mérséklésére és nyomon követésére**.  
Ez az irányítási réteg biztosítja, hogy minden élesített modell **átlátható, magyarázható és elszámoltatható** legyen.  
A **Modellkockázati Nyilvántartás** e fegyelem élő dokumentuma — az egyetlen hiteles forrás, amely a modellek célját, kontrolljait és kockázati állapotát rögzíti. 🧩  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
Every model introduces risk — from algorithmic bias and data drift to compliance violations and operational failures.  
Model Risk Management formalizes how these risks are detected, tracked, and reported.  
Its goal is not to eliminate risk but to **make it visible, measurable, and controllable**.  

**HU:**  
Minden modell kockázatot hordoz — az algoritmikus torzítástól és adatsodródástól a megfelelőségi hibákig vagy működési meghibásodásokig.  
A modellkockázat-kezelés szabályozott keretet ad arra, hogyan kell ezeket a kockázatokat észlelni, követni és jelenteni.  
A cél nem a kockázat megszüntetése, hanem annak **láthatóvá, mérhetővé és kezelhetővé tétele**. ⚙️  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
Model Risk Management unites technical risk evaluation with organizational accountability.  
It integrates:  
- **Quantitative evaluation** (e.g., model stability, drift metrics),  
- **Qualitative judgment** (e.g., ethical, reputational, or legal impact),  
- and **Governance evidence** (documented testing, validation, and approvals).  
The result is a holistic, auditable view of model trustworthiness.  

**HU:**  
A modellkockázat-kezelés a technikai kockázatértékelést az **irányítási felelősséggel** egyesíti.  
Magában foglalja:  
- a **kvantitatív értékelést** (pl. modellstabilitás, sodródási metrikák),  
- a **kvalitatív megítélést** (pl. etikai, reputációs vagy jogi hatások),  
- valamint az **irányítási bizonyítékokat** (tesztelés, érvényesítés és jóváhagyás dokumentálása).  
Az eredmény egy átfogó, auditálható kép a modell megbízhatóságáról. 🧠  

---

## 🧩 Key Components / A modellkockázat-kezelés fő elemei

**EN:**  
1. **Model Inventory:** a complete list of models with ownership, purpose, and lifecycle phase.  
2. **Risk Assessment:** periodic evaluation of exposure, severity, and impact ([[ai_risk_assessment_methodology]]).  
3. **Validation and Testing:** ongoing verification of assumptions and performance ([[assurance_testing_and_validation]]).  
4. **Governance Controls:** policies defining approvals, retraining, and decommissioning ([[ai_governance_and_policy]]).  
5. **Risk Register:** a continuously updated record of all identified risks, mitigations, and responsible owners.  

**HU:**  
1. **Modell-leltár:** a modellek teljes listája tulajdonosokkal, céllal és életciklus-státusszal.  
2. **Kockázatértékelés:** az expozíció, súlyosság és hatás időszakos értékelése ([[ai_risk_assessment_methodology]]).  
3. **Érvényesítés és tesztelés:** a feltételezések és teljesítmény folyamatos ellenőrzése ([[assurance_testing_and_validation]]).  
4. **Irányítási kontrollok:** jóváhagyási, újratanítási és kivezetési szabályzatok ([[ai_governance_and_policy]]).  
5. **Kockázati nyilvántartás:** az összes azonosított kockázat, intézkedés és felelős személy folyamatosan frissített jegyzéke. 📘  

---

## ⚙️ The Model Risk Register / A modellkockázati nyilvántartás felépítése

**EN:**  
A Model Risk Register typically includes:
- Model name, ID, and owner.  
- Purpose and business function.  
- Key datasets and dependencies ([[data_provenance_and_integrity]]).  
- Validation results and assurance status ([[continuous_validation_and_review]]).  
- Risk categories (data, model, operational, ethical, compliance).  
- Mitigation controls and responsible owners.  
- Date of last review and next scheduled audit.  

**HU:**  
A Modellkockázati Nyilvántartás jellemzően tartalmazza:  
- A modell nevét, azonosítóját és tulajdonosát.  
- A célját és üzleti funkcióját.  
- Főbb adathalmazait és függőségeit ([[data_provenance_and_integrity]]).  
- Az érvényesítés eredményeit és a garanciális státuszt ([[continuous_validation_and_review]]).  
- A kockázati kategóriákat (adat-, modell-, működési, etikai, megfelelőségi).  
- A mérséklő kontrollokat és a felelős személyeket.  
- Az utolsó felülvizsgálat és a következő audit időpontját. 🧾  

---

## 🧮 Risk Quantification / Kockázatok kvantifikálása

**EN:**  
Model risks are typically rated using a multi-dimensional scoring matrix:
$$
RiskScore = Likelihood × Impact × Detectability
$$  
Each factor can include subdimensions:
- **Likelihood:** data drift, system exposure, or attack surface.  
- **Impact:** business loss, ethical harm, or compliance breach.  
- **Detectability:** monitoring coverage, audit latency, alert accuracy.  

**HU:**  
A modellkockázatokat jellemzően többdimenziós pontozási mátrix segítségével értékelik:
$$
KockázatiPontszám = Valószínűség × Hatás × Észlelhetőség
$$  
Az egyes tényezők alábontása:
- **Valószínűség:** adat-sodródás, rendszerkitettség vagy támadási felület.  
- **Hatás:** üzleti veszteség, etikai kár vagy megfelelőségi sérülés.  
- **Észlelhetőség:** monitorozási lefedettség, auditkésleltetés, riasztási pontosság. 📊  

---

## 🔐 Risk Control and Mitigation / Kockázatkezelési stratégiák

**EN:**  
Mitigation strategies should align with model criticality:
- **High-risk models:** require independent validation and dual control review.  
- **Medium-risk models:** require periodic revalidation and governance reporting.  
- **Low-risk models:** can follow lightweight assurance with automated controls.  
All controls and mitigations are logged in [[audit_logging_and_traceability]] and linked to governance baselines ([[control_framework_and_baselines]]).  

**HU:**  
A mérséklési stratégiákat a modell kritikalitásához kell igazítani:  
- **Magas kockázatú modellek:** független érvényesítést és kettős kontroll-felülvizsgálatot igényelnek.  
- **Közepes kockázatú modellek:** időszakos újraértékelést és irányítási jelentést.  
- **Alacsony kockázatú modellek:** automatizált kontrollokkal ellátott, egyszerűsített garanciát követhetnek.  
Minden kontrollt és intézkedést rögzíteni kell az [[audit_logging_and_traceability]] rendszerében, és az [[control_framework_and_baselines]] szerinti alapokhoz kell kapcsolni. 🧱  

---

## ⚖️ Governance and Compliance Context / Irányítási és megfelelőségi kontextus

**EN:**  
Under major frameworks:
- **NIST AI RMF:** risk registers support the “Govern” and “Manage” phases.  
- **ISO 42001:** requires documentation of AI-related risks and mitigation plans.  
- **EU AI Act:** mandates risk documentation for high-risk systems (Article 9).  
Model risk registers are thus both a **compliance artifact** and a **governance instrument**.  

**HU:**  
A főbb keretrendszerek alapján:  
- **NIST AI RMF:** a kockázati nyilvántartások a „Govern” és „Manage” fázisokat támogatják.  
- **ISO 42001:** előírja az MI-hez kapcsolódó kockázatok és mérséklési tervek dokumentálását.  
- **EU AI Act:** kötelezővé teszi a kockázati dokumentációt a magas kockázatú rendszerek esetében (9. cikk).  
A modellkockázati nyilvántartás így egyszerre **megfelelőségi bizonyíték** és **irányítási eszköz**. ⚖️  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Model Risk Management will evolve into **AI-driven risk orchestration**, where systems automatically detect, quantify, and mitigate risks in real time.  
Future model registers will integrate with monitoring dashboards and compliance engines, forming a **self-updating risk graph**.  
Ultimately, MRM will move from documentation to **autonomous assurance**.  

**HU:**  
A modellkockázat-kezelés a jövőben **MI-alapú kockázat-orchesztrációvá** fejlődik, ahol a rendszerek automatikusan észlelik, kvantifikálják és mérséklik a kockázatokat valós időben.  
A jövő modell-nyilvántartásai integrálódnak a monitorozási irányítópultokkal és megfelelőségi motorokkal, **önfrissülő kockázati gráfot** alkotva.  
Így a MRM a dokumentációs folyamatról **autonóm garanciarendszerré** válik. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What is the purpose of a Model Risk Register?  
2. How do quantitative and qualitative assessments complement each other in MRM?  
3. What types of risks should be tracked in the register?  
4. How does the register link to validation, audit, and governance layers?  
5. Which frameworks legally require documented model risk management?  
6. How could AI-driven automation transform future MRM processes?  

---

> “You can’t govern what you can’t measure — and you can’t trust what you don’t document.”
