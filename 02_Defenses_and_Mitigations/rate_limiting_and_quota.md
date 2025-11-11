---
version: "3.2"
section_type: "defense"
agent: "Threat Mapper"
---
# ⏳ Rate Limiting & Quota Enforcement

---

## 🌍 What Is Rate Limiting? / Mi az a rate limiting?

**EN:**  
**Rate limiting** is a foundational security and reliability mechanism that restricts how frequently users or systems can access an API, model, or resource within a given time window.  
In AI systems — especially in [[model_serving_security|Model Serving Security]] and [[prompt_injection_and_rag_attacks|Prompt Injection Defense]] — rate limiting protects against brute-force queries, automated extraction, denial-of-service (DoS) attacks, and excessive model probing.  

It’s the “speed governor” of AI services: it ensures fair use, prevents overload, and stops attackers from learning too much too fast. 🚦🧩  

**HU:**  
A **rate limiting** (sebességkorlátozás) alapvető biztonsági és megbízhatósági mechanizmus, amely korlátozza, hogy a felhasználók vagy rendszerek milyen gyakran férhetnek hozzá egy API-hoz, modellhez vagy erőforráshoz meghatározott időn belül.  
Az MI-rendszerekben — különösen a [[model_serving_security|Modell-szolgáltatás biztonsága]] és a [[prompt_injection_and_rag_attacks|Prompt Injection elleni védelem]] esetében — ez megakadályozza a brute-force lekérdezéseket, az automatizált model-kinyerést, a szolgáltatásmegtagadást (DoS) és a túlzott modell-szondázást.  

Ez az MI-szolgáltatások „sebességszabályzója”: biztosítja a tisztességes használatot, megakadályozza a túlterhelést, és lelassítja a támadókat. 🚦🧩  

---

## 💡 Why It Matters / Miért fontos

**EN:**  
Without rate limiting, attackers can:  
- Enumerate API responses to extract a model ([[model_stealing_and_extraction|Model Extraction]])  
- Send adversarially optimized queries ([[adversarial_example_attacks|Adversarial Example Attacks]])  
- Trigger prompt-injection cascades in [[rag|RAG]] systems  
- Cause service degradation or full denial of service  
- Inflate operational costs through automated misuse  

**HU:**  
Rate limiting nélkül a támadók képesek lehetnek:  
- API-válaszok szisztematikus feltérképezésére ([[model_stealing_and_extraction|Modell-kinyerés]])  
- Adverszáriális lekérdezések futtatására ([[adversarial_example_attacks|Adverszáriális példák]])  
- Prompt-injekciós láncreakciók indítására [[rag|RAG]]-rendszerekben  
- Szolgáltatáslassításra vagy teljes leállításra  
- Üzemeltetési költségek felfuttatására automatizált visszaélésekkel  

---

## ⚙️ Core Mechanisms / Alapvető mechanizmusok

**EN:**  
Common rate limiting strategies include:

### 1️⃣ Token Bucket  
Each client has a bucket that fills at a constant rate. Each request consumes one token.  
If the bucket is empty → requests are delayed or denied.  

### 2️⃣ Leaky Bucket  
Similar to Token Bucket, but with fixed outflow rate — smooths burst traffic.  

### 3️⃣ Fixed Window  
A hard cap on the number of requests allowed per time window (e.g., 100/min).  

### 4️⃣ Sliding Window  
Tracks requests over a continuously moving window for more accurate enforcement.  

### 5️⃣ Adaptive Rate Limiting  
Uses ML or anomaly detection to dynamically adjust limits based on behavior patterns.  

**HU:**  
A leggyakoribb rate limiting stratégiák:

### 1️⃣ Token Bucket  
Minden klienshez tartozik egy vödör, amely állandó sebességgel töltődik. Minden kérés egy tokent fogyaszt.  
Ha a vödör üres → a kérést késleltetjük vagy elutasítjuk.  

### 2️⃣ Leaky Bucket  
A Token Buckethez hasonló, de fix kiáramlási sebességgel — kisimítja a forgalmi csúcsokat.  

### 3️⃣ Fix ablak  
Adott időintervallumon belül fix számú lekérdezés engedélyezett (pl. 100/perc).  

### 4️⃣ Csúszó ablak  
Folyamatosan mozgó időablak alapján számolja a kéréseket, így pontosabb a szabályozás.  

### 5️⃣ Adaptív Rate Limiting  
ML- vagy anomáliaészlelés segítségével dinamikusan módosítja a korlátokat a felhasználói viselkedés alapján.  

---

## 🧮 Formal Model / Formális megközelítés

**EN:**  
Let \( R_t \) be the number of requests a client makes during window \( t \).  
A rate limiter enforces:

$$
R_t \leq Q_{max}
$$

where \( Q_{max} \) is the quota or maximum number of requests allowed per period.  
Adaptive variants define \( Q_{max}(u, t) \) as a function of user risk score \( u \) and time \( t \):

$$
Q_{max}(u, t) = Q_0 \cdot \frac{1}{1 + e^{(r(u, t) - \tau)}}
$$

where \( r(u, t) \) is the behavioral risk and \( \tau \) a sensitivity threshold.  

**HU:**  
Legyen \( R_t \) a kliens által adott időablakban küldött kérések száma.  
A rate limiter betartatja:

$$
R_t \leq Q_{max}
$$

