---
version: "3.2"
section_type: "safety"
agent: "Learning Mentor"
---
---
title: Fairness and Bias Mitigation / Igazságosság és torzítás csökkentése
phase: Foundation
category: AI Governance & Ethics
difficulty: Advanced
related: [ethical_ai_policy, explainability_and_transparency, ai_fairness_and_transparency_governance, data_provenance_and_integrity, ai_accountability_and_responsibility]
updated: 2025-11-11
---

## ⚖️ Fairness and Bias Mitigation / Igazságosság és torzítás csökkentése

**EN:**  
Fairness is the ethical and mathematical pursuit of equality in AI outcomes. It ensures that automated systems treat individuals and groups without unjustified bias, while bias mitigation provides the technical mechanisms to achieve that fairness.  

**HU:**  
Az igazságosság az AI-ban az egyenlőség etikai és matematikai megvalósítása. Célja, hogy az automatizált rendszerek az embereket és csoportokat ne kezeljék indokolatlan torzítással. A torzítás-csökkentés pedig ennek a technikai megvalósítását jelenti.

---

## 💡 Concept Overview / Fogalmi áttekintés

**EN:**  
Fairness means more than removing prejudice — it requires quantifying and managing *how* bias appears in data, models, or human feedback. [[ai_fairness_and_transparency_governance]] extends this principle into governance and continuous auditing.  

**HU:**  
Az igazságosság nem csak az előítéletek eltávolítását jelenti — fel kell tárni és kezelni kell, *hogyan* jelenik meg a torzítás az adatokban, a modellekben vagy az emberi visszajelzésekben. Az [[ai_fairness_and_transparency_governance]] ezt a szemléletet a kormányzás és a folyamatos auditálás szintjére emeli.

---

## 🧩 Core Idea / Alapgondolat

**EN:**  
AI fairness bridges ethics and mathematics. Each decision boundary or probabilistic output can amplify existing societal imbalances unless constraints are introduced. Bias mitigation therefore combines **data ethics**, **statistical control**, and **policy enforcement**.  

**HU:**  
Az AI-igazságosság az etika és a matematika határterülete. Minden döntési határ vagy valószínűségi kimenet felerősítheti a meglévő társadalmi egyenlőtlenségeket, ha nem vezetünk be korrekciós korlátokat. A torzítás-csökkentés ezért az **adatetika**, a **statisztikai kontroll** és a **szabályozási megfelelés** kombinációja.

---

## 📊 Types of Bias / A torzítás típusai

**EN:**  
Bias can enter at multiple stages of the AI lifecycle:  

- **Data bias:** sampling errors, representation gaps.  
- **Label bias:** subjective annotation or labeling inconsistency.  
- **Model bias:** algorithmic preferences or regularization imbalance.  
- **Societal bias:** historical discrimination reflected in input data.  

**HU:**  
A torzítás az AI-életciklus számos pontján megjelenhet:  

- **Adattorzítás:** mintavételi hibák, reprezentációs hiányok.  
- **Címketorzítás:** szubjektív címkézés vagy inkonzisztencia.  
- **Modelltorzítás:** algoritmikus preferenciák, hibás súlyozás.  
- **Társadalmi torzítás:** a történelmi diszkrimináció lenyomata az adatokban.

---

## 🧮 Mathematical Framing / Matematikai megközelítés

**EN:**  
Fairness can be formalized through several mathematical criteria, depending on context. The simplest binary classification fairness test compares predicted positive rates across groups:

$$
Δ = |P(ŷ = 1 | A = group₁) − P(ŷ = 1 | A = group₂)|
$$

If Δ exceeds a policy-defined threshold τ, bias mitigation is required.  

**HU:**  
Az igazságosság többféle matematikai módon is mérhető, a kontextustól függően. A legegyszerűbb bináris osztályozási teszt a pozitív kimenetek arányát hasonlítja össze a csoportok között:

$$
Δ = |P(ŷ = 1 | A = group₁) − P(ŷ = 1 | A = group₂)|
$$

Ha a Δ érték meghaladja a politikában rögzített küszöböt (**τ**), torzítás-csökkentés szükséges.

---

## 🛠️ Bias Mitigation Strategies / Torzítás-csökkentési stratégiák

**EN:**  
There are three primary mitigation levels:  

1. **Pre-processing:** rebalance or anonymize data before training.  
2. **In-processing:** adjust learning objectives (e.g., fairness constraints).  
3. **Post-processing:** calibrate model outputs to equalize group outcomes.  

