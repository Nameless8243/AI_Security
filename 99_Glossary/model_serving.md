---
id: model_serving
title: "Model Serving / Modell-kiszolgálás"
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

*Serving models securely in an untrusted world ⚙️🧩*

## 🧠 Overview

**EN:**  
When a model is deployed for inference, it stops being just data — it becomes an *active target*. The serving infrastructure connects your trained model to unpredictable users and potentially malicious inputs. A single misconfiguration or unprotected endpoint can compromise the entire [[ai_pipeline|AI pipeline]].  

**HU:**  
Amikor egy modellt éles környezetbe helyezünk, az többé nem pusztán adat — hanem *aktív célpont*. A kiszolgáló infrastruktúra köti össze a betanított modellt a felhasználókkal és azok potenciálisan rosszindulatú bemeneteivel. Egyetlen hibás beállítás vagy védtelen végpont az egész [[ai_pipeline|AI-folyamatot]] veszélybe sodorhatja.

---

## 🛠️ Security Considerations

**EN:**  
When serving models, attackers may exploit the serving layer to **steal models, poison responses, or crash services**.  
Common threats include:

- [[model_extraction|Model Extraction]] – replicating models through API queries.  
- [[prompt_injection|Input Injection]] – sending crafted inputs to manipulate behavior.  
- [[data_poisoning|Data Poisoning]] – compromising feedback loops or retraining data.  
- [[serialization_attack|Serialization Attacks]] – exploiting unsafe deserialization libraries.  

Security therefore requires both **application-layer** and **ML-layer** protections.

$$
\text{Secure Serving} = f(\text{Access Control}, \text{Monitoring}, \text{Integrity Checks})
$$

**HU:**  
A modellkiszolgálás során a támadók kihasználhatják a szolgáltatási réteg gyengeségeit: **ellophatják a modellt, manipulálhatják a válaszokat, vagy összeomlaszthatják a szolgáltatást**.  
A leggyakoribb fenyegetések:

- [[model_extraction|Modell-kivonás]] – az API-lekérdezések alapján reprodukálható a modell.  
- [[prompt_injection|Input-injekció]] – manipulált bemenetek a viselkedés torzításához.  
- [[data_poisoning|Adatmérgezés]] – a visszacsatolt vagy újratanított adatok megmérgezése.  
- [[serialization_attack|Szerializációs támadások]] – nem biztonságos deszerializációs könyvtárak kihasználása.  

A biztonság ezért **alkalmazás- és ML-szinten** is védelmet igényel.

$$
\text{Secure Serving} = f(\text{Hozzáférés-vezérlés}, \text{Megfigyelés}, \text{Integritás-ellenőrzés})
$$

---

## ⚖️ Performance vs. Security Trade-off

**EN:**  
Model serving environments often trade performance for protection. Encrypting every inference, isolating containers, and verifying inputs can add latency — but this latency buys **resilience**. In security terms:

$$
\text{Latency Cost} \propto \text{Security Gain}
$$

Every extra millisecond spent on verification reduces the attack surface of an entire cluster.

**HU:**  
A kiszolgáló környezetek gyakran kompromisszumot kötnek a **teljesítmény és a védelem** között. A predikciók titkosítása, a konténerek elkülönítése és a bemenetek ellenőrzése növeli a késleltetést — de ez a késleltetés **megbízhatóságot vásárol**.  
Biztonsági értelemben:

$$
\text{Késleltetési Költség} \propto \text{Biztonsági Nyereség}
$$

Minden plusz milliszekundum ellenőrzés csökkenti a teljes klaszter támadási felületét.

---

## 🧩 Threat Detection at Serving Time

**EN:**  
Traditional firewalls and IDS systems do not detect AI-specific anomalies.  
AI serving requires **telemetry-based behavioral defense**, including:

- Embedding-level anomaly detection (to spot adversarial queries).  
- Query volume and entropy monitoring for [[model_extraction|model extraction]] attempts.  
- Drift and [[membership_inference|membership inference]] detection using statistical deviation.  

$$
\text{Risk}_{\text{serving}} = f(Q_{\text{volume}}, Q_{\text{entropy}}, D_{\text{drift}})
$$

