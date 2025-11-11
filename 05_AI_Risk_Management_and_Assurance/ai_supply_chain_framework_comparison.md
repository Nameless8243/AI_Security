---
title: AI Supply Chain Framework Comparison
phase: Governance
category: Supply Chain & Risk Frameworks
difficulty: Advanced
related: [ai_supply_chain_attestation_and_audit, ai_sbom_and_mbom_management, ai_model_provenance_and_lineage, compliance_mapping_nist_ai_rmf, regulatory_and_legal_compliance]
updated: 2025-11-10
---

# 🧭 AI Supply Chain Framework Comparison / MI-ellátási lánc keretrendszerek összehasonlítása

**EN:**  
AI supply chain security is not defined by a single framework — it’s a **mosaic of global standards**, each emphasizing a different aspect of trust.  
From technical attestation to legal governance, these frameworks together define *how organizations design, verify, and operate trustworthy AI systems*.  
Comparing them allows us to identify overlaps, integration points, and blind spots.  

**HU:**  
Az MI-ellátási lánc biztonságát nem egyetlen szabvány határozza meg — hanem egy **globális szabványhálózat**, amelyben minden keret más-más bizalmi aspektusra fókuszál.  
A technikai hitelesítéstől a jogi irányításig ezek a keretrendszerek együttesen határozzák meg, *hogyan tervezzenek, ellenőrizzenek és működtessenek a szervezetek megbízható MI-rendszereket*.  
Az összehasonlítás segít feltárni az átfedéseket, az integrációs pontokat és a hiányosságokat. 🌍  

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
AI supply chain frameworks address four trust domains:  
1. **Provenance and traceability** — how models, data, and code are documented and verified.  
2. **Integrity and attestation** — how authenticity is cryptographically proven.  
3. **Governance and compliance** — how accountability is structured and enforced.  
4. **Operational assurance** — how monitoring, audits, and transparency are maintained.  

**HU:**  
Az MI-ellátási lánc keretrendszerei négy bizalmi dimenziót fednek le:  
1. **Származás és visszakövethetőség** — hogyan dokumentáljuk és ellenőrizzük a modelleket, adatokat és kódokat.  
2. **Integritás és hitelesítés** — hogyan bizonyítható a hitelesség kriptográfiailag.  
3. **Irányítás és megfelelés** — hogyan épül fel és érvényesül az elszámoltathatóság.  
4. **Működési garancia** — hogyan biztosítható a megfigyelés, auditálás és átláthatóság. ⚙️  

---

## 💡 Core Idea / Alapgondolat

**EN:**  
No single framework covers the entire AI supply chain lifecycle.  
Security architects must **combine and align** them — using NIST for structure, ISO for governance, MITRE ATLAS for threat intelligence, and the EU AI Act for legal compliance.  
The goal is *not conformity to one model*, but **interoperability across many**.  

**HU:**  
Egyetlen keretrendszer sem fedi le az MI-ellátási lánc teljes életciklusát.  
A biztonsági architekteknek **kombinálniuk és összehangolniuk** kell őket — a NIST-et a szerkezeti, az ISO-t az irányítási, a MITRE ATLAS-t a fenyegetési, az EU AI Act-et pedig a jogi oldalról.  
A cél nem az, hogy egy modellt kövessünk, hanem az, hogy **sok között biztosítsuk az interoperabilitást**. 🧩  

---

## 🧱 1. NIST AI RMF — U.S. Risk Management Standard

**EN:**  
- **Focus:** Risk management, lifecycle governance, and explainable AI.  
- **Structure:** Govern → Map → Measure → Manage.  
- **Strength:** Flexible integration with cybersecurity (NIST SP 800-53, CSF).  
- **Limitation:** Non-binding; requires adaptation to sector or law.  

