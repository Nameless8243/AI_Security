---
id: model_drift
title: "Model Drift / Modell-eltolódás"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "01_Glossary"
agent: "Lifecycle Analyst"
tags:
  - ai_security
  - glossary
  - underscore_slug
---
🚨 COPY START 🚨
# Model Drift  
*When yesterday’s model no longer understands today’s world*  

---

## 🌍 Concept Overview  

**EN:**  
**Model Drift** (also called **Concept Drift**) refers to the **degradation of a model’s performance** over time because the **underlying data distribution changes**. 🌍  
In simple terms: the world evolves, but the model stays frozen in time.  
Drift can occur due to new user behavior, external events, or even malicious interference (such as **[[data_poisoning|Data Poisoning]]**).  

**HU:**  
A **Model Drift** (vagy más néven **Concept Drift**) azt jelenti, hogy a modell **pontossága idővel romlik**, mert a **valóság megváltozik**, de a modell nem alkalmazkodik hozzá. 🔄  
Egyszerűen fogalmazva: a világ változik, de a modell ugyanaz marad.  
A drift oka lehet a felhasználói viselkedés módosulása, külső események hatása, vagy akár **rosszindulatú adatmanipuláció** is (például **[[data_poisoning|Data Poisoning]]**).  

---

## 💡 Types of Drift  

**EN:**  
Model drift is not a single phenomenon — it appears in multiple forms:  

- **Data Drift (Covariate Shift):** the input distribution \( P(X) \) changes, but the relationship \( P(Y|X) \) stays constant.  
- **Concept Drift:** the conditional distribution \( P(Y|X) \) itself changes — the model’s learned mapping becomes outdated.  
- **Label Drift:** the meaning or labeling of outputs evolves, especially in human-annotated data.  

Mathematically, drift occurs when the training and deployment distributions diverge:  

$$
P_{\text{train}}(X, Y) \neq P_{\text{deploy}}(X, Y)
$$  

**HU:**  
A modelldrift többféle formában jelentkezhet:  

- **Adat-drift (Covariate Shift):** a bemenetek eloszlása \( P(X) \) változik, de a kapcsolat \( P(Y|X) \) nem.  
- **Koncepció-drift:** maga a feltételes eloszlás \( P(Y|X) \) módosul — a modell leképezése elavul.  
- **Címke-drift:** a címkék jelentése vagy emberi értelmezése idővel megváltozik.  

Matematikailag drift akkor következik be, ha a tanítás és az éles működés során tapasztalt eloszlások eltérnek:  

$$
P_{\text{train}}(X, Y) \neq P_{\text{deploy}}(X, Y)
$$  

---

## ⚙️ Causes of Drift  

**EN:**  
1. **Environmental Change:** new market conditions, pandemics, regulation changes, or seasonality.  
2. **User Behavior:** shifts in customer intent, language usage, or device patterns.  
3. **Data Pipeline Issues:** broken sensors, biased samples, or incomplete ingestion.  
4. **Adversarial Manipulation:** stealthy input corruption or poisoning designed to slowly degrade model performance (**[[adversarial_example_attacks|Adversarial Example Attacks]]**).  

**HU:**  
1. **Környezeti változás:** új piaci helyzet, járvány, szabályozás vagy szezonalitás.  
2. **Felhasználói viselkedés:** a keresési szándék, nyelvhasználat vagy eszközök mintázatának változása.  
3. **Adatfolyam hibák:** hibás szenzorok, torz mintavétel vagy hiányos adatbeolvasás.  
4. **Adverszáriális manipuláció:** lassú, rejtett bemenet-mérgezés, ami fokozatosan rontja a modell teljesítményét (**[[adversarial_example_attacks|Adversarial Example Attacks]]**).  

---

## 🧠 Detection and Metrics  

**EN:**  
Detecting drift requires **continuous monitoring** and statistical comparison between new and historical data.  
Common techniques include:  

- **Population Stability Index (PSI):** measures distributional change in features.  
- **Kullback–Leibler (KL) Divergence:** quantifies how much one probability distribution diverges from another.  

$$
D_{\mathrm{KL}}(P || Q) = \sum_i P(i) \log \frac{P(i)}{Q(i)}
$$  

A high KL divergence indicates that the model is seeing data that differs significantly from its training distribution — an early warning sign for retraining.  

