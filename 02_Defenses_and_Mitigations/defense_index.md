---
version: "3.2"
section_type: "defense_index"
agent: "Index Architect"
---
# 🛡️ Defense Index

---

## 🌍 Purpose / Cél

**EN:**  
The **Defense Index** serves as a structured navigation map across all defensive mechanisms in the Vault — from data-level hardening to model, pipeline, and system-level protections. It connects each family of defense strategies and highlights where they fit in the broader [[ai_security_lifecycle|AI Security Lifecycle]].  

This index is designed as a conceptual *threat-to-defense bridge*: every major attack vector (e.g., [[data_poisoning|Data Poisoning]], [[adversarial_example_attacks|Adversarial Examples]], [[model_stealing_and_extraction|Model Extraction]], [[prompt_injection_and_rag_attacks|Prompt Injection]], etc.) has one or more mapped countermeasures here.  

**HU:**  
A **Defense Index** az összes védelmi mechanizmus strukturált térképe a Vaultban — az adat-szintű védelmektől kezdve a modell-, pipeline- és rendszer-szintű megoldásokig. Összekapcsolja a védelmi stratégiák családjait, és megmutatja, hol illeszkednek a [[ai_security_lifecycle|MI-biztonsági életciklus]] tágabb keretébe.  

Ez az index egyfajta *támadás–védekezés híd*: minden fő támadási típushoz (pl. [[data_poisoning|Adatmérgezés]], [[adversarial_example_attacks|Adverszáriális példák]], [[model_stealing_and_extraction|Modell-lopás]], [[prompt_injection_and_rag_attacks|Prompt Injection]] stb.) megtalálhatók itt a megfelelő ellentechnikák.  

---

## 🧱 Layered Defense Architecture / Rétegzett védekezési architektúra

**EN:**  
AI security requires **defense-in-depth** — layered controls that protect across the entire lifecycle:

### 1️⃣ Data & Input Layer
- **[[data_sanitization|Data Sanitization]]** — removing or validating untrusted inputs  
- **[[data_provenance|Data Provenance]]** — tracking dataset origin & integrity  
- **[[data_poisoning_detection|Data Poisoning Detection]]** — anomaly and label consistency audits  
- **[[input_filtering|Input Filtering]]** — content moderation, schema validation, and injection prevention  
- **[[differential_privacy|Differential Privacy]]** — privacy-preserving data processing  

### 2️⃣ Model Layer
- **[[adversarial_training|Adversarial Training]]** — embedding adversarial examples during learning  
- **[[certified_robustness|Certified Robustness]]** — mathematically provable robustness bounds  
- **[[model_ensemble_defense|Model Ensembles]]** — diversity-based robustness  
- **[[regularization_and_smoothing|Regularization & Smoothing]]** — smoother decision boundaries  
- **[[model_monitoring|Model Monitoring]]** — drift and consistency checks post-deployment  

### 3️⃣ Pipeline Layer
- **[[ai_supply_chain_security|AI Supply Chain Security]]** — securing dependencies, models, and datasets  
- **[[ci_cd_hardening|CI/CD Hardening]]** — secured build and deployment pipelines  
- **[[model_serving_security|Model Serving Security]]** — API protection, rate limiting, authentication  
- **[[sbom|Software Bill of Materials (SBOM)]]** — transparency of components  
- **[[logging_and_audit|Logging & Audit Trails]]** — forensic visibility and traceability  

### 4️⃣ System & Retrieval Layer
- **[[prompt_injection_and_rag_attacks|Prompt Injection Defense]]** — context separation, retrieval validation  
- **[[retrieval_hardening|Retrieval Hardening]]** — allow-lists, content signing, provenance verification  
- **[[rag_sanitization|RAG Sanitization]]** — embedding validation and context role enforcement  
- **[[output_filtering|Output Filtering]]** — sensitive data redaction and hallucination prevention  
- **[[zero_trust|Zero Trust for AI Systems]]** — strict identity and access segmentation  

### 5️⃣ Governance & Oversight Layer
- **[[ai_governance|AI Governance]]** — policies, standards, risk categorization  
- **[[consistency_audit|Consistency Auditing]]** — cross-version and behavior drift checks  
- **[[compliance_frameworks|Compliance Frameworks]]** — NIST AI RMF, ISO/IEC 42001 alignment  
- **[[red_team_testing|Adversarial Red Teaming]]** — simulated attacks to measure resilience  
- **[[incident_response_for_ai|AI Incident Response]]** — detection, containment, and recovery workflows  

**HU:**  
Az MI-biztonság **többrétegű védekezést** igényel — olyan kontrollokat, amelyek lefedik az egész életciklust:

### 1️⃣ Adat- és bemenet-szint
- **[[data_sanitization|Adattisztítás]]** — nem megbízható adatok eltávolítása vagy validálása  
- **[[data_provenance|Adat-eredet követése]]** — az adathalmaz forrásának és integritásának nyomon követése  
- **[[data_poisoning_detection|Adatmérgezés-felismerés]]** — anomália és címkekonzisztencia ellenőrzés  
- **[[input_filtering|Bemenet-szűrés]]** — tartalomszűrés, sémaellenőrzés, injekció-megelőzés  
- **[[differential_privacy|Differenciális adatvédelem]]** — adatvédelmet biztosító feldolgozás  

