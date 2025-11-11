---
version: "3.2"
section_type: "risk"
agent: "Principle Engineer"
---
---
title: Control Framework and Baselines
phase: Governance
category: Control Architecture & Assurance
difficulty: Advanced
related: [ai_governance_and_policy, ai_risk_assessment_methodology, regulatory_and_legal_compliance, audit_logging_and_traceability, continuous_validation_and_review]
updated: 2025-11-10
---

# 🧱 Control Framework and Baselines / Kontrollkeret és alapbiztonsági szintek

**EN:**  
A control framework defines *how security, ethics, and governance are operationalized* across the AI lifecycle.  
It translates abstract principles (like fairness or accountability) into **enforceable rules, measurable baselines, and continuous controls**.  
Baselines, in turn, represent the **minimum acceptable trust posture** — the level below which AI deployment becomes non-compliant or unsafe.  

**HU:**  
A kontrollkeret azt határozza meg, *hogyan válik a biztonság, etika és irányítás gyakorlattá* az MI-életciklus során.  
Az elvont elveket (pl. méltányosság, elszámoltathatóság) **végrehajtható szabályokká, mérhető alapértékekké és folyamatos kontrollokká** alakítja.  
Az alapbiztonsági szintek pedig a **minimálisan elfogadható bizalmi állapotot** jelentik — azt a határt, ami alatt az MI-üzembe helyezése már nem felel meg az elvárásoknak. 🧩  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
A control framework aligns organizational goals, regulatory duties, and risk management.  
It defines *who controls what, when, and how* — ensuring accountability across both technical and human layers.  
Baselines translate governance policies into actionable, measurable safeguards.  

**HU:**  
A kontrollkeret összehangolja a szervezeti célokat, a jogi kötelezettségeket és a kockázatkezelést.  
Meghatározza, *ki mit, mikor és hogyan ellenőriz*, így biztosítva az elszámoltathatóságot a technikai és emberi rétegekben egyaránt.  
Az alapbiztonsági szintek az irányítási elveket **mérhető védelmi követelményekké** fordítják le. ⚙️  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
Control frameworks bridge the gap between *intent* and *implementation*.  
They ensure that every AI activity — from dataset ingestion to model serving — follows a verifiable standard of trust.  
Baselines act as the **guardrails** of that standard, establishing minimum thresholds for security, compliance, and fairness.  

**HU:**  
A kontrollkeretek hidat képeznek az *elvárás* és a *megvalósítás* között.  
Biztosítják, hogy az MI-folyamatok — az adatok betöltésétől a modellkiszolgálásig — egy **ellenőrizhető bizalmi szabvány** mentén történjenek.  
Az alapbiztonsági szintek **korlátként** szolgálnak: rögzítik a biztonság, a megfelelés és a méltányosság minimális elvárt szintjét. 🧱  

---

## 🧩 Control Categories / Kontrollkategóriák

**EN:**  
AI security controls can be grouped into four layers:
1. **Strategic Controls** — governance, ethics, accountability.  
2. **Technical Controls** — encryption, access control, attestation, validation.  
3. **Operational Controls** — monitoring, incident response, and auditing.  
4. **Compliance Controls** — legal alignment, evidence, and continuous certification.  

**HU:**  
Az MI-biztonsági kontrollok négy fő rétegbe sorolhatók:  
1. **Stratégiai kontrollok** — irányítás, etika, elszámoltathatóság.  
2. **Technikai kontrollok** — titkosítás, hozzáférés-kezelés, hitelesítés, érvényesítés.  
3. **Működési kontrollok** — megfigyelés, incidenskezelés és auditálás.  
4. **Megfelelőségi kontrollok** — jogi illeszkedés, bizonyíték és folyamatos tanúsítás. 🧠  

---

## ⚙️ Control Lifecycle / A kontrollok életciklusa

**EN:**  
Control design follows a cyclical model:  
1. **Define:** identify objectives and map to regulations ([[regulatory_and_legal_compliance]]).  
2. **Implement:** apply controls to systems and processes.  
3. **Validate:** test control effectiveness ([[assurance_testing_and_validation]]).  
4. **Monitor:** detect drift or degradation ([[continuous_validation_and_review]]).  
5. **Improve:** refine controls after audit feedback ([[audit_logging_and_traceability]]).  

