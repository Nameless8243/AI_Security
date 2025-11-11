# 📈 Model Monitoring

---

## 🌍 What Is Model Monitoring? / Mi az a modell-monitorozás?

**EN:**  
**Model monitoring** is the continuous process of tracking an AI model’s behavior, inputs, outputs, and performance in production to ensure that it remains accurate, secure, and trustworthy over time.  
It’s how we detect when a model “goes off the rails” — whether due to data drift, bias, poisoning, adversarial attacks, or silent degradation.  

In AI security, model monitoring is not just about accuracy — it’s about **integrity, reliability, and early detection of threats** to the model’s decision logic. 🛡️📊  

**HU:**  
A **modell-monitorozás** az a folyamatos folyamat, amely során az MI-modell viselkedését, bemeneteit, kimeneteit és teljesítményét figyeljük a produkcióban, hogy hosszú távon pontos, biztonságos és megbízható maradjon.  
Ez teszi lehetővé, hogy észrevegyük, ha a modell „letér a pályáról” — akár adatdrift, torzítás, mérgezés, adverszáriális támadás vagy fokozatos romlás miatt.  

Az MI-biztonságban a modell-monitorozás nemcsak a pontosságról szól — hanem a **modell integritásának, megbízhatóságának és logikai biztonságának** megőrzéséről. 🛡️📊  

---

## 💡 Why It Matters / Miért fontos

**EN:**  
Without monitoring, you cannot detect:  
- Gradual accuracy degradation (concept drift)  
- Adversarial probing or [[data_poisoning|data poisoning]]  
- Unauthorized model behavior (e.g., prompt leakage, backdoor activation)  
- Bias amplification or fairness decay  
- Infrastructure misuse or abnormal inference loads  

Monitoring turns AI systems from *black boxes* into *observable systems* — enabling incident response, accountability, and compliance.  

**HU:**  
Monitorozás nélkül nem észlelheted:  
- A pontosság fokozatos romlását (konceptuális drift)  
- [[data_poisoning|Adatmérgezés]] vagy adverszáriális szondázás jeleit  
- Jogosulatlan modellviselkedést (pl. prompt-szivárgás, backdoor-aktiválás)  
- Torzítás felerősödését vagy fairness romlását  
- Infrastruktúra-visszaélést vagy abnormális inferencia-terhelést  

A monitorozás átláthatóvá teszi az MI-rendszert: *feketeboxból megfigyelhető rendszerré* alakítja, támogatva az incidenskezelést, elszámoltathatóságot és megfelelést.  

---

## ⚙️ What to Monitor / Mit érdemes figyelni

**EN:**  
Model monitoring spans multiple dimensions:  

1. **Data Drift:**  
   Detect shifts in input feature distributions compared to training data.  
   (E.g., change in demographics, language, or environmental conditions.)  

2. **Concept Drift:**  
   The relationship between features and labels evolves over time.  

3. **Prediction Behavior:**  
   Confidence entropy, output distribution, or class frequency changes.  

4. **Security Events:**  
   Detect adversarial examples, abnormal query frequency, or injection attempts.  

5. **Fairness & Bias:**  
   Track group-level performance parity over time.  

6. **Operational Metrics:**  
   Latency, throughput, memory usage, rate-limit hits, etc.  

**HU:**  
A modell-monitorozás több dimenziót fog át:  

1. **Adat-drift:**  
   A bemeneti jellemzők eloszlásának eltolódása a tanítóadatokhoz képest.  
   (Pl. demográfiai, nyelvi vagy környezeti változások.)  

2. **Konceptuális drift:**  
   A jellemzők és a címkék közötti kapcsolat idővel módosul.  

3. **Predikciós viselkedés:**  
   Bizalmi entrópia, kimeneti eloszlás vagy osztályfrekvencia-változások.  

4. **Biztonsági események:**  
   Adverszáriális példák, abnormális lekérdezés-minták, injekciós kísérletek észlelése.  

5. **Fairness és torzítás:**  
   Csoportszintű teljesítményparitás követése időben.  

6. **Operatív metrikák:**  
   Késleltetés, áteresztőképesség, memóriahasználat, rate-limit találatok stb.  

---

## 🧮 Formal Drift Detection / Formális drift-észlelés

**EN:**  
A model’s input distribution \( P_{train}(x) \) may diverge from the live distribution \( P_{prod}(x) \).  
We quantify drift using statistical divergence:

$$
D_{KL}(P_{train} \parallel P_{prod}) = \sum_i P_{train}(x_i) \log \frac{P_{train}(x_i)}{P_{prod}(x_i)}
$$

A large \( D_{KL} \) indicates drift — prompting model retraining or revalidation.

**HU:**  
A modell bemeneti eloszlása \( P_{train}(x) \) eltérhet az aktuális produkciós eloszlástól \( P_{prod}(x) \).  
A driftet statisztikai divergenciával mérjük:

$$
D_{KL}(P_{train} \parallel P_{prod}) = \sum_i P_{train}(x_i) \log \frac{P_{train}(x_i)}{P_{prod}(x_i)}
$$

A nagy \( D_{KL} \) driftet jelez — ilyenkor újratanítás vagy revalidálás szükséges.  

---

## 🧩 Security-Focused Monitoring / Biztonság-központú monitorozás

**EN:**  
AI security requires special observables:  
- **Query anomaly detection:** identify suspicious input sequences or patterns (e.g., probing model boundaries).  
- **Adversarial noise signatures:** track gradient-space perturbation norms.  
- **Backdoor activation triggers:** monitor latent activations for known trigger patterns.  
- **Model extraction traces:** correlate API calls to detect systematic function approximation attempts.  
- **Output leakage detection:** scan model responses for secrets, code, or prompt fragments.  

**HU:**  
Az MI-biztonság speciális megfigyelési pontokat igényel:  
- **Lekérdezési anomália-észlelés:** gyanús inputminták felismerése (pl. modell-határok szondázása).  
- **Adverszáriális zaj minták:** gradiens-térben mért perturbációk normájának követése.  
- **Backdoor-aktiválási jelek:** ismert triggerekhez kapcsolódó rejtett aktivációk monitorozása.  
- **Modell-kinyerés nyomai:** API-hívások korrelációja a funkció-approximalás felismerésére.  
- **Kimeneti szivárgás-észlelés:** modellek válaszainak szkennelése titkok, kód vagy prompt-töredékek után.  

---

## 🧠 Integration & Tooling / Integráció és eszközök

**EN:**  
Monitoring integrates with:  
- [[observability_and_monitoring|Observability Stack]] — central metrics and tracing  
- [[consistency_audit|Consistency Audit]] — check behavioral stability across versions  
- [[incident_response_for_ai|AI Incident Response]] — trigger alerts and workflows  
- [[governance_index|Governance Index]] — ensure accountability and compliance  

### Common Tools:
- Prometheus / Grafana (metrics dashboards)  
- Evidently / WhyLabs (ML drift detection)  
- Seldon Core / Arize / Fiddler (AI observability platforms)  
- OpenTelemetry for unified tracing  

**HU:**  
A monitorozás integrálódik:  
- [[observability_and_monitoring|Observability rendszerrel]] — központi metrikák és trace-ek  
- [[consistency_audit|Konzisztencia-audit]] — viselkedés-stabilitás ellenőrzése verziók között  
- [[incident_response_for_ai|MI incidenskezelés]] — riasztások és automatizált folyamatok indítása  
- [[governance_index|Irányítási index]] — elszámoltathatóság és megfelelőség biztosítása  

### Gyakori eszközök:
- Prometheus / Grafana (metrika dashboardok)  
- Evidently / WhyLabs (ML drift detektálás)  
- Seldon Core / Arize / Fiddler (AI-observability platformok)  
- OpenTelemetry a közös nyomkövetéshez  

---

## 🔗 Connection to Lifecycle / Kapcsolat az életciklussal

**EN:**  
Model monitoring is part of the **secure MLOps loop**:  

**Train → Validate → Deploy → Monitor → Retrain → Audit**

When integrated properly, it closes the feedback loop — turning each anomaly into learning for future robustness.  

**HU:**  
A modell-monitorozás a **biztonságos MLOps-ciklus** része:  

**Tanítás → Validálás → Bevezetés → Monitorozás → Újratanítás → Audit**

Megfelelő integráció esetén ez bezárja a visszacsatolási hurkot — minden anomália a jövőbeli robusztusság tanulságává válik.  

---

## ⚖️ Trade-offs / Kompromisszumok

**EN:**  
- Too much logging → privacy and cost concerns  
- Too little monitoring → silent degradation or missed attacks  
- Continuous retraining can amplify data drift if not verified  
- Must balance privacy (e.g., [[differential_privacy|Differential Privacy]]) with auditability  

**HU:**  
- Túl sok naplózás → adatvédelmi és költségbeli aggályok  
- Túl kevés monitorozás → csendes teljesítményromlás vagy támadások észrevétlenek maradnak  
- Az automatikus újratanítás driftet is felerősíthet, ha nincs ellenőrizve  
- Az adatvédelem (pl. [[differential_privacy|Differenciális adatvédelem]]) és az auditálhatóság között egyensúlyra van szükség  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. How does model monitoring differ from observability in AI security?  
2. Explain the difference between data drift and concept drift with examples.  
3. What indicators suggest a possible adversarial or poisoning attack?  
4. How would you design a monitoring pipeline for an LLM API with RAG integration?  
5. What trade-offs arise between monitoring depth and data privacy?  

---

> “A model that’s not monitored is a model that’s already drifting.” 📉