**HU:**  
A drift észleléséhez **folyamatos megfigyelés** és a régi–új adatok **statisztikai összevetése** szükséges.  
Gyakori módszerek:  

- **Population Stability Index (PSI):** a jellemzők eloszlásváltozását méri.  
- **Kullback–Leibler (KL) Divergencia:** számszerűsíti, mennyire tér el két valószínűségi eloszlás egymástól.  

$$
D_{\mathrm{KL}}(P || Q) = \sum_i P(i) \log \frac{P(i)}{Q(i)}
$$  

A magas KL-érték arra utal, hogy a modell olyan adatokkal találkozik, amelyek jelentősen eltérnek a tanítóhalmaztól — ez **újratanítási jelzés** lehet.  

---

## 🛡️ Mitigation Strategies  

**EN:**  
- **[[observability_and_monitoring|Observability and Monitoring]]:** track drift metrics in real time.  
- **Retraining Pipelines:** automate retraining when drift exceeds thresholds.  
- **[[input_restoration|Input Restoration]]:** cleanse or normalize incoming data streams.  
- **[[drift_detection_and_feedback_loops|Feedback Loops]]:** trigger human or automated retraining based on alerts.  
- **Ensemble or Continual Learning:** allow the system to adapt gradually without full retraining.  

**HU:**  
- **[[observability_and_monitoring|Megfigyelés és monitoring]]:** a drift-mutatók folyamatos követése valós időben.  
- **Újratanítási folyamatok:** automatikus retrain, ha a drift meghaladja a küszöböt.  
- **[[input_restoration|Input Restoration]]:** a bemeneti adatok tisztítása és normalizálása.  
- **[[drift_detection_and_feedback_loops|Visszacsatolási hurkok]]:** automatikus vagy emberi beavatkozás újratanításhoz.  
- **Ensemble vagy folyamatos tanulás:** a modell fokozatosan alkalmazkodik, nem kell teljesen újratanítani.  

---

## 🤖 Security Implications  

**EN:**  
Model drift can **mask adversarial attacks** or **create silent failures**.  
A poisoned dataset that slowly shifts the model’s behavior may look like “natural” drift — this is called **malicious drift camouflage**. 🕶️  
Hence, **[[ai_security_metrics_and_kpis|AI Security Metrics]]** must differentiate between *natural drift* and *malicious drift*.  

**HU:**  
A modelldrift **elfedheti az adverszáriális támadásokat** vagy **csendes hibákat** okozhat.  
Ha egy mérgezett adathalmaz fokozatosan változtatja meg a modell viselkedését, az „természetes” driftnek tűnhet — ezt hívjuk **rosszindulatú drift álcázásnak**. ⚠️  
Ezért az **[[ai_security_metrics_and_kpis|AI Security Metrics]]** rendszernek meg kell különböztetnie a *természetes* és a *rosszindulatú* driftet.  

---

## 🧩 Related Vault Topics  

- [[observability_and_monitoring|Observability and Monitoring]]  
- [[drift_detection_and_feedback_loops|Drift Detection and Feedback Loops]]  
- [[input_restoration|Input Restoration]]  
- [[data_poisoning|Data Poisoning]]  
- [[ai_security_metrics_and_kpis|AI Security Metrics and KPIs]]  
- [[continuous_improvement_and_reporting|Continuous Improvement and Reporting]]  

---

## 🧭 Review Questions / Ellenőrző kérdések  

1. **EN:** What is the difference between data drift and concept drift?  
   **HU:** Mi a különbség az adat-drift és a koncepció-drift között?  

2. **EN:** How can KL divergence be used to detect model drift statistically?  
   **HU:** Hogyan használható a KL-divergencia a drift statisztikai kimutatására?  

3. **EN:** What security risks arise when drift hides adversarial manipulation?  
   **HU:** Milyen biztonsági kockázatot jelent, ha a drift elfedi az adverszáriális manipulációt?  

4. **EN:** How does Input Restoration help mitigate model drift?  
   **HU:** Hogyan segíti az Input Restoration a modelldrift enyhítését?  

5. **EN:** Why should natural and malicious drift be treated separately in monitoring systems?  
   **HU:** Miért kell külön kezelni a természetes és a rosszindulatú driftet a monitorozásban?  

---

> “AI models age not with time, but with change.” ⏳  

🚨 COPY END 🚨