**HU:**  
- **Fókusz:** Kockázatkezelés, életciklus-irányítás és magyarázható MI.  
- **Struktúra:** Govern → Map → Measure → Manage.  
- **Erősség:** Rugalmasan integrálható a kiberbiztonsági szabványokkal (NIST SP 800-53, CSF).  
- **Korlát:** Nem kötelező érvényű; szektorspecifikus alkalmazás szükséges. 🇺🇸  

---

## 🧾 2. ISO/IEC 42001 — AI Management System (AIMS)

**EN:**  
- **Focus:** Organizational governance and ethical AI lifecycle management.  
- **Structure:** Based on ISO 27001 model (Plan–Do–Check–Act).  
- **Strength:** Certifiable standard for AI governance maturity.  
- **Limitation:** Broad and policy-driven — lacks technical attestation depth.  

**HU:**  
- **Fókusz:** Szervezeti irányítás és etikus MI-életciklus menedzsment.  
- **Struktúra:** ISO 27001 mintájára (Plan–Do–Check–Act).  
- **Erősség:** Tanúsítható szabvány, amely méri az MI-irányítás érettségét.  
- **Korlát:** Túl általános; a technikai hitelesítés szintjén hiányos. 🌐  

---

## 🔒 3. EU AI Act — Regulatory and Legal Mandate

**EN:**  
- **Focus:** Legal obligations, human oversight, and risk classification.  
- **Structure:** Risk-based tiers (Unacceptable → High → Limited → Minimal).  
- **Strength:** First comprehensive AI law enforcing transparency and documentation.  
- **Limitation:** Requires operational translation into controls and evidence.  

**HU:**  
- **Fókusz:** Jogi kötelezettségek, emberi felügyelet és kockázati besorolás.  
- **Struktúra:** Kockázati szintek (Elfogadhatatlan → Magas → Korlátozott → Minimális).  
- **Erősség:** Az első átfogó MI-törvény, amely kikényszeríti az átláthatóságot és dokumentálást.  
- **Korlát:** Operatív szintű lefordítást igényel konkrét kontrollokra és bizonyítékokra. 🇪🇺  

---

## 🧠 4. MITRE ATLAS — Adversarial Threat Knowledge Base

**EN:**  
- **Focus:** Mapping adversarial attacks and defensive techniques in AI.  
- **Structure:** Modeled after MITRE ATT&CK, covering data, model, and inference stages.  
- **Strength:** Provides real-world attacker tactics for defensive design.  
- **Limitation:** Technical and tactical — lacks governance or compliance structure.  

**HU:**  
- **Fókusz:** Adverszáriális támadások és védelmi módszerek feltérképezése MI-környezetben.  
- **Struktúra:** A MITRE ATT&CK mintájára, az adat-, modell- és inferencia-fázisokat lefedve.  
- **Erősség:** Valós támadói taktikákat dokumentál, így védekezési tervezésre kiváló.  
- **Korlát:** Technikai és taktikai fókuszú — hiányzik belőle a megfelelőségi-irányítási dimenzió. ⚔️  

---

## 🧩 5. OWASP ML Top 10 — Machine Learning Vulnerabilities

**EN:**  
- **Focus:** Common vulnerabilities and exposures in ML pipelines.  
- **Structure:** Top 10 ranked by impact and exploitability.  
- **Strength:** Developer-friendly; simplifies vulnerability awareness.  
- **Limitation:** Not a governance framework; requires integration with NIST or ISO for compliance.  

**HU:**  
- **Fókusz:** A leggyakoribb gépi tanulási sebezhetőségek és fenyegetések.  
- **Struktúra:** Top 10 lista hatás és kihasználhatóság alapján.  
- **Erősség:** Fejlesztőbarát; segít a sebezhetőségi tudatosságban.  
- **Korlát:** Nem irányítási keret; a megfelelőséghez NIST- vagy ISO-integráció szükséges. 🧮  

---

## ⚙️ Comparative Integration / Összehangolt alkalmazás

