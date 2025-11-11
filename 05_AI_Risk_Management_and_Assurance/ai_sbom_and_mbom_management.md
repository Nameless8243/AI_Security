---
version: "3.2"
section_type: "assurance"
agent: "Core Concepts Engineer"
---
---
title: AI SBOM and MBOM Management
phase: Governance
category: Supply Chain Security
difficulty: Advanced
related: [ai_model_provenance_and_lineage, audit_logging_and_traceability, model_release_and_signing, environment_hardening, regulatory_and_legal_compliance]
updated: 2025-11-10
---

# 🧾 AI SBOM and MBOM Management / MI SBOM- és MBOM-kezelés

**EN:**  
In AI security, **SBOM (Software Bill of Materials)** and **MBOM (Model Bill of Materials)** are the blueprints of trust.  
They describe the *components, dependencies, and origins* of software and models across the AI pipeline.  
Maintaining these inventories allows organizations to trace vulnerabilities, manage licenses, and prove integrity during audits — ensuring that no hidden code, dataset, or dependency compromises the system.  

**HU:**  
Az MI-biztonságban az **SBOM (Software Bill of Materials)** és az **MBOM (Model Bill of Materials)** a bizalom tervrajzai.  
Leírják a szoftverek és modellek *összetevőit, függőségeit és eredetét* az MI-pipeline teljes hosszában.  
Ezeknek a leltáraknak a fenntartása lehetővé teszi a sebezhetőségek visszakövetését, a licencek kezelését és az integritás igazolását audit során — biztosítva, hogy ne maradjon rejtett kód, adat vagy függőség, ami veszélyeztetné a rendszert. 🌍  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
- **SBOM** = a complete manifest of software libraries, packages, and configurations.  
- **MBOM** = a structured record of model artifacts — datasets, hyperparameters, algorithms, weights, and signing data.  

Together, they form the **AI Supply Chain Map**, enabling visibility into both software and model provenance ([[ai_model_provenance_and_lineage]]).  

**HU:**  
- **SBOM:** a szoftver-könyvtárak, csomagok és konfigurációk teljes listája.  
- **MBOM:** a modellek strukturált leltára — adathalmazok, hiperparaméterek, algoritmusok, súlyok és aláírási adatok.  

Együtt alkotják az **MI-ellátási lánc térképét**, amely átláthatóvá teszi a szoftver- és modell-eredetet ([[ai_model_provenance_and_lineage]]). 🧩  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
AI systems are composite organisms — built from thousands of libraries, datasets, and pretrained models.  
SBOM and MBOM management turns this complexity into **structured transparency**.  
They allow you to answer three critical questions at any time:
1. What is inside this model or system?  
2. Who created or approved each component?  
3. What vulnerabilities or licenses affect them?  

**HU:**  
Az MI-rendszerek összetett organizmusok — több ezer könyvtárból, adathalmazból és előtanított modellből épülnek fel.  
Az SBOM- és MBOM-kezelés ezt a komplexitást **strukturált átláthatósággá** alakítja.  
Lehetővé teszi három alapvető kérdés megválaszolását bármikor:  
1. Mi van ebben a modellben vagy rendszerben?  
2. Ki hozta létre vagy hagyta jóvá az egyes komponenseket?  
3. Milyen sebezhetőségek vagy licencek vonatkoznak rájuk? 🧱  

---

## 🧠 SBOM: Software Supply Chain Visibility / SBOM: a szoftverellátási lánc átláthatósága

**EN:**  
An SBOM ensures that every piece of software — from Python libraries to Docker images — is identified and verified.  
Key attributes include:  
- package name and version,  
- source and license,  
- checksum or hash,  
- known vulnerabilities (via CVE references),  
- and signing metadata.  

**HU:**  
Az SBOM biztosítja, hogy minden szoftver-összetevő — a Python-könyvtáraktól a Docker-képekig — azonosítható és ellenőrzött legyen.  
Fontos attribútumai:  
- csomagnév és verzió,  
- forrás és licenc,  
- checksum vagy hash,  
- ismert sebezhetőségek (CVE-hivatkozások),  
- aláírási metaadatok. 🧾  

---

## 🧬 MBOM: Model Supply Chain Integrity / MBOM: a modell-ellátási lánc integritása

**EN:**  
MBOM extends the SBOM idea to AI models. It documents:
- training datasets and their lineage,  
- preprocessing pipelines and transformations,  
- algorithms and frameworks used,  
- model weights, signatures, and checkpoints,  
- and responsible owners or approvers.  

This provides **forensic visibility** — if a model behaves unexpectedly, the MBOM shows *which ingredient caused the deviation*.  

**HU:**  
Az MBOM az SBOM elvét az MI-modellekre terjeszti ki. Dokumentálja:  
- a tanítóadatokat és azok származási láncát,  
- az előfeldolgozó pipeline-okat és transzformációkat,  
- a felhasznált algoritmusokat és frameworköket,  
- a modell-súlyokat, aláírásokat és checkpointokat,  
- valamint a felelős személyeket vagy jóváhagyókat.  

