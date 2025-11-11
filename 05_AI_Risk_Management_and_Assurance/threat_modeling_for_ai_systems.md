---
version: "3.2"
section_type: "risk"
agent: "Threat Mapper"
---
---
title: Threat Modeling for AI Systems
phase: Design
category: Risk Analysis & Architecture
difficulty: Advanced
related: [data_poisoning_attacks, model_stealing_and_extraction, adversarial_training, ai_risk_assessment_methodology, control_framework_and_baselines]
updated: 2025-11-10
---

# ⚔️ Threat Modeling for AI Systems / Fenyegetésmodellezés MI-rendszerekhez

**EN:**  
Threat modeling for AI identifies, analyzes, and prioritizes **potential adversarial paths and systemic weaknesses** across the model lifecycle.  
It brings structured reasoning to AI risk — transforming abstract fears into *actionable mitigations*.  
Unlike traditional IT systems, AI introduces **new threat surfaces** (data, models, and prompts), demanding domain-specific frameworks and defensive patterns.  

**HU:**  
Az MI-rendszerek fenyegetésmodellezése az **adverszáriális utak és rendszerhibák azonosítását, elemzését és rangsorolását** jelenti az egész modelléletciklusban.  
Célja, hogy a kockázatokat strukturált gondolkodással *konkrét megelőző intézkedésekké* alakítsa.  
A hagyományos IT-rendszerektől eltérően az MI **új fenyegetési felületeket** hoz létre (adat, modell, prompt), ezért speciális módszertanokra és védelmi mintákra van szükség. 🧠  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
Threat modeling in AI combines:
- **Adversarial thinking:** how attackers can exploit model behavior.  
- **Systematic decomposition:** understanding components, dependencies, and data flows.  
- **Attack surface mapping:** identifying where control, data, or trust can be subverted.  
It ensures that security, privacy, and fairness controls are *built in* — not bolted on.  

**HU:**  
Az MI-fenyegetésmodellezés három fő megközelítést egyesít:  
- **Adverszáriális gondolkodás:** hogyan tudja a támadó kihasználni a modell viselkedését.  
- **Rendszeres bontás:** a komponensek, függőségek és adatáramlás megértése.  
- **Támadási felületek feltérképezése:** hol sérülhet a kontroll, az adat vagy a bizalom.  
Így biztosítható, hogy a biztonság, adatvédelem és méltányosság **beépüljön a rendszerbe, ne utólag toldják hozzá**. ⚙️  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
Traditional STRIDE or PASTA frameworks are not sufficient for AI because they assume deterministic systems.  
AI behaves probabilistically and learns from mutable data — its “attack surface” *evolves over time*.  
Therefore, threat modeling must integrate **learning dynamics, model drift, and adversarial adaptation**.  

**HU:**  
A klasszikus STRIDE vagy PASTA keretrendszerek nem elegendők az MI-re, mert determinisztikus rendszerekkel számolnak.  
Az MI viszont valószínűségi módon viselkedik, és változó adatokból tanul — vagyis a *támadási felülete folyamatosan fejlődik*.  
Ezért a fenyegetésmodellezésnek figyelembe kell vennie a **tanulási dinamikát, a modell-sodródást és az adverszáriális alkalmazkodást**. 🔄  

---

## 🧩 Threat Modeling Lifecycle / Fenyegetésmodellezési életciklus

**EN:**  
1. **Define the scope:** identify AI assets — datasets, models, APIs, pipelines.  
2. **Decompose the system:** visualize data and control flows.  
3. **Identify threats:** use frameworks (e.g., MITRE ATLAS, OWASP ML Top 10).  
4. **Assess risks:** calculate impact × likelihood ([[ai_risk_assessment_methodology]]).  
5. **Define mitigations:** design controls and align with [[control_framework_and_baselines]].  
6. **Validate continuously:** monitor drift and new adversarial techniques ([[continuous_validation_and_review]]).  

**HU:**  
1. **Határozd meg a hatókört:** azonosítsd az MI-eszközöket — adathalmazok, modellek, API-k, pipeline-ok.  
2. **Bontsd fel a rendszert:** vizualizáld az adat- és vezérlésáramlást.  
3. **Azonosítsd a fenyegetéseket:** használj kereteket (pl. MITRE ATLAS, OWASP ML Top 10).  
4. **Értékeld a kockázatokat:** számítsd ki a hatás × valószínűség értéket ([[ai_risk_assessment_methodology]]).  
5. **Határozd meg a megelőzéseket:** tervezd meg a kontrollokat a [[control_framework_and_baselines]] alapján.  
6. **Folyamatosan érvényesíts:** figyeld a sodródást és az új támadási mintákat ([[continuous_validation_and_review]]). 🧱  

---

## ⚔️ AI-Specific Threat Categories / MI-specifikus fenyegetési kategóriák

**EN:**  
1. **Data Poisoning:** manipulation of training data to degrade performance ([[data_poisoning_attacks]]).  
2. **Model Extraction:** replication of model logic through API probing ([[model_stealing_and_extraction]]).  
3. **Membership Inference:** identifying whether specific data points were used in training.  
4. **Adversarial Perturbation:** crafting inputs that exploit model sensitivity.  
5. **Prompt Injection:** manipulating input text to subvert generative model behavior.  
6. **Model Drift Exploitation:** exploiting unmonitored updates or retraining pipelines.  
7. **Supply Chain Manipulation:** inserting malicious dependencies or pre-trained weights.  