### 2️⃣ Modell-szint
- **[[adversarial_training|Adversarial Training]]** — adverszáriális példákkal edzett robusztus modell  
- **[[certified_robustness|Tanúsított robusztusság]]** — matematikailag bizonyított robusztussági határok  
- **[[model_ensemble_defense|Model-ensemble védelem]]** — diverzitáson alapuló robusztusság  
- **[[regularization_and_smoothing|Regularizáció & simítás]]** — simább döntési határok kialakítása  
- **[[model_monitoring|Modell-monitorozás]]** — drift- és konzisztencia-ellenőrzés bevezetés után  

### 3️⃣ Pipeline-szint
- **[[ai_supply_chain_security|MI-ellátási lánc biztonság]]** — függőségek, modellek és adatok védelme  
- **[[ci_cd_hardening|CI/CD megerősítése]]** — biztonságos build- és bevezetési folyamatok  
- **[[model_serving_security|Modell-szolgáltatás biztonsága]]** — API-védelem, rate limiting, autentikáció  
- **[[sbom|SBOM]]** — komponensek átláthatósága  
- **[[logging_and_audit|Naplózás és auditálás]]** — forenzikus nyomkövethetőség biztosítása  

### 4️⃣ Rendszer- és visszakeresési szint
- **[[prompt_injection_and_rag_attacks|Prompt Injection védelem]]** — kontextus-elválasztás, visszakeresés validálás  
- **[[retrieval_hardening|Visszakeresés megerősítése]]** — allow-listák, aláírás, eredetellenőrzés  
- **[[rag_sanitization|RAG sanitizálás]]** — embedding-validálás, szerepkörök szétválasztása  
- **[[output_filtering|Kimenet-szűrés]]** — érzékeny adatok takarása, hallucináció-megelőzés  
- **[[zero_trust|Zero Trust az MI rendszerekben]]** — identitásalapú hozzáférés-szegmentálás  

### 5️⃣ Irányítás és felügyelet
- **[[ai_governance|MI-irányítás]]** — szabályok, standardok, kockázati kategorizálás  
- **[[consistency_audit|Konzisztencia-auditálás]]** — verzióközi és viselkedési eltérések ellenőrzése  
- **[[compliance_frameworks|Megfelelőségi keretrendszerek]]** — NIST AI RMF, ISO/IEC 42001 illesztés  
- **[[red_team_testing|Adverszáriális Red Teaming]]** — támadások szimulálása a védelem tesztelésére  
- **[[incident_response_for_ai|MI incidenskezelés]]** — észlelés, izolálás, helyreállítás  

---

## 🧠 Core Defensive Principles / Alapelvi védelmi irányok

**EN:**  
- **Defense-in-depth:** multiple, independent layers reduce single-point failure risk.  
- **Least privilege:** minimal access across data, models, APIs, and agents.  
- **Continuous validation:** reverify integrity at every lifecycle stage.  
- **Explainability as defense:** interpretability tools detect malicious drift and anomalous reasoning.  
- **Human-in-the-loop:** critical actions and overrides require human verification.  
- **Zero Trust mindset:** assume every component and external input can be hostile.

**HU:**  
- **Többrétegű védelem:** több, egymástól független réteg csökkenti az egyetlen hiba kockázatát.  
- **Legkisebb jogosultság elve:** minimális hozzáférés az adatokhoz, modellekhez, API-khoz és agentekhez.  
- **Folyamatos validálás:** minden életciklus-fázisban ellenőrizni kell az integritást.  
- **Magyarázhatóság mint védelem:** az értelmezhetőség segíti a rosszindulatú drift vagy anomália felismerését.  
- **Ember a folyamatban:** a kritikus döntésekhez emberi megerősítés szükséges.  
- **Zero Trust szemlélet:** minden komponens és bemenet potenciálisan ellenséges.

---

## 🔗 Cross-References / Kapcsolatok

**EN:**  
This index crosslinks with:  
- [[attack_index|Attack Index]] for corresponding offensive tactics  
- [[ai_security_lifecycle|AI Security Lifecycle]] for stage-wise defense mapping  
- [[governance_index|Governance Index]] for oversight frameworks  

**HU:**  
Ez az index összekapcsolódik a következőkkel:  
- [[attack_index|Attack Index]] — a támadási technikák párjai  
- [[ai_security_lifecycle|MI-biztonsági életciklus]] — védekezési térkép az életciklus mentén  
- [[governance_index|Governance Index]] — az irányítási és megfelelőségi keretrendszerek  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. How do the five defense layers interact to form defense-in-depth in AI systems?  
2. Which defenses mitigate poisoning and inference-time attacks respectively?  
3. How can governance frameworks strengthen technical defenses through policy and oversight?  
4. Why is Zero Trust critical in AI supply chains and RAG systems?  
5. Design a minimal defense stack for a small-scale AI API that still achieves layered security.

---

> “Every AI defense is a layer of trust — fragile alone, resilient together.” ⚖️
