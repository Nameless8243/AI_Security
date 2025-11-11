---
id: fairness
title: "Fairness / Méltányosság"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "01_Glossary"
agent: "Core Concepts Engineer"
tags:
  - ai_security
  - glossary
  - underscore_slug
---
# ⚖️ AI Fairness & Bias Mitigation

---

## 🌍 Concept Overview

**EN:**  
Fairness in Artificial Intelligence means ensuring that models make decisions without systematically favoring or disadvantaging particular groups. It is a cornerstone of **trustworthy AI**, forming one of the key pillars in frameworks such as the [[nist_ai_rmf|NIST AI Risk Management Framework]] and the [[eu_ai_act|EU AI Act]]. Fairness goes beyond accuracy—it’s about aligning AI behavior with societal values, ethics, and equal opportunity.  

**HU:**  
A mesterséges intelligenciában a „fairness” (méltányosság) azt jelenti, hogy a modellek döntései nem kedveznek vagy hátrányosítanak rendszerszinten bizonyos csoportokat. Ez az **etikus és megbízható MI** egyik alapköve, amelyet többek között a [[nist_ai_rmf|NIST AI Kockázatkezelési Keretrendszer]] és az [[eu_ai_act|EU MI Rendelet]] is kiemel. A fairness nem azonos a pontossággal – inkább arról szól, hogy a mesterséges intelligencia viselkedése összhangban legyen a társadalmi értékekkel és az esélyegyenlőséggel.

---

## 💡 Why Fairness Matters

**EN:**  
Bias in datasets or models can lead to discriminatory outcomes — for example, unfair credit scoring, biased hiring, or unequal healthcare recommendations. These are not just ethical failures but also security and compliance risks. An unfair model can be *attacked*, *manipulated*, or *exploited* through **bias amplification**, creating reputational, legal, and systemic vulnerabilities.  

**HU:**  
Az adat- vagy modelltorzítás diszkriminatív eredményekhez vezethet – például igazságtalan hitelbírálathoz, torzított munkaerő-felvételhez vagy egyenlőtlen egészségügyi javaslatokhoz. Ezek nem csupán etikai problémák, hanem **biztonsági és megfelelőségi kockázatok** is. Egy nem fair modell **támadható**, **manipulálható** vagy **kihasználható** a torzítás felerősítése révén, ami hírnévromláshoz, jogi következményekhez és rendszerszintű sebezhetőségekhez vezethet.

---

## 🧩 Types of Fairness

**EN:**  
Different fairness definitions exist, depending on what kind of “equality” we aim for. The three most common categories are:

1. **Individual Fairness** — similar individuals should be treated similarly.  
2. **Group Fairness** — outcomes should not differ significantly between protected groups (e.g., gender, ethnicity).  
3. **Counterfactual Fairness** — a model’s decision should remain the same if an individual’s sensitive attribute (like gender) were hypothetically changed.

Formally, one common metric for group fairness is **Statistical Parity Difference** (SPD):

$$
SPD = P(\hat{Y}=1 | A=0) - P(\hat{Y}=1 | A=1)
$$

Where:
- \( \hat{Y}=1 \) represents a positive model decision (e.g., loan approved),
- \( A \) is a binary sensitive attribute (e.g., 0 = male, 1 = female).

A model is considered *statistically fair* when \( |SPD| \) is close to zero.

**HU:**  
A fairness többféleképpen definiálható, attól függően, hogy milyen „egyenlőséget” szeretnénk elérni:

1. **Egyéni fairness** — hasonló személyeket hasonlóan kell kezelni.  
2. **Csoportos fairness** — az eredmények nem térhetnek el lényegesen a védett csoportok (pl. nem, etnikum) között.  
3. **Kontrafaktuális fairness** — a modell döntése maradjon változatlan, ha egy érzékeny attribútumot (pl. nemet) hipotetikusan megváltoztatunk.

A csoportos fairness egyik tipikus mérőszáma a **statisztikai paritáskülönbség (SPD)**:

$$
SPD = P(\hat{Y}=1 | A=0) - P(\hat{Y}=1 | A=1)
$$

Ahol  
- \( \hat{Y}=1 \) egy pozitív döntést jelöl (pl. hitel jóváhagyva),  
- \( A \) egy bináris érzékeny attribútum (pl. 0 = férfi, 1 = nő).  

A modell *statisztikailag fair*, ha \( |SPD| \) értéke közel nulla.

---

## 🧠 Sources of Bias