Ez **forenzikus átláthatóságot** biztosít — ha a modell váratlanul viselkedik, az MBOM megmutatja, *melyik összetevő volt az oka*. 🧬  

---

## ⚙️ Implementation Guidelines / Megvalósítási irányelvek

**EN:**  
1. **Automate SBOM generation** using tools like Syft, Anchore, or CycloneDX during CI/CD builds.  
2. **Generate MBOM artifacts** at model training and release time (MLflow, Weights & Biases, or custom scripts).  
3. **Link both SBOM and MBOM** in a shared provenance registry ([[ai_model_provenance_and_lineage]]).  
4. **Digitally sign BOMs** using organizational PKI ([[model_release_and_signing]]).  
5. **Scan for CVEs and license violations** before deployment.  
6. **Integrate with governance reports** for compliance and transparency ([[transparency_reporting_framework]]).  

**HU:**  
1. **Automatizáld az SBOM-generálást** Syft, Anchore vagy CycloneDX segítségével a CI/CD build-folyamat során.  
2. **Generálj MBOM-artefaktumokat** a modelltanítás és kiadás idején (MLflow, Weights & Biases vagy egyedi szkriptek használatával).  
3. **Kapcsold össze az SBOM-ot és az MBOM-ot** egy közös származási nyilvántartásban ([[ai_model_provenance_and_lineage]]).  
4. **Digitálisan írd alá a BOM-okat** a szervezeti PKI segítségével ([[model_release_and_signing]]).  
5. **Végezze el a CVE- és licenc-szkennelést** az üzembe helyezés előtt.  
6. **Integráld az eredményeket** a megfelelőségi és átláthatósági jelentésekbe ([[transparency_reporting_framework]]). 🧱  

---

## 🔐 Security and Compliance Benefits / Biztonsági és megfelelőségi előnyök

**EN:**  
- Enables rapid vulnerability remediation.  
- Provides traceable evidence for audits.  
- Supports regulatory requirements under [[regulatory_and_legal_compliance]] (e.g., EU AI Act Article 12).  
- Detects unapproved open-source components.  
- Strengthens model supply chain integrity.  

**HU:**  
- Lehetővé teszi a sebezhetőségek gyors javítását.  
- Visszakövethető bizonyítékot biztosít az auditokhoz.  
- Támogatja a [[regulatory_and_legal_compliance]] követelményeit (pl. EU AI Act 12. cikk).  
- Észleli az engedély nélküli nyílt forrású komponenseket.  
- Megerősíti a modell-ellátási lánc integritását. 🛡️  

---

## ⚖️ Governance and Lifecycle Integration / Irányítási és életciklus-integráció

**EN:**  
SBOM and MBOM together form a **traceability backbone** across the AI lifecycle:  
- During training → dataset and library documentation.  
- During deployment → versioned model and image signatures.  
- During monitoring → vulnerability scanning and patch tracking.  

This structure supports both [[ai_governance_and_policy]] and [[audit_logging_and_traceability]] as continuous compliance evidence.  

**HU:**  
Az SBOM és MBOM együtt az MI-életciklus **visszakövethetőségi gerincét** alkotják:  
- A tanítás során → az adathalmazok és könyvtárak dokumentálása.  
- Az üzembe helyezés során → verziózott modellek és képaláírások kezelése.  
- A megfigyelés során → sebezhetőségi szkennelés és patch-követés.  

Ez a struktúra támogatja mind az [[ai_governance_and_policy]], mind az [[audit_logging_and_traceability]] rendszereit — **folyamatos megfelelőségi bizonyítékként**. ⚙️  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Future SBOM/MBOM systems will adopt **machine-readable provenance graphs**, enabling automated verification and blockchain-backed attestation.  
AI supply chains will be continuously monitored by autonomous agents that correlate SBOMs, MBOMs, and runtime telemetry — detecting tampering or outdated dependencies in real time.  

**HU:**  
A jövő SBOM/MBOM rendszerei **géppel olvasható származási gráfokat** alkalmaznak, amelyek automatizált ellenőrzést és blockchain-alapú hitelesítést tesznek lehetővé.  
Az MI-ellátási láncokat **autonóm ügynökök** fogják folyamatosan felügyelni, amelyek összekapcsolják az SBOM-, MBOM- és futásidejű telemetriai adatokat — így valós időben észlelik a manipulációt vagy az elavult függőségeket. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What is the difference between SBOM and MBOM in AI systems?  
2. Why are SBOM and MBOM critical for supply chain integrity?  
3. How do BOMs integrate with governance and audit processes?  
4. What key information must an MBOM contain for compliance?  
5. Which tools and standards can automate SBOM/MBOM generation?  
6. How can BOM signing enhance traceability and trust?  
7. What future technologies may automate AI supply chain attestation?  

---

> “Transparency without structure is noise — SBOM and MBOM turn it into verified trust.”
