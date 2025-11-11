---
version: "3.2"
section_type: "risk"
agent: "Lifecycle Analyst"
---
---
title: Supplier and Third-Party Risk for AI
phase: Governance
category: Supply Chain Assurance
difficulty: Advanced
related: [ai_supply_chain_attestation_and_audit, ai_sbom_and_mbom_management, regulatory_and_legal_compliance, ai_risk_assessment_methodology, model_risk_management_and_registers]
updated: 2025-11-10
---

# 🌐 Supplier and Third-Party Risk for AI / Beszállítói és harmadik féltől származó kockázatok az MI-ben

**EN:**  
AI systems rarely exist in isolation — they rely on a complex ecosystem of **vendors, APIs, models, and cloud services**.  
Each external dependency introduces potential weaknesses that can undermine the system’s integrity, privacy, or compliance posture.  
Supplier and third-party risk management ensures that the **trust you build internally is not lost externally**.  

**HU:**  
Az MI-rendszerek ritkán működnek elszigetelten — **szállítók, API-k, modellek és felhőszolgáltatások** összetett ökoszisztémájára épülnek.  
Minden külső függőség potenciális gyengeséget jelenthet, amely veszélyeztetheti a rendszer integritását, adatvédelmét vagy megfelelőségét.  
A beszállítói és harmadik féltől származó kockázatkezelés célja, hogy a **belsőleg felépített bizalom ne vesszen el a külső határokon**. 🧩  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
Supplier and third-party risk management (TPRM) for AI is the process of **evaluating, monitoring, and governing** all external entities that contribute to an AI system’s lifecycle.  
This includes:
- Cloud and infrastructure providers,  
- AI model vendors or pretrained model sources,  
- Data suppliers and labeling vendors,  
- Open-source libraries and API dependencies.  

**HU:**  
Az MI-hez kapcsolódó beszállítói és harmadik féltől származó kockázatkezelés (TPRM) az összes **külső entitás értékelését, megfigyelését és irányítását** jelenti, amely részt vesz az MI-rendszer életciklusában.  
Ide tartoznak:  
- a felhő- és infrastruktúraszolgáltatók,  
- az MI-modellbeszállítók és előtanított modellek forrásai,  
- az adatbeszállítók és címkéző vállalkozók,  
- a nyílt forrású könyvtárak és API-függőségek. ⚙️  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
Third-party trust is **not transferable** — each supplier must provide verifiable assurance.  
AI security extends beyond your code and data; it includes **the entire ecosystem** that influences your model’s behavior and governance posture.  
The goal of TPRM is to make this web of dependencies **transparent, auditable, and contractually accountable**.  

**HU:**  
A harmadik féltől származó bizalom **nem átruházható** — minden beszállítónak ellenőrizhető garanciát kell nyújtania.  
Az MI-biztonság nem korlátozódik a saját kódodra és adataidra; magában foglalja **az egész ökoszisztémát**, amely befolyásolja a modell viselkedését és irányítási helyzetét.  
A TPRM célja, hogy ez a függőségi háló **átlátható, auditálható és szerződésileg elszámoltatható** legyen. 🔐  

---

## 🧱 Risk Categories / Kockázati kategóriák

**EN:**  
Third-party risks in AI can be grouped into:
1. **Data Risks:** provenance, accuracy, licensing, and privacy.  
2. **Model Risks:** quality, robustness, and vulnerability of pretrained models.  
3. **Infrastructure Risks:** cloud configuration, shared responsibility, and key management.  
4. **Compliance Risks:** missing documentation or regulatory misalignment.  
5. **Ethical Risks:** opacity, bias inheritance, and social impact from external inputs.  

**HU:**  
Az MI-hez kapcsolódó harmadik féltől származó kockázatok az alábbi csoportokba sorolhatók:  
1. **Adatkockázatok:** származás, pontosság, licencelés, adatvédelem.  
2. **Modellkockázatok:** előtanított modellek minősége, robusztussága és sebezhetősége.  
3. **Infrastrukturális kockázatok:** felhőkonfiguráció, megosztott felelősség, kulcskezelés.  
4. **Megfelelőségi kockázatok:** hiányzó dokumentáció vagy szabályozási eltérés.  
5. **Etikai kockázatok:** átláthatatlanság, örökölt torzítások, külső hatások társadalmi következményei. 🌍  

---

## ⚙️ Evaluation and Due Diligence / Értékelés és átvilágítás

**EN:**  
A supplier’s trustworthiness must be proven, not assumed.  
Before integration, organizations should:
1. Request **security and compliance certifications** (ISO 27001, SOC 2, ISO 42001).  
2. Evaluate **AI-specific risks** — data lineage, model explainability, fairness.  
3. Require **SBOM/MBOM disclosures** ([[ai_sbom_and_mbom_management]]).  
4. Validate **PKI-based signing** for data, models, and APIs ([[model_release_and_signing]]).  
5. Assess **incident response maturity** and SLAs.  

