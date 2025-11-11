---
version: "3.2"
section_type: "detection_index"
agent: "Index Architect"
---
# 🧠 Detection Index

---

## 🌍 Purpose / Cél

**EN:**  
The **Detection Index** provides a unified map of all detection mechanisms within the AI Security Vault — covering threats that target data, models, prompts, pipelines, and runtime environments.  
Detection is the *sensory layer* of AI defense: it observes, measures, and identifies abnormal signals before or during an attack.  

Each detection module complements prevention and response — together forming the “eyes and ears” of the AI security ecosystem. 👁️🧩  

**HU:**  
A **Detection Index** az MI Security Vault összes felismerési mechanizmusának egységes térképe — lefedve az adatokat, modelleket, promptokat, pipeline-okat és futásidejű környezeteket célzó támadásokat.  
A detekció az MI-védelem *érzékszervi rétege*: megfigyel, mér és azonosítja az anomáliákat a támadás előtt vagy közben.  

Minden detekciós modul a megelőzést és a reagálást egészíti ki — együtt az MI-biztonsági ökoszisztéma „szemei és fülei”. 👁️🧩  

---

## 🧱 Detection Layers / Detekciós rétegek

**EN:**  
AI detection mechanisms operate across five main layers:

### 1️⃣ Data-Level Detection  
- **[[data_poisoning_detection|Data Poisoning Detection]]** — finds manipulated or mislabeled samples.  
- **[[data_provenance|Data Provenance Tracking]]** — verifies dataset origin and lineage integrity.  
- **[[input_sanitization|Input Sanitization]]** — filters untrusted data before entering the model.  
- **[[differential_privacy|Differential Privacy]]** — indirectly detects data leaks by bounding re-identification risk.  

### 2️⃣ Input & Adversarial Detection  
- **[[adversarial_input_detection|Adversarial Input Detection]]** — identifies perturbed or adversarial inputs.  
- **[[prompt_injection_and_rag_attacks|Prompt Injection Detection]]** — flags malicious RAG or LLM context manipulations.  
- **[[rate_limiting_and_quota|Rate-Limit Telemetry]]** — detects abnormal query spikes or probing.  
- **[[deception_and_honeypots|Honeypot Detection Systems]]** — lure and record adversarial behavior in real time.  

### 3️⃣ Model Behavior Detection  
- **[[model_monitoring|Model Monitoring]]** — observes model confidence, drift, and anomalies.  
- **[[consistency_audit|Consistency Auditing]]** — detects version drift and logical inconsistencies.  
- **[[adversarial_training|Adversarial Robustness Evaluation]]** — detects gaps during retraining.  
- **[[explainability|Explainability Analysis]]** — identifies unexplainable or suspicious reasoning patterns.  

### 4️⃣ Runtime & Infrastructure Detection  
- **[[runtime_isolation_and_sandboxing|Runtime Isolation Breach Detection]]** — identifies container or process escape attempts.  
- **[[observability_and_monitoring|Security Observability]]** — aggregates telemetry across all layers.  
- **[[ai_supply_chain_security|Supply Chain Validation]]** — detects tampered dependencies or compromised models.  
- **[[sbom|SBOM Drift Detection]]** — tracks version and signature mismatches in deployed components.  

### 5️⃣ Governance & Forensic Detection  
- **[[incident_response_for_ai|AI Incident Detection & Response]]** — automates threat triage and response workflows.  
- **[[deception_and_honeypots|Deception Intelligence]]** — collects forensic traces for attribution.  
- **[[audit_logging|Audit & Logging Integrity]]** — detects log tampering and forensic inconsistencies.  
- **[[ai_governance|AI Governance Oversight]]** — enforces compliance detection for model misuse or bias.  

**HU:**  
Az MI-detekció öt fő rétegben működik:

### 1️⃣ Adat-szintű detekció  
- **[[data_poisoning_detection|Adatmérgezés-felismerés]]** — manipulált vagy rosszul címkézett minták azonosítása.  
- **[[data_provenance|Adat-eredet követés]]** — az adathalmaz forrásának és integritásának ellenőrzése.  
- **[[input_sanitization|Bemenet-tisztítás]]** — nem megbízható adatok szűrése a modell előtt.  
- **[[differential_privacy|Differenciális adatvédelem]]** — közvetett módon jelzi az adat-szivárgási kockázatot.  