**EN:**  
Bias can enter the AI pipeline at multiple stages:  
- **Data Collection Bias:** The data does not represent all populations equally.  
- **Label Bias:** Human annotators encode subjective or cultural biases.  
- **Algorithmic Bias:** Learning algorithms amplify existing disparities.  
- **Deployment Bias:** The model is used in contexts for which it was not trained.

**HU:**  
A torzítás több ponton is bekerülhet az MI-pipeline-ba:  
- **Adatgyűjtési torzítás:** Az adathalmaz nem reprezentál minden csoportot egyenlően.  
- **Címkézési torzítás:** Az emberi címkézők szubjektív vagy kulturális elfogultságokat visznek be.  
- **Algoritmikus torzítás:** A tanulási algoritmus felerősíti a meglévő egyenlőtlenségeket.  
- **Bevezetési torzítás:** A modellt olyan környezetben használják, amire eredetileg nem képezték.

---

## 🛡️ Bias Mitigation Strategies

**EN:**  
To achieve fairness, we use techniques at different stages of the [[ai_pipeline|AI pipeline]]:

### 1. Pre-processing  
- Balance or resample datasets (e.g., reweighting, [[data_augmentation|Data Augmentation]])  
- Remove or obfuscate sensitive attributes  
- Use fair representations via adversarial debiasing

### 2. In-processing  
- Add fairness constraints to the loss function  
- Use adversarial learning where a secondary model tries to detect bias  
- Apply regularization terms promoting equal treatment

### 3. Post-processing  
- Calibrate model outputs across demographic groups  
- Modify decision thresholds to reduce disparities

**HU:**  
A fairness különböző pipeline-szakaszokban érhető el:

### 1. Pre-processing  
- Az adathalmaz kiegyensúlyozása (pl. újrasúlyozás, [[data_augmentation|adatbővítés]])  
- Érzékeny attribútumok eltávolítása vagy elfedése  
- „Fair” reprezentációk létrehozása adverszáriális tanulással  

### 2. In-processing  
- Fairness-korlátok beépítése a veszteségfüggvénybe  
- Másodlagos modell alkalmazása, amely megpróbálja felismerni a torzítást  
- Regularizáció, amely az egyenlő bánásmódot ösztönzi  

### 3. Post-processing  
- A modellkimenetek kalibrálása demográfiai csoportok között  
- Küszöbértékek módosítása az egyenlőbb eredmények érdekében  

---

## ⚙️ Metrics and Evaluation

**EN:**  
Fairness metrics must be interpreted carefully, as they can conflict. For instance, achieving equal false positive rates may reduce overall accuracy. A common evaluation approach is **Pareto optimization**, balancing fairness and performance:

$$
\text{Optimize: } \max (Accuracy, -|SPD|, -|EO|)
$$

where \( EO \) represents **Equalized Odds** — the difference in error rates between groups.

**HU:**  
A fairness-mutatókat körültekintően kell értékelni, mert gyakran ellentmondanak egymásnak. Például az egyenlő hamis pozitív arány elérése ronthatja az általános pontosságot. Gyakori megközelítés a **Pareto-optimalizálás**, amely a fairness és a teljesítmény közötti egyensúlyt keresi:

$$
\text{Optimalizálás: } \max (Pontosság, -|SPD|, -|EO|)
$$

ahol \( EO \) az **Equalized Odds** (kiegyenlített hibaarányok) mutatója.

---

## 🧭 Practical Considerations

**EN:**  
In practice, fairness requires continuous monitoring. Models deployed in dynamic environments (like financial or hiring systems) may drift and reintroduce bias over time. Integration with [[model_drift|Model Drift Detection]], [[consistency_audit|Consistency Auditing]], and [[ai_governance|AI Governance]] frameworks ensures sustained fairness.  

**HU:**  
A gyakorlatban a fairness folyamatos felügyeletet igényel. A dinamikus környezetben működő modellek (például pénzügyi vagy toborzási rendszerek) idővel újra torzulhatnak. A [[model_drift|modell-drift felismerésével]], a [[consistency_audit|konzisztencia-auditálással]] és az [[ai_governance|MI-irányítási]] keretrendszerekkel való integráció biztosítja a hosszú távú méltányosságot.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. How does fairness differ from accuracy in AI systems?  
2. What are the main types of fairness, and when should each be applied?  
3. How can bias emerge at different stages of the AI pipeline?  
4. What are the trade-offs between fairness and model performance?  
5. How can fairness monitoring be automated in production systems?

---

> “Fairness is not a static property of an algorithm — it’s a continuous dialogue between data, design, and humanity.” 💭