**HU:**  
A kontrolltervezés ciklikus folyamat:  
1. **Meghatározás:** célok kijelölése és szabályozásokhoz való illesztés ([[regulatory_and_legal_compliance]]).  
2. **Bevezetés:** kontrollok alkalmazása rendszerekben és folyamatokban.  
3. **Érvényesítés:** a kontrollok hatékonyságának tesztelése ([[assurance_testing_and_validation]]).  
4. **Megfigyelés:** az eltérések és degradáció észlelése ([[continuous_validation_and_review]]).  
5. **Fejlesztés:** a kontrollok finomítása az auditvisszajelzések alapján ([[audit_logging_and_traceability]]). 🔄  

---

## 🧠 Baseline Standards / Alapbiztonsági szabványok

**EN:**  
AI baselines are derived from established control catalogs:
- **NIST SP 800-53 / CSF 2.0** → cybersecurity baseline.  
- **ISO 27001 & 42001** → information and AI governance baseline.  
- **MITRE ATLAS / OWASP ML Top 10** → threat-specific defensive baseline.  
- **EU AI Act Annex III** → high-risk category operational baseline.  

**HU:**  
Az MI-alapbiztonsági szintek meglévő kontroll-katalógusokból származnak:  
- **NIST SP 800-53 / CSF 2.0** → kiberbiztonsági alap.  
- **ISO 27001 & 42001** → információ- és MI-irányítási alap.  
- **MITRE ATLAS / OWASP ML Top 10** → fenyegetés-specifikus védelmi alap.  
- **EU AI Act III. Melléklet** → magas kockázatú rendszerek működési alapja. 📚  

---

## 🔐 Example: Control–Baseline Mapping / Példa: kontroll–alap leképezés

**EN:**  
- **Access Control (AC-01):** IAM policies for model APIs → Baseline: NIST IA-5 & ISO 27002-9.  
- **Model Integrity (AI-05):** Signed release & checksum validation → Baseline: NIST SC-12 & EU AI Act Art. 12.  
- **Bias Monitoring (AI-12):** Fairness metrics audit → Baseline: ISO 42001 §7.4 / NIST AI RMF “Measure.”  
- **Incident Logging (AU-08):** Immutable audit trail → Baseline: NIST AU-2 / ISO 27037.  

**HU:**  
- **Hozzáférés-kezelés (AC-01):** IAM-szabályok a modell API-kra → Alap: NIST IA-5 és ISO 27002-9.  
- **Modell-integritás (AI-05):** Aláírt kiadás + checksum-ellenőrzés → Alap: NIST SC-12 és EU AI Act 12. cikk.  
- **Torzítás-monitorozás (AI-12):** Méltányossági metrikák auditja → Alap: ISO 42001 §7.4 / NIST AI RMF „Measure”.  
- **Incidens-naplózás (AU-08):** Megváltoztathatatlan auditnyom → Alap: NIST AU-2 / ISO 27037. 🧾  

---

## ⚖️ Governance Integration / Irányítási integráció

**EN:**  
Control frameworks are the **execution layer** of [[ai_governance_and_policy]].  
They turn policies into measurable evidence of compliance.  
Without baselines, governance remains theoretical; with them, it becomes **auditable and defensible**.  

**HU:**  
A kontrollkeretek az [[ai_governance_and_policy]] **végrehajtási rétegét** képezik.  
A szabályzatokat mérhető megfelelőségi bizonyítékokká alakítják.  
Alapbiztonsági szintek nélkül az irányítás elméleti marad; velük együtt **auditálható és megvédhető** rendszerré válik. 🧭  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Next-generation control frameworks will be **dynamic and adaptive** — adjusting baselines based on model behavior, risk score, and compliance posture.  
Machine-readable controls and AI-driven policy engines will allow real-time enforcement across hybrid environments.  
The future baseline will **evolve with the system it protects**.  

**HU:**  
A jövő kontrollkeretei **dinamikusak és adaptívak** lesznek — az alapbiztonsági szinteket a modell viselkedése, kockázati szintje és megfelelőségi állapota alapján módosítják.  
A géppel olvasható kontrollok és az MI-alapú szabályzat-motorok valós idejű érvényesítést tesznek lehetővé hibrid környezetekben.  
A jövő alapbiztonsági szintje **együtt fejlődik majd azzal a rendszerrel, amit véd**. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What is the difference between a control framework and a baseline?  
2. How do control frameworks translate governance policies into technical actions?  
3. Which global standards influence AI control baselines?  
4. How can controls be validated and improved continuously?  
5. Why are adaptive baselines critical for modern AI systems?  
6. How does control–baseline mapping enhance auditability?  
7. What role will AI play in next-generation automated control enforcement?  

---

> “Policy defines intent; control proves action; baseline sustains trust.”
