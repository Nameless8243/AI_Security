---
version: "3.2"
section_type: "detection"
agent: "Learning Mentor"
---
# 🌊 Drift and Anomaly Detection / Drift- és anomália-detektálás

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
Drift and anomaly detection are essential to preserve **trust, accuracy, and resilience** in deployed AI systems. Over time, the environment, data sources, and user behavior evolve — meaning the model’s original assumptions slowly become invalid. This phenomenon is known as **model drift**, and if left unchecked, it can silently corrupt predictions and introduce hidden vulnerabilities.  

**HU:**  
A drift- és anomália-detektálás alapvető szerepet játszik a **megbízhatóság, pontosság és robusztusság** fenntartásában. Az idő múlásával a környezet, az adatforrások és a felhasználói viselkedés is változik — így a modell eredeti feltételezései fokozatosan érvényüket vesztik. Ezt a jelenséget nevezzük **modell-driftnek**, és ha nem figyeljük, csendben torzíthatja az előrejelzéseket, biztonsági réseket okozva.

---

## 💡 Core Idea / Alapelv

**EN:**  
Every model is trained under a specific statistical view of the world. When the real data distribution \(P_{real}(x)\) starts to deviate from the training distribution \(P_{train}(x)\), we experience drift. The earlier we detect this, the less risk we face — whether it’s financial mispredictions or adversarial model manipulation.  

**HU:**  
Minden modell egy adott statisztikai világképre épül. Amikor a valós adateloszlás \(P_{real}(x)\) eltér a tanító eloszlástól \(P_{train}(x)\), drift jelenség lép fel. Minél korábban észleljük ezt, annál kisebb a kockázat — legyen szó pénzügyi tévedésekről vagy adverszáriális manipulációról.

---

## 🧮 Mathematical View / Matematikai szemlélet

**EN:**  
We quantify drift by measuring the statistical distance between the training and current input distributions:
$$
D_drift = d(P_train(x), P_real(x))
$$
If this distance exceeds a threshold τ, the system flags a potential concept drift:
$$
D_drift > τ ⇒ alert("drift")
$$
Typical distance measures include KL-divergence, Jensen–Shannon distance, and the Population Stability Index (PSI).

**HU:**  
A drift mértéke a tanító és az aktuális adateloszlás közötti statisztikai távolság:
$$
D_drift = d(P_train(x), P_real(x))
$$
Ha ez a távolság meghaladja a küszöböt τ, a rendszer koncepciódriftet jelez:
$$
D_drift > τ ⇒ alert("drift")
$$
A leggyakoribb távolságmérők: KL-divergencia, Jensen–Shannon-távolság és a populációstabilitási index (PSI).

---

## 🧩 Types of Drift / Drift típusai

**EN:**  
- **Data drift:** Input features change in distribution or meaning.  
- **Concept drift:** The relationship between inputs and outputs evolves.  
- **Model drift:** The internal state or learned embeddings shift after updates or retraining.  

**HU:**  
- **Adatdrift:** A bemeneti jellemzők eloszlása vagy jelentése módosul.  
- **Koncepciódrift:** Megváltozik az input–output kapcsolat logikája.  
- **Modelldrift:** A modell belső paraméterei vagy embeddingjei eltolódnak frissítés vagy újratanítás hatására.

---

## ⚙️ Anomaly Detection in AI / Anomáliák detektálása az AI-ban

**EN:**  
Anomaly detection focuses on identifying *rare or abnormal* inputs, patterns, or predictions that deviate from expected behavior. In AI security, anomalies can indicate:
- [[adversarial_input_detection|Adversarial Inputs]] attempting to fool the model  
- [[data_poisoning|Data Poisoning]] during training  
- Sensor malfunctions or corrupted data feeds  
- Model degradation or unauthorized fine-tuning  

**HU:**  
Az anomália-detektálás célja a *ritka vagy szokatlan* bemenetek, minták és kimenetek azonosítása, amelyek eltérnek a várt viselkedéstől. AI-biztonságban az anomáliák utalhatnak:
- a modell megtévesztésére irányuló [[adversarial_input_detection|Adversarial Inputs]] próbálkozásokra,  
- tanítási szakaszban történő [[data_poisoning|Data Poisoning]] támadásokra,  
- szenzorhibákra vagy sérült adatfolyamokra,  
- modellromlásra vagy illetéktelen finomhangolásra.

---

## 🧠 Example Scenario / Példahelyzet

**EN:**  
A self-driving car model trained in summer conditions encounters snow for the first time. Feature distributions like brightness, edge density, and object contours shift drastically. Drift detection flags this, triggering a retraining pipeline before the model’s perception errors become dangerous.  

**HU:**  
Egy önvezető autó modellje nyári körülmények között tanul, majd először találkozik hóval. Az olyan jellemzők, mint a fényerő, az élsűrűség és az objektumkontúrok eloszlása drasztikusan megváltozik. A drift-detektálás jelzi a változást, és újratanítási folyamatot indít, mielőtt a modell hibás és veszélyes döntéseket hozna.

---

## 🧭 Integration with Lifecycle / Integráció az életciklusba

**EN:**  
Drift and anomaly monitoring are integral parts of [[model_monitoring|Model Monitoring]] and [[ai_governance|AI Governance]]. When coupled with automated retraining, explainability checks, and [[data_versioning|Data Versioning]], they maintain a continuous loop of alignment between model behavior and real-world data.  

**HU:**  
A drift- és anomáliamonitoring szorosan kapcsolódik a [[model_monitoring|Model Monitoring]] és az [[ai_governance|AI Governance]] folyamatokhoz. Ha automatizált újratanítással, magyarázhatósági vizsgálatokkal és [[data_versioning|Data Versioning]] rendszerrel kombináljuk, akkor a modell működése folyamatosan igazodik a valós adatokhoz és környezethez.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What causes model drift and how does it impact security?  
2. How can statistical distance help detect drift?  
3. What is the difference between data drift and concept drift?  
4. Why is anomaly detection critical for trustworthy AI systems?  
5. How does drift monitoring connect to AI governance and retraining cycles?

---

> “Adaptation without awareness is chaos — detection turns it into learning.” 💡