### 2️⃣ Bemeneti és adverszáriális detekció  
- **[[adversarial_input_detection|Adverszáriális bemenet-észlelés]]** — pertubált vagy szándékosan megtévesztő inputok felismerése.  
- **[[prompt_injection_and_rag_attacks|Prompt Injection-felismerés]]** — rosszindulatú kontextus-manipulációk azonosítása RAG/LLM környezetben.  
- **[[rate_limiting_and_quota|Rate-limit telemetria]]** — szokatlan lekérdezés-sűrűség vagy szondázás észlelése.  
- **[[deception_and_honeypots|Honeypot rendszerek]]** — támadói viselkedés valós idejű csapdába ejtése és rögzítése.  

### 3️⃣ Modell-viselkedési detekció  
- **[[model_monitoring|Modell-monitorozás]]** — bizalmi értékek, drift és anomáliák megfigyelése.  
- **[[consistency_audit|Konzisztencia-auditálás]]** — verziók közötti eltérések és logikai inkonzisztenciák felismerése.  
- **[[adversarial_training|Robusztusság-értékelés]]** — a modell sebezhetőségeinek azonosítása újratanításkor.  
- **[[explainability|Magyarázhatósági elemzés]]** — gyanús vagy nem értelmezhető döntési minták észlelése.  

### 4️⃣ Futásidejű és infrastrukturális detekció  
- **[[runtime_isolation_and_sandboxing|Futásidejű izoláció megsértésének észlelése]]** — konténer- vagy folyamatkitörési próbálkozások felismerése.  
- **[[observability_and_monitoring|Biztonsági megfigyelés]]** — telemetria gyűjtése minden rétegből.  
- **[[ai_supply_chain_security|Ellátási lánc-validálás]]** — kompromittált függőségek és modellek azonosítása.  
- **[[sbom|SBOM drift detekció]]** — verzió- és aláírás-eltérések figyelése a komponensekben.  

### 5️⃣ Irányítási és forenzikus detekció  
- **[[incident_response_for_ai|Incidens-felismerés és válasz]]** — fenyegetések automatikus osztályozása és reagálása.  
- **[[deception_and_honeypots|Megtévesztéses intelligencia]]** — forenzikus nyomok gyűjtése attribúcióhoz.  
- **[[audit_logging|Auditnapló-integritás]]** — naplóhamisítás vagy forenzikus inkonzisztencia felismerése.  
- **[[ai_governance|MI-irányítási felügyelet]]** — modell-visszaélések és torzítások megfelelőségi detektálása.  

---

## 🔍 Core Detection Principles / Alapelvi detekciós irányok

**EN:**  
- **Anomaly-based detection:** learn normal behavior → flag deviations.  
- **Signature-based detection:** detect known patterns or attack fingerprints.  
- **Behavioral correlation:** aggregate signals across data, model, and runtime.  
- **Adversarial awareness:** anticipate that attackers adapt to detectors.  
- **Explainability-linked detection:** treat unexplained outputs as potential compromises.  

**HU:**  
- **Anomália-alapú detekció:** a normál viselkedés megtanulása, majd az eltérések jelzése.  
- **Aláírás-alapú detekció:** ismert támadási minták vagy fingerprint-ek felismerése.  
- **Viselkedés-korreláció:** jelek összekapcsolása adat-, modell- és futásidő-szinten.  
- **Adverszáriális tudatosság:** figyelembe veszi, hogy a támadók alkalmazkodnak a detektorokhoz.  
- **Magyarázhatósághoz kötött detekció:** a nem magyarázható eredmények potenciális kompromittálásként kezelése.  

---

## 🔗 Integration Across the Vault / Kapcsolódás a Vault rendszeréhez

**EN:**  
Detection modules feed into:  
- [[observability_and_monitoring|Observability]] — central telemetry  
- [[incident_response_for_ai|Incident Response]] — automated alerting and quarantine  
- [[governance_index|Governance Index]] — compliance mapping  
- [[defense_index|Defense Index]] — upstream correlation with mitigations  

**HU:**  
A detekciós modulok kimenetei kapcsolódnak:  
- [[observability_and_monitoring|Observability]] — központi telemetria  
- [[incident_response_for_ai|Incidenskezelés]] — automatizált riasztás és izolálás  
- [[governance_index|Irányítási index]] — megfelelőségi térkép  
- [[defense_index|Védelmi index]] — összekapcsolás a megelőző kontrollokkal  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What is the role of detection in the broader AI security lifecycle?  
2. How do data-level and runtime-level detection differ in purpose and method?  
3. Why must detection be combined with deception and observability?  
4. Which detection layer is most critical in protecting RAG-based LLM systems, and why?  
5. How can explainability techniques assist in adversarial behavior detection?  

---

> “Detection is awareness — it’s how intelligence systems learn to defend themselves.” 🧠