**EN:**  
Each framework covers a unique trust dimension — combining them creates full lifecycle assurance:  
- **NIST AI RMF** → defines *structure* for managing risk.  
- **ISO 42001** → defines *governance maturity* and policy systems.  
- **MITRE ATLAS / OWASP ML** → define *threat and vulnerability awareness*.  
- **EU AI Act** → defines *legal enforceability and accountability*.  

Together they form a **hybrid AI trust architecture**:  
$$
NIST_{structure} + ISO_{governance} + MITRE_{threats} + EU_{compliance} = Trusted\ AI
$$  

**HU:**  
Minden keretrendszer egyedi bizalmi dimenziót fed le — együtt teljes életciklus-garanciát biztosítanak:  
- **NIST AI RMF** → a *kockázatkezelési szerkezetet* adja.  
- **ISO 42001** → az *irányítási érettséget* és a szabályzati rendszert határozza meg.  
- **MITRE ATLAS / OWASP ML** → a *fenyegetési tudatosságot* biztosítja.  
- **EU AI Act** → a *jogi megfelelőséget és elszámoltathatóságot* rögzíti.  

Együtt egy **hibrid MI-bizalmi architektúrát** alkotnak:  
$$
NIST_{szerkezet} + ISO_{irányítás} + MITRE_{fenyegetések} + EU_{megfelelés} = Megbízható\ MI
$$ 🧠  

---

## ⚖️ Alignment and Interoperability / Összhang és interoperabilitás

**EN:**  
To unify frameworks effectively:
1. **Map overlapping controls** (e.g., NIST “Govern” ↔ ISO “Plan” ↔ EU “High-Risk” Tier).  
2. **Use SBOM/MBOM evidence** ([[ai_sbom_and_mbom_management]]) to cross-verify compliance.  
3. **Harmonize auditing** using [[ai_supply_chain_attestation_and_audit]].  
4. **Implement continuous validation loops** ([[continuous_validation_and_review]]) to ensure frameworks remain aligned over time.  

**HU:**  
A keretrendszerek hatékony egyesítéséhez:  
1. **Térképezd fel az átfedő kontrollokat** (pl. NIST „Govern” ↔ ISO „Plan” ↔ EU „High-Risk”).  
2. **Használd az SBOM/MBOM-bizonyítékokat** ([[ai_sbom_and_mbom_management]]) a megfelelőség ellenőrzésére.  
3. **Egységesítsd az auditálást** a [[ai_supply_chain_attestation_and_audit]] segítségével.  
4. **Vezess be folyamatos érvényesítési hurkokat** ([[continuous_validation_and_review]]), hogy a keretek idővel is összehangban maradjanak. 🔄  

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Future frameworks will converge toward **machine-readable governance**, allowing automated mapping between legal, ethical, and technical standards.  
AI-driven compliance engines will interpret frameworks dynamically and self-audit their adherence — transforming compliance from paperwork into *autonomous trust orchestration*.  

**HU:**  
A jövő keretrendszerei **géppel olvasható irányítási modellek** felé konvergálnak, lehetővé téve a jogi, etikai és technikai szabványok közötti automatikus leképezést.  
Az MI-alapú megfelelőségi motorok dinamikusan értelmezik majd a kereteket és **önellenőrző módon auditálják** a betartásukat — így a megfelelés **papíralapú adminisztrációból autonóm bizalmi koordinációvá** válik. 🤖  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What are the main global frameworks governing AI supply chain security?  
2. How does NIST AI RMF differ from ISO 42001 in purpose and scope?  
3. Why is MITRE ATLAS considered complementary rather than regulatory?  
4. How can SBOM/MBOM artifacts support multi-framework compliance?  
5. What synergies exist between EU AI Act and NIST AI RMF?  
6. How can organizations maintain framework interoperability over time?  
7. What might “machine-readable governance” look like in the future?  

---

> “No single framework builds trust — it’s the harmony between them that creates accountability.”