**HU:**  
A beszállító megbízhatóságát **bizonyítani kell, nem feltételezni**.  
Integráció előtt a szervezetnek:  
1. Bizonyítania kell a **biztonsági és megfelelőségi tanúsítványokat** (ISO 27001, SOC 2, ISO 42001).  
2. Értékelnie kell az **MI-specifikus kockázatokat** — adatszármazás, magyarázhatóság, méltányosság.  
3. Követelnie kell az **SBOM/MBOM-leltárak** közzétételét ([[ai_sbom_and_mbom_management]]).  
4. Ellenőriznie kell az **PKI-alapú aláírásokat** az adatokra, modellekre és API-kra ([[model_release_and_signing]]).  
5. Fel kell mérnie az **incidenskezelési érettséget** és a szolgáltatási szintmegállapodásokat (SLA). 🧾  

---

## 🧩 Continuous Monitoring / Folyamatos megfigyelés

**EN:**  
Third-party risk does not end after onboarding.  
It must be **continuously monitored** through:
- Vulnerability feeds and threat intelligence updates.  
- Contract compliance audits.  
- AI supply chain attestation systems ([[ai_supply_chain_attestation_and_audit]]).  
- Model performance drift tracking using external components ([[model_integrity_monitoring]]).  

**HU:**  
A harmadik féltől származó kockázat nem ér véget a beszállító beléptetésével.  
**Folyamatosan figyelni kell** a következő módokon:  
- Sérülékenységi és fenyegetési hírcsatornák monitorozása.  
- Szerződéses megfelelőségi auditok végrehajtása.  
- MI-ellátási lánc hitelesítési rendszerek alkalmazása ([[ai_supply_chain_attestation_and_audit]]).  
- A modell teljesítménysodródásának figyelése a külső komponensek hatására ([[model_integrity_monitoring]]). 🔄  

---

## 🔐 Contractual and Governance Controls / Szerződéses és irányítási kontrollok

**EN:**  
Strong TPRM integrates legal and governance enforcement:
- Include **AI-specific SLAs** in supplier contracts (bias limits, retraining cadence).  
- Require **attestation evidence** for all externally sourced AI components.  
- Establish **termination clauses** for non-compliance or data integrity breaches.  
- Maintain a **Third-Party Risk Register** linked to the overall [[model_risk_management_and_registers]].  

**HU:**  
A hatékony TPRM jogi és irányítási érvényesítést is tartalmaz:  
- Tartalmazzon a szerződés **MI-specifikus SLA-kat** (torzítási határok, újratanítási gyakoriság).  
- Követelje meg **hitelesítési bizonyítékok** benyújtását minden külső MI-komponensre.  
- Rögzítsen **felmondási záradékokat** a megfelelés megsértése vagy adatintegritási incidens esetére.  
- Tartson fenn **Harmadik Felek Kockázati Nyilvántartást**, amely kapcsolódik az általános [[model_risk_management_and_registers]] rendszerhez. ⚖️  

---

## ⚖️ Regulatory and Ethical Context / Szabályozási és etikai kontextus

**EN:**  
Third-party accountability is embedded in multiple frameworks:  
- **EU AI Act (Art. 28–30):** suppliers must ensure traceability and conformity.  
- **ISO/IEC 42001:** requires vendor assessment and lifecycle control.  
- **NIST AI RMF:** “Manage” function — external party alignment.  
- **OECD AI Principles:** shared accountability and responsible sourcing.  

**HU:**  
A harmadik fél felelősségvállalása több szabványban is megjelenik:  
- **EU AI Act (28–30. cikk):** a beszállítóknak biztosítaniuk kell a visszakövethetőséget és a megfelelést.  
- **ISO/IEC 42001:** megköveteli a beszállítói értékelést és az életciklus-kontrollt.  
- **NIST AI RMF:** „Manage” funkció — külső felek összehangolása.  
- **OECD MI-elvek:** közös felelősség és etikus beszerzés. 🌍  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Future AI supply ecosystems will adopt **verifiable third-party credentials** — cryptographically signed supplier attestations proving compliance and ethical sourcing.  
AI agents may autonomously evaluate supplier reliability through real-time API risk scoring.  
Ultimately, supply chains will evolve into **self-auditing trust networks**.  

**HU:**  
A jövő MI-ellátási ökoszisztémái **hitelesített, kriptográfiailag aláírt beszállítói tanúsítványokat** fognak használni, amelyek bizonyítják a megfelelést és az etikus forrásokat.  
Az MI-ügynökök valós időben értékelhetik a beszállítók megbízhatóságát **API-alapú kockázati pontszámítás** segítségével.  
Végül az ellátási láncok **önellenőrző bizalmi hálózatokká** fejlődnek. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What are the main categories of third-party risk in AI systems?  
2. How can SBOM/MBOM management support supplier transparency?  
3. Why is PKI-based attestation critical for external model trust?  
4. What continuous monitoring practices reduce third-party exposure?  
5. How do contractual clauses enforce AI governance requirements?  
6. Which global frameworks mandate vendor accountability?  
7. How might AI-driven risk scoring transform future TPRM?  

---

> “Trust in AI is only as strong as the weakest supplier in its chain.”
