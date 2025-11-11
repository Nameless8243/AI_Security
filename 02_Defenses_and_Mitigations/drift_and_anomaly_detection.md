# Drift & Anomaly Detection in AI Systems 📉

_Catching misbehavior before it becomes an incident – bilingual educational version (HU + EN)_

---

AI models don’t break like classic software.  
They **slowly slide** out of alignment: data changes, user behavior shifts, attackers adapt, and suddenly the model is making decisions that _used to be_ correct, but now are subtly wrong.

This slow slide is called **drift** — and if you don’t detect it, it silently becomes an **incident**.  
Ez a fejezet arról szól, hogyan ismerd fel, ha a modelled _eltávolodik a valóságtól_ vagy a biztonságos működéstől, és hogyan állítsd meg, mielőtt kárt okozna.

---

## 🧭 What is Drift? – Mi az a drift?

**EN:**  
In AI, **drift** means that the world the model sees has changed compared to the world it was trained on.  
The model is still “correct” _relative to its training data_, but that data is no longer representative of current reality.

**Types of drift you’ll meet in practice:**

- **Data (input) drift:** the distribution of incoming inputs changes.
    
- **Label (target) drift:** the relationship between features and labels changes (e.g., fraud patterns evolve).
    
- **Concept drift:** the underlying meaning of “right vs wrong” changes (e.g., new regulations or business rules).
    

**HU:**  
AI-ban **driftnek** azt nevezzük, amikor a modell **más világot lát**, mint amire tanítottuk.  
A modell a saját tréning-adatához képest még „oké”, csak épp a valóság ment el mellette.

**A legfontosabb drift-típusok:**

- **Adat (input) drift:** megváltozik a beérkező adatok eloszlása.
    
- **Label (target) drift:** a bemenet–kimenet kapcsolat változik (pl. új csalási minták).
    
- **Koncept drift:** maga a _„mi a jó döntés”_ változik (jogszabály, üzleti szabály, etikai elv).
    

💡 _Drift is not a bug — it’s the world moving while your model stands still._

---

## 🚨 Why Drift is a Security & Safety Problem

**EN:**  
Drift is not only a “data science” concern — it’s a **security and safety** concern:

- A fraud model with drift can start **approving fraud**.
    
- A content filter with drift might miss **toxic or extremist content**.
    
- A medical triage model with drift can misprioritize patients.
    

Attackers can even **weaponize drift**:

- By slowly injecting poisoned inputs over time ([[data_poisoning_attacks|Data Poisoning Attacks]]).
    
- By exploiting changes in user behavior to trigger misclassifications.
    

**HU:**  
A drift nem csak adatkutatói probléma — **biztonsági és safety-kérdés**:

- Ha driftes a csalásdetektáló modell, elkezd **tévesen jóváhagyni csalásokat**.
    
- Ha driftes a tartalomszűrő, nem veszi észre a **toxikus / szélsőséges tartalmakat**.
    
- Ha driftes az orvosi modell, **rossz pácienst rangsorol előre vagy hátra**.
    

A támadók akár **szándékosan is generálhatnak driftet**:  
lassan adagolt mérgező inputokkal, szokatlan mintákkal, amelyek kicsúsztatják a modellt az ideális működésből.

---

## 🧠 Anomaly Detection vs Drift Detection

**EN:**  
Although related, **drift** and **anomalies** are not the same:

- Drift = _systematic_ shift of the whole distribution.
    
- Anomaly = _local_ weirdness (outliers, spikes, unexpected events).
    

You need both:

- **[[drift_and_anomaly_detection|Drift Detection]]** to see the long-term trend.
    
- **Anomaly Detection** to spot sudden, suspicious events (e.g., a burst of adversarial queries).
    

**HU:**  
Bár kapcsolódnak, a **drift** és az **anomália** nem ugyanaz:

- Drift = _rendszerszintű_ eltolódás az idők során.
    
- Anomália = _helyi_ furcsaság — kiugró pont, szokatlan esemény.
    

Mindkettőre szükség van:

- **Drift Detektálás**: hosszú távú elcsúszás figyelése
    
- **Anomália Detektálás**: hirtelen, gyanús történések (pl. támadási próbálkozás-csúcs) felismerése
    

---

## 🧩 Where to Monitor for Drift & Anomalies

**EN:**  
You can (and should) monitor multiple layers of your AI system:

1. **Input Level:**
    
    - Monitor the distribution of incoming data: feature ranges, categorical frequencies, language, source.
        
    - Catch abnormal spikes: weird tokens, repeated prompts, suspicious IP ranges.
        
2. **Model Output Level:**
    
    - Track predicted classes, probabilities, and calibration over time.
        
    - Monitor toxicity scores, bias indicators, hallucination likelihood (for LLMs).
        