**HU:**  
A hagyományos tűzfalak és IDS rendszerek nem képesek felismerni az AI-specifikus anomáliákat.  
Az AI-kiszolgálás **viselkedés-alapú védelmet** igényel, amely tartalmazza:

- Az embedding-alapú anomáliafelismerést (az adversarial lekérdezések kimutatására).  
- A lekérdezések mennyiségének és entrópiájának figyelését [[model_extraction|modell-kivonási]] kísérletek esetén.  
- A drift és a [[membership_inference|tagsági következtetés]] statisztikai eltérés-alapú detektálását.

$$
\text{Kiszolgálási Kockázat} = f(Q_{\text{mennyiség}}, Q_{\text{entrópia}}, D_{\text{drift}})
$$

---

## 🔐 Zero Trust Model Serving

**EN:**  
Applying [[zero_trust_for_ai|Zero Trust for AI]] to serving means **never trusting any query by default**.  
Each inference request is authenticated, logged, rate-limited, and isolated.  
The goal is to reduce trust scope to the absolute minimum.

Key practices:
- Strict API key or [[identity_and_access_management|IAM]] validation.  
- Sandboxed execution using Firecracker or Kata Containers.  
- Encrypted model weights with HSM or KMS keys.  
- Real-time integrity validation via signed hashes.

**HU:**  
A [[zero_trust_for_ai|Zero Trust]] elv alkalmazása a kiszolgálásban azt jelenti, hogy **semmilyen lekérdezés nem tekinthető biztonságosnak alapértelmezetten**.  
Minden predikciós kérés hitelesítve, naplózva, sebességkorlátozva és izolálva van.  
A cél a bizalmi kör minimalizálása.

Fő gyakorlatok:
- Szigorú API-kulcs vagy [[identity_and_access_management|IAM]] ellenőrzés.  
- Sandbox futtatás (Firecracker, Kata Containers).  
- Modell-súlyok titkosítása HSM vagy KMS kulccsal.  
- Valós idejű integritás-ellenőrzés aláírt hash segítségével.

---

## 📊 Logging, Auditing, and Assurance

**EN:**  
Serving security depends on continuous assurance.  
Without telemetry, no trust is provable.  
Logs must include metadata such as user ID, timestamp, model version, and query fingerprint.  
This enables real-time rollback and accountability under [[ai_governance_frameworks|AI Governance]].

**HU:**  
A kiszolgálás biztonsága a **folyamatos bizonyíthatóságon** alapul.  
Telemetria nélkül nincs igazolható biztonság.  
A naplóknak tartalmazniuk kell a felhasználó azonosítóját, időbélyeget, modellverziót és lekérdezési ujjlenyomatot.  
Ez teszi lehetővé a valós idejű visszagörgetést és az elszámoltathatóságot a [[ai_governance_frameworks|AI irányítás]] keretein belül.

---

## ⚙️ Example: Secure Inference Workflow

**EN:**  
Typical hardened inference pipeline:

1. **Client Request** → Authenticated and signed  
2. **API Gateway** → Token validation and throttling  
3. **Sandboxed Model Runtime** → Isolated inference container  
4. **Telemetry Logger** → Embedding fingerprints  
5. **Monitor & Response** → Drift and attack detection  

**HU:**  
Tipikus biztonságos inference-folyamat:

1. **Kliens kérés** → Hitelesített és aláírt  
2. **API Gateway** → Tokenellenőrzés és sebességkorlátozás  
3. **Szigetelt modellfuttatás** → Izolált inference-konténer  
4. **Telemetria-naplózó** → Embedding ujjlenyomatok rögzítése  
5. **Monitor és válasz** → Drift- és támadásdetektálás

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What distinguishes serving-layer threats from training-time attacks?  
2. How can [[zero_trust_for_ai|Zero Trust principles]] be adapted for model inference?  
3. Why is telemetry essential to model serving assurance?  
4. How does performance degradation relate to security gain?  
5. Which detection methods best expose [[model_extraction|model extraction]] attempts?

---

> _“When a model begins to serve others, its first duty is to protect itself.”_ 🛡️🤖

🚨 COPY END 🚨