**HU:**  
1. **Adatmérgezés:** a tanítóadat manipulálása a teljesítmény rombolása érdekében ([[data_poisoning_attacks]]).  
2. **Modellkivonás:** a modell logikájának másolása API-próbálgatással ([[model_stealing_and_extraction]]).  
3. **Tagsági következtetés:** annak kiderítése, hogy egy adott adat szerepelt-e a tanításban.  
4. **Adverszáriális perturbáció:** a modell érzékenységének kihasználása manipulált bemenetekkel.  
5. **Prompt Injection:** bemenet manipulálása a generatív modellek viselkedésének torzítására.  
6. **Modellsodródás kihasználása:** nem monitorozott újratanítás vagy frissítés manipulálása.  
7. **Ellátási lánc manipuláció:** rosszindulatú függőségek vagy előtanított súlyok beillesztése. 🧩  

---

## 🧮 Threat Prioritization Matrix / Fenyegetés-prioritási mátrix

**EN:**  
Threats can be scored using an AI-adapted DREAD model:
$$
Risk = (Damage + Reproducibility + Exploitability + Affected Users + Discoverability) / 5
$$  
High-risk vectors are then correlated with likelihood and mapped to specific AI layers (data, model, deployment).  

**HU:**  
A fenyegetések AI-ra adaptált DREAD-modellel értékelhetők:
$$
Kockázat = (Kár + Reprodukálhatóság + Kihasználhatóság + Érintett\ felhasználók + Felfedezhetőség) / 5
$$  
A magas kockázatú vektorokat ezután a valószínűséggel kombinálva hozzárendeljük az MI-rétegekhez (adat, modell, üzembe helyezés). 📊  

---

## 🔐 Defensive Design Principles / Védekezési tervezési elvek

**EN:**  
- **Minimize attack surface:** isolate training, inference, and deployment.  
- **Implement Zero Trust for AI pipelines** ([[zero_trust_for_ai]]).  
- **Verify all external inputs:** data, prompts, model updates.  
- **Embed anomaly detection and explainability controls** ([[model_integrity_monitoring]], [[ai_fairness_and_transparency_governance]]).  
- **Apply secure-by-design architecture:** least privilege, encryption, and PKI-based attestation ([[model_release_and_signing]]).  

**HU:**  
- **Csökkentsd a támadási felületet:** válaszd szét a tanítást, az inferenciát és az üzembe helyezést.  
- **Alkalmazd a Zero Trust elvet az MI-pipeline-okban** ([[zero_trust_for_ai]]).  
- **Ellenőrizd az összes külső bemenetet:** adatok, promptok, modellfrissítések.  
- **Építs be anomáliaérzékelést és magyarázhatósági kontrollokat** ([[model_integrity_monitoring]], [[ai_fairness_and_transparency_governance]]).  
- **Biztonságos tervezés:** legkisebb jogosultság, titkosítás és PKI-alapú hitelesítés ([[model_release_and_signing]]). 🛡️  

---

## ⚖️ Governance Integration / Irányítási integráció

**EN:**  
Threat modeling outputs directly inform governance and compliance frameworks:
- Feed results into [[model_risk_management_and_registers]] and [[ai_risk_assessment_methodology]].  
- Document mitigations in control baselines ([[control_framework_and_baselines]]).  
- Communicate findings via structured reporting ([[reporting_and_communication]]).  

**HU:**  
A fenyegetésmodellezés eredményei közvetlenül beépülnek az irányítási és megfelelőségi keretekbe:  
- Az eredmények beépítése a [[model_risk_management_and_registers]] és [[ai_risk_assessment_methodology]] rendszerekbe.  
- A megelőző intézkedések dokumentálása a kontrollalapokban ([[control_framework_and_baselines]]).  
- Az eredmények kommunikálása strukturált jelentésekben ([[reporting_and_communication]]). ⚖️  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
AI threat modeling will evolve into **autonomous adversarial simulation systems** — where defensive AIs continuously predict, simulate, and neutralize emerging threats.  
Future frameworks will include **AI-vs-AI red teaming**, and threat models will update dynamically as the system learns and adapts.  

**HU:**  
Az MI-fenyegetésmodellezés a jövőben **autonóm adverszáriális szimulációs rendszerekké** fejlődik — ahol a védelmi MI folyamatosan előrejelzi, modellezi és semlegesíti az új fenyegetéseket.  
A jövő keretrendszerei tartalmazni fogják az **MI-ellen-MI red teaming** megközelítést, és a fenyegetésmodellek **dinamikusan frissülnek**, ahogy a rendszer tanul és alkalmazkodik. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What makes AI threat modeling different from traditional cybersecurity threat modeling?  
2. How does the AI lifecycle influence the evolving attack surface?  
3. What are the most critical AI-specific threats to consider?  
4. How can threat modeling be integrated into governance and control frameworks?  
5. What role might autonomous adversarial simulations play in the future?  

---

> “You cannot defend what you have not imagined — threat modeling is imagination made operational.”