3. **Behavior Level (Systems & Users):**
    
    - Monitor user behavior: error reports, manual overrides, escalations.
        
    - Monitor downstream system impact: chargebacks, safety complaints, legal incidents.
        

**HU:**  
Driftet és anomáliát több rétegen kell figyelni:

1️⃣ **Bemeneti szint:**

- Az érkező adatok eloszlása, tartománya, típusa, forrása
    
- Szokatlan tüskék: fura tokenek, ismétlődő promptok, gyanús IP-tartományok
    

2️⃣ **Modell kimeneti szint:**

- Predikált osztályok eloszlása, valószínűségek, kalibráció
    
- Toxicitás, torzítás-mutatók, LLM-eknél a hallucináció gyanúja
    

3️⃣ **Viselkedési szint (felhasználó + rendszer):**

- Felhasználói panaszok, manuális felülbírálások, eszkalációk
    
- Üzleti mutatók: chargeback, safety-incident, compliance-riasztások száma
    

🎯 _If you only watch accuracy on a test set, you are blind to real-world drift._

---

## 🧪 Techniques for Drift Detection

**EN:**  
Common techniques include:

- **Statistical Distance Metrics:**  
    Compare new data to training data using KL divergence, Jensen–Shannon divergence, Kolmogorov–Smirnov tests, etc.
    
- **Population Stability Index (PSI):**  
    Widely used in finance; measures how much a feature distribution has shifted.
    
- **Embedding-based Drift:**  
    For text/image models, compute embeddings and monitor shifts in embedding space instead of raw tokens or pixels.
    
- **Performance Drift:**  
    Monitor business KPIs and ground truth where available: increased error rates, fewer true positives, more false negatives.
    

**HU:**  
Elterjedt drift-detektálási módszerek:

- **Statisztikai távolságok:**  
    Az új és régi adat eloszlásainak összehasonlítása (KL-divergencia, JS-divergencia, KS-teszt stb.).
    
- **PSI (Population Stability Index):**  
    Főleg pénzügyben használják; azt méri, mennyire tért el egy változó eloszlása a referenciától.
    
- **Embedding-alapú drift:**  
    Szöveg- és képalapú modelleknél az embedding-térben figyeljük a változást, nem a nyers tokeneket vagy pixeleket.
    
- **Teljesítmény-drift:**  
    Üzleti vagy ground-truth mutatók romlása: több hiba, kevesebb helyes találat, több panasz.
    

---

## 🔍 Techniques for Anomaly Detection

**EN:**  
For anomalies, we usually care about **rare, suspicious patterns**:

- Unusually high number of failed logins / API calls
    
- Sudden spike in “jailbreak” prompts to an LLM
    
- Highly unusual input combinations (never seen before in training)
    

Techniques include:

- **Rule-based detectors:** simple thresholds, regex, allowlists/denylists.
    
- **Unsupervised models:** Isolation Forest, One-Class SVM, autoencoders on embeddings.
    
- **Hybrid:** rules + ML to reduce false positives.
    

**HU:**  
Anomáliáknál a **ritka, gyanús mintákra** vadászunk:

- Hirtelen megugró sikertelen belépések
    
- Prompt injection kísérletek „hullámai” LLM-eknél
    
- Olyan bemenetek, amelyeket a tréningadat sosem látott együtt
    

Alkalmazható technikák:

- **Szabályalapú detektálás:** küszöbértékek, regex, allow/deny listák
    
- **Felhügyelet nélküli modellek:** Isolation Forest, One-Class SVM, autoencoder az embedding-térben
    
- **Hibrid megoldások:** a szabályok és ML kombinálása a hamis pozitívak csökkentésére
    

---

## 🛰️ Observability for AI – láthatóvá tenni a láthatatlant

**EN:**  
Drift and anomaly detection live inside a broader practice: **[[observability_and_monitoring|Observability and Monitoring]]** for AI.  
This includes:

- Centralized logging of inputs, outputs, and metadata
    
- Model-version tracking ([[ai_model_provenance_and_lineage|Provenance & Lineage]])
    
- Correlation with infrastructure metrics (CPU, GPU, memory, latency)
    
- Linking alerts to [[incident_response_for_ai|Incident Response Playbooks]]
    

**HU:**  
A drift- és anomália-detektálás az **AI Observability** része.  
Ide tartozik:

- Bemenetek, kimenetek és metaadatok központosított naplózása
    
- Modellverziók és lineage nyomon követése
    
- Infrastruktúra-metrikák (CPU, GPU, memória, latency) korrelálása a modellviselkedéssel
    
- Riasztások kapcsolása az [[incident_response_for_ai|AI Incidenskezelési]] playbookokhoz
    