ahol \( Q_{max} \) a maximális engedélyezett kérésszám időszakonként.  
Az adaptív változatok \( Q_{max}(u, t) \)-t a felhasználói kockázati pontszám \( u \) és az idő \( t \) függvényeként határozzák meg:

$$
Q_{max}(u, t) = Q_0 \cdot \frac{1}{1 + e^{(r(u, t) - \tau)}}
$$

ahol \( r(u, t) \) a viselkedési kockázat, \( \tau \) pedig az érzékenységi küszöb.  

---

## 🧩 Quota Enforcement / Kvóta-kezelés

**EN:**  
While **rate limiting** controls request *frequency*, **quota enforcement** manages *total usage* over time — such as tokens, compute cost, or API credits.  

Quota systems are crucial for:  
- Preventing **model extraction** through high-volume queries  
- Managing **financial risk** in pay-per-use APIs  
- Enforcing **tiered access** (e.g., free vs enterprise customers)  
- Supporting **legal compliance** (data access limits per user)  

**HU:**  
Míg a **rate limiting** a lekérdezések *gyakoriságát* szabályozza, addig a **kvóta-kezelés** a *teljes felhasználást* korlátozza — például tokeneket, számítási erőforrást vagy API-kreditet.  

A kvóták kulcsfontosságúak:  
- A **modell-kinyerés** nagy mennyiségű lekérdezés általi megakadályozásához  
- A **pénzügyi kockázat** kezeléséhez „pay-per-use” API-k esetén  
- **Hozzáférési szintek** (pl. ingyenes vs vállalati) elkülönítéséhez  
- **Jogszabályi megfeleléshez** (felhasználónkénti adat-hozzáférési korlátok)  

---

## 🔒 Security Integration / Kapcsolódás a biztonsági architektúrához

**EN:**  
Rate limiting and quota enforcement are integral to:  
- [[model_serving_security|Model Serving Security]] — protect inference endpoints  
- [[api_security|API Security]] — stop brute-force and credential stuffing  
- [[model_stealing_and_extraction|Model Extraction Defense]] — cap query budgets  
- [[observability_and_monitoring|Observability & Monitoring]] — detect anomalies in query volume  
- [[zero_trust|Zero Trust for AI Systems]] — enforce per-identity policies  

**HU:**  
A rate limiting és a kvóta-kezelés szorosan kapcsolódik:  
- [[model_serving_security|Modell-szolgáltatás biztonsága]] — inferencia végpontok védelme  
- [[api_security|API-biztonság]] — brute-force és credential stuffing elleni védelem  
- [[model_stealing_and_extraction|Modell-kinyerés elleni védelem]] — lekérdezési büdzsé korlátozása  
- [[observability_and_monitoring|Observability & Monitoring]] — lekérdezési anomáliák felismerése  
- [[zero_trust|Zero Trust MI-rendszerekben]] — identitás-alapú házirendek betartatása  

---

## 🧠 Best Practices / Legjobb gyakorlatok

**EN:**  
- Apply rate limits **per user, per API key, and per IP**.  
- Combine static limits with **dynamic anomaly detection**.  
- Use **distributed rate limiters** (Redis, Envoy, API Gateway).  
- Implement **backoff and retry** policies to prevent overload.  
- Enforce **separate limits for sensitive operations** (e.g., model introspection).  
- Log and correlate rate-limit events in your [[observability_and_monitoring|Observability]] stack.  
- Provide **graceful error handling** (HTTP 429) with retry-after headers.  

**HU:**  
- Alkalmazz limitet **felhasználónként, API-kulcsonként és IP-címenként**.  
- Kombináld a statikus limiteket **dinamikus anomáliaészleléssel**.  
- Használj **elosztott rate limitert** (Redis, Envoy, API Gateway).  
- Valósíts meg **backoff és retry** politikát a túlterhelés elkerülésére.  
- **Érzékeny műveletekre** (pl. modell-lekérdezés, introspekció) külön limitet vezess be.  
- **Naplózd és korreláld** a rate-limit eseményeket az [[observability_and_monitoring|Observability]] rendszerben.  
- Biztosíts **kifinomult hibakezelést** (HTTP 429) és „retry-after” fejlécet.  

---

## ⚖️ Trade-offs / Kompromisszumok

**EN:**  
- Overly strict limits can hurt user experience and legitimate batch workloads.  
- Too lenient limits expose the system to probing and extraction attacks.  
- Dynamic adaptation (e.g., trust-based scaling) improves balance but adds complexity.  

**HU:**  
- A túl szigorú limitek rontják a felhasználói élményt és a jogos folyamatok futását.  
- A túl laza limitek lehetőséget adnak szondázásra és kinyeréses támadásokra.  
- A dinamikus adaptáció (pl. bizalmi szint alapú skálázás) jobb egyensúlyt teremt, de bonyolultabb megvalósítást igényel.  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What is the difference between rate limiting and quota enforcement in AI APIs?  
2. How can rate limiting mitigate model extraction and prompt-injection attacks?  
3. Describe how adaptive rate limiting can use behavioral risk scores to adjust quotas.  
4. What telemetry signals would indicate a rate limit bypass attempt?  
5. Design a rate-limiting policy for an LLM API serving both enterprise and public users.

---

> “Security is not just about stopping bad requests — it’s about pacing trust.” ⏳