**HU:**  
A torzítás-csökkentés három fő szinten történhet:  

1. **Előfeldolgozás:** az adatok kiegyensúlyozása vagy anonimizálása tréning előtt.  
2. **Tanulási folyamat közben:** az objektív függvény módosítása (pl. fairness-korlátok).  
3. **Utófeldolgozás:** a kimenetek kalibrálása a csoportok közti arány kiegyenlítésére.

---

## 🔐 Trade-offs and Constraints / Korlátok és kompromisszumok

**EN:**  
Perfect fairness is mathematically unattainable. Improving equality often reduces accuracy or privacy. The optimal balance depends on the AI’s purpose, data sensitivity, and ethical threshold defined in [[ethical_ai_policy]].  

**HU:**  
A tökéletes igazságosság matematikailag elérhetetlen. Az egyenlőség növelése gyakran csökkenti a pontosságot vagy a magánszféra védelmét. Az optimális egyensúly az AI céljától, az adatok érzékenységétől és az [[ethical_ai_policy]] által meghatározott etikai küszöbtől függ.

---

## 🧾 Governance and Accountability / Irányítás és felelősség

**EN:**  
Governance frameworks must document fairness testing results and mitigation actions. [[ai_accountability_and_responsibility]] ensures traceability of decisions, while [[data_provenance_and_integrity]] verifies data origin integrity — crucial for fair outcomes.  

**HU:**  
Az irányítási kereteknek dokumentálniuk kell az igazságossági tesztek eredményeit és a korrekciós lépéseket. Az [[ai_accountability_and_responsibility]] biztosítja a döntések nyomonkövethetőségét, míg a [[data_provenance_and_integrity]] az adatok származási hitelességét — ami elengedhetetlen a tisztességes eredményekhez.

---

## 🧠 Fairness in Model Design / Igazságosság a modelltervezésben

**EN:**  
Architectural fairness can be enforced through **constraint regularization** or **adversarial debiasing** — training a secondary network to detect and remove bias signals in embeddings. These methods make fairness a structural property rather than a cosmetic fix.  

**HU:**  
Az architekturális igazságosság megvalósítható **korlátozási regularizációval** vagy **adverzáriális torzítás-eltávolítással** — egy másodlagos hálózat betanításával, amely felismeri és eltávolítja a torzító jeleket az embedding-térből. Így az igazságosság nem utólagos javítás, hanem a modell szerkezeti tulajdonsága lesz.

---

## ⚖️ Legal and Ethical Frameworks / Jogi és etikai keretrendszerek

**EN:**  
Laws like the EU AI Act and frameworks such as OECD AI Principles explicitly classify bias mitigation as a compliance requirement. Ethical alignment thus becomes measurable through fairness metrics, directly influencing audit results and public trust.  

**HU:**  
Az olyan jogszabályok, mint az EU AI Act, valamint az OECD AI Principles, kifejezetten előírják a torzítás-csökkentést mint megfelelőségi követelményt. Az etikai összhang így mérhetővé válik a fairness-mutatókon keresztül, közvetlenül befolyásolva az audit-eredményeket és a társadalmi bizalmat.

---

## 🚀 Future Directions / Jövőbeli irányok

**EN:**  
Emerging methods aim for **causal fairness** — identifying not only correlations but causal pathways that produce inequality. Integration with [[ai_risk_assessment_methodology]] and graph-based interpretability models may soon allow dynamic, context-aware fairness adjustment during runtime.  

**HU:**  
Az új kutatások célja a **kauzális igazságosság**, amely nemcsak az összefüggéseket, hanem az egyenlőtlenséget okozó oksági útvonalakat is feltárja. Az [[ai_risk_assessment_methodology]] és a gráfalapú értelmezhetőségi modellek integrációja lehetővé teheti a dinamikus, kontextusérzékeny fairness-korrekciót futásidőben.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What are the main sources of bias in AI systems?  
2. How can fairness be represented mathematically between groups?  
3. What are the three main stages of bias mitigation?  
4. Why is perfect fairness impossible to achieve?  
5. How does governance ensure fairness accountability?  
6. What is adversarial debiasing and how does it work?  
7. How do legal frameworks enforce fairness obligations?  
8. What new trends emerge toward causal fairness?

> “Fairness is not equality of outcome — it is equality of opportunity.  
> In AI, justice begins where bias ends.”