💡 _You can’t detect what you don’t log — and you shouldn’t log what you can’t protect._

---

## 🔄 Drift Detection as Part of the Lifecycle

**EN:**  
Drift detection isn’t a one-off task — it’s embedded into the **AI lifecycle**:

1. **During Design:**
    
    - Identify which features are most sensitive to drift.
        
    - Decide what “normal behavior” looks like and how to measure it.
        
2. **During Deployment:**
    
    - Enable logging and metrics from day one.
        
    - Set initial thresholds and alerts based on training data.
        
3. **During Operation:**
    
    - Continuously compare live data to reference distributions.
        
    - Trigger retraining / human review when drift crosses thresholds.
        
4. **During Governance Reviews:**
    
    - Use drift reports as input to [[ai_risk_assessment_methodology|Risk Assessments]].
        
    - Document decisions to retrain, rollback, or retire models.
        

**HU:**  
A drift-detektálás nem egy külön feladat, hanem az **AI-életciklus része**:

1️⃣ **Tervezéskor:**

- Azonosítsd, mely feature-ök érzékenyek a driftre.
    
- Döntsd el, hogy mi számít „normális működésnek”, és hogyan méred.
    

2️⃣ **Bevetéskor:**

- Már az első naptól legyen naplózás és metrika.
    
- Állíts be kezdő küszöböket a tréningadat alapján.
    

3️⃣ **Üzemeltetés közben:**

- Folyamatosan hasonlítsd össze a live adatot a referenciával.
    
- Küszöb átlépésekor indíts retraininget vagy emberi review-t.
    

4️⃣ **Governance-reviewk során:**

- Használd a drift-jelentéseket a kockázatelemzés részeként.
    
- Dokumentáld, mikor, miért és hogyan tanítottad újra vagy vontad vissza a modellt.
    

---

## 🧯 Linking Drift to Incident Response

**EN:**  
Sometimes drift is slow and harmless.  
Other times, it’s a **pre-incident signal**.

That’s why your drift detection must integrate with:

- **[[incident_response_for_ai|AI Incident Response]]** (automatic case creation when thresholds are exceeded)
    
- **[[red_teaming_and_simulation|Red Teaming & Simulation]]** (test whether drift makes attacks easier)
    
- **[[ai_security_metrics_and_kpis|Security Metrics & KPIs]]** (drift indicators as leading risk signals)
    

**HU:**  
A drift néha ártalmatlan, máskor **közelgő incidens előjele**.  
Ezért a drift-detektort össze kell kötni:

- az **AI Incidenskezeléssel** (küszöb átlépése → ticket, eszkaláció)
    
- a **Red Teaminggel** (meg kell nézni, a drift nem könnyíti-e meg a támadást)
    
- a **Security KPI-kkel** (a drift a kockázat növekedését jelző korai mutató lehet)
    

🎯 _Think of drift alerts as smoke detectors — not every alarm means fire, but you never ignore them._

---

## 🧠 Practical Example – Fraud Detection Model

**EN:**  
A bank uses a model to detect fraud.  
For months, performance is stable — then the drift dashboard shows:

- More transactions at night
    
- New geographic clusters
    
- Less frequent use of older payment methods
    

The model’s accuracy on recent labeled data starts to fall.  
At the same time, chargebacks increase.

Actions:

- Investigate feature drift and concept drift
    
- Retrain the model with recent data
    
- Update [[model_certification_and_testing|Certification Tests]]
    
- Adjust threshold and guardrails
    

**HU:**  
Egy bank csalásdetektáló modellt használ.  
Hónapokig stabil, majd a drift-dashboard ezt mutatja:

- több éjszakai tranzakció,
    
- új földrajzi minták,
    
- a régi fizetési módok visszaszorulása.
    

A modell pontossága csökken, a chargeback-ek nőnek.

Teendők:

- A drift okának elemzése (feature + koncept drift)
    
- A modell újratanítása friss adatokkal
    
- A tanúsítási tesztek frissítése
    
- A küszöbök és guardrailok módosítása
    

---

## 🧠 Review Questions / Ellenőrző kérdések

1. What is the difference between **drift** and **anomaly** in AI systems?
    
2. Why is drift both a data science and a security/safety concern?
    
3. Which layers (input, model, behavior) should be monitored for drift and anomalies?
    
4. How can embedding-based monitoring help with drift detection in NLP or vision models?
    
5. How do drift alerts integrate with [[incident_response_for_ai|Incident Response]] and [[ai_risk_assessment_methodology|Risk Management]]?
    

---

> “AI doesn’t usually fail with a bang.  
> It fails with a quiet slide into irrelevance — unless you watch it.” 📉