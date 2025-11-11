---
id: data_poisoning
title: "Data Poisoning / Adatmérgezés"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "01_Glossary"
agent: "Threat Mapper"
tags:
  - ai_security
  - glossary
  - underscore_slug
---
# ☣️ Data Poisoning / Adatmérgezés

**Lifecycle phase:** Training / Model Supply Chain

---

## 🌍 Concept Overview / Fogalmi áttekintés

**EN:**  
Data poisoning refers to the deliberate corruption of training data to manipulate an AI model’s learning process. It compromises the *trust chain* at the very origin — data collection and curation — and allows attackers to influence model behavior, inject hidden triggers, or degrade overall accuracy. What makes poisoning especially dangerous is its stealth: the model behaves normally during testing but fails catastrophically in specific attacker-chosen conditions.

**HU:**  
Az adatmérgezés a tanító adatok szándékos megfertőzését jelenti, amelynek célja az AI-modell tanulási folyamatának manipulálása. Ez már az adatgyűjtés és -feldolgozás szintjén megbontja a *bizalmi láncot*, lehetővé téve a támadó számára a modell működésének befolyásolását, rejtett triggerek beépítését vagy a pontosság rombolását. Az adatmérgezés különösen veszélyes, mert rejtve marad: a modell normálisan viselkedik a tesztelés során, de célzott körülmények között súlyosan hibázik.

---

## 💡 Core Idea / Alapelv

**EN:**  
Unlike adversarial examples, which target the inference phase, data poisoning attacks compromise the *training dataset itself*. A few malicious samples can irreversibly change model parameters. Once the poisoned data is integrated, even retraining cannot guarantee a clean recovery.  

**HU:**  
Az adatmérgezés az **inferenciafázistól eltérően** nem a kimenetet, hanem magát a *tanító adathalmazt* támadja. Már néhány rosszindulatú minta is visszafordíthatatlanul megváltoztathatja a modell paramétereit. Miután ezek az adatok bekerülnek a tanulásba, az újratanítás sem mindig képes teljesen helyreállítani a modellt.

---


## 🧮 Mathematical View / Matematikai szemlélet

**EN:**  
Let the training dataset be:

$$
D = {(x, y)}
$$

A poisoning attack inserts malicious samples to maximize the model’s performance degradation:

$$
max(x′, y′)[L(fθ*(x′), y′) − L(fθ(x), y)]
$$

where fθ* is the poisoned model and fθ the clean baseline.  
The attacker’s goal is to find small perturbations that alter gradient updates, forcing the model to learn incorrect or biased representations.

**HU:**  
Legyen a tanító adathalmaz:

$$
D = {(x, y)}
$$

Az adatmérgezés során a támadó rosszindulatú mintákat ad hozzá, hogy a modell teljesítményromlását maximalizálja:

$$
max(x′, y′)[L(fθ*(x′), y′) − L(fθ(x), y)]
$$

ahol fθ* a mérgezett, fθ pedig a tiszta modell.  
A támadó célja apró perturbációkkal megváltoztatni a gradiensfrissítéseket, így a modell hibás vagy torzított reprezentációkat tanul meg.




---

## ⚙️ Implementation & Attack Vectors / Megvalósítás és támadási vektorok

**EN:**  
1. **Label-flipping attacks** – Modify correct samples with incorrect labels.  
2. **Backdoor injection** – Embed hidden triggers in specific patterns (e.g., pixel patches, keywords).  
3. **Clean-label poisoning** – Select semantically valid but adversarial samples that bias learning.  
4. **Gradient manipulation** – Craft data that drives gradient descent toward adversarial minima.  

**HU:**  
1. **Címkefelcseréléses támadás** – Helyes minták szándékos hibás címkézése.  
2. **Hátsó kapu beültetés** – Rejtett triggerek elhelyezése speciális mintákban (pl. pixelminták, kulcsszavak).  
3. **Tiszta-címkés mérgezés** – Látszólag érvényes, de torzító minták kiválasztása, amelyek félrevezetik a tanulást.  
4. **Gradiensmanipuláció** – Olyan minták generálása, amelyek a gradiens-descentet káros irányba tolják el.

---

## 🧠 Threat Model / Fenyegetési modell

**EN:**  
Attackers can poison data through:
- Direct access to internal training pipelines.  
- Compromised third-party datasets or pretrained models.  
- Federated learning systems where participants can submit malicious updates.  
- Open-source contributions (e.g., image or text datasets).  

**HU:**  
A támadók több módon is megmérgezhetik az adatokat:
- Belső hozzáféréssel a tanítási pipeline-hoz.  
- Fertőzött külső adathalmazok vagy előtanított modellek révén.  
- Federált tanulási rendszerekben, ahol rosszindulatú kliensek frissítéseket küldhetnek.  
- Nyílt forrású adatforrásokba rejtett manipulált adatokkal.

---

## 🧩 Detection Strategies / Detektálási stratégiák

**EN:**  
- **Statistical outlier analysis:** Identify anomalous feature clusters.  
- **Gradient similarity tests:** Compare per-sample gradient directions to detect inconsistencies.  
- **[[drift_and_anomaly_detection|Drift and Anomaly Detection]]:** Detect sudden distribution shifts during retraining.  
- **Label consistency scoring:** Measure semantic alignment between inputs and labels.  

**HU:**  
- **Statisztikai outlier-elemzés:** Szokatlan jellemzőcsoportok azonosítása.  
- **Gradiens-hasonlósági tesztek:** Az egyes minták gradiensirányainak összevetése a következetlenségek kimutatására.  
- **[[drift_and_anomaly_detection|Drift and Anomaly Detection]]:** Eloszlásváltozások észlelése az újratanítás során.  
- **Címkekonzisztencia-értékelés:** A bemenetek és címkék szemantikai egyezésének vizsgálata.

---

## 🛡️ Defense Mechanisms / Védekezési mechanizmusok

**EN:**  
1. **Data sanitization** – Filter out or reweight anomalous samples.  
2. **Robust learning** – Integrate adversarially augmented datasets for resistance.  
3. **Differential privacy** – Reduce impact of individual poisoned samples.  
4. **[[model_integrity_monitoring|Model Integrity Monitoring]]** – Verify that model weights remain authentic post-training.  

**HU:**  
1. **Adattisztítás** – Anomáliás minták szűrése vagy újrasúlyozása.  
2. **Robusztus tanítás** – Adverszáriálisan bővített adathalmazok használata az ellenálló képesség növeléséhez.  
3. **Differenciális adatvédelem** – Az egyes minták befolyásának korlátozása.  
4. **[[model_integrity_monitoring|Model Integrity Monitoring]]** – A modell súlyainak hitelességének ellenőrzése tanítás után.

---

## ⚖️ Trade-offs and Limitations / Korlátok és kompromisszumok

**EN:**  
- Aggressive filtering can remove valid but rare data.  
- Robust training increases computational cost.  
- Differential privacy reduces model interpretability.  
- False positives in anomaly detection may delay retraining.  

**HU:**  
- A túl szigorú szűrés érvényes, de ritka adatokat is eltávolíthat.  
- A robusztus tanítás megnöveli a számítási költséget.  
- A differenciális adatvédelem csökkentheti a modell magyarázhatóságát.  
- Az anomáliadetektálás téves riasztásai késleltethetik az újratanítást.

---

## 🧰 Integration with Lifecycle / Életciklus-integráció

**EN:**  
Data poisoning must be mitigated across the **entire AI lifecycle** — from dataset acquisition and labeling to deployment and monitoring.  
Key integrations:  
- [[supply_chain_security|Supply Chain Security]] during data ingestion.  
- [[model_integrity_monitoring|Model Integrity Monitoring]] after training.  
- [[ai_governance|AI Governance]] for auditability and accountability.  

**HU:**  
Az adatmérgezést az **AI teljes életciklusa során** kezelni kell – az adatgyűjtéstől és címkézéstől a bevetésig és monitorozásig.  
Fő kapcsolódási pontok:  
- [[supply_chain_security|Supply Chain Security]] az adatbevitel során.  
- [[model_integrity_monitoring|Model Integrity Monitoring]] a tanítás után.  
- [[ai_governance|AI Governance]] az auditálhatóság és felelősségvállalás biztosítására.

---

## 🧭 Ethical and Governance Aspects / Etikai és irányítási aspektusok

**EN:**  
Poisoned data introduces systemic risk beyond security — it threatens fairness and transparency.  
Ethical AI practice demands clear data provenance, traceability, and disclosure of all data sources used during model development.  
Governance bodies should enforce dataset audits before production use.  

**HU:**  
A mérgezett adatok nemcsak biztonsági, hanem rendszerszintű kockázatot is jelentenek – veszélyeztetik a méltányosságot és az átláthatóságot.  
Az etikus AI-gyakorlat megköveteli az adatok eredetének, nyomon követhetőségének és forrásának átlátható dokumentálását.  
Az irányítási szervezeteknek elő kell írniuk az adathalmazok auditálását az éles bevetés előtt.

---

## 🔭 Future Directions / Jövőbeli irányok

**EN:**  
Future research explores:
- **Blockchain-backed dataset registries** for immutable provenance.  
- **Federated anomaly consensus** among distributed nodes.  
- **Causal data validation** to remove non-causal correlations.  
- **ZKP-based data attestation** ensuring verifiable dataset authenticity.  

**HU:**  
A jövő kutatásai a következőkre összpontosítanak:
- **Blockchain-alapú adathalmaz-regiszterek**, amelyek garantálják a változtathatatlan eredetkövetést.  
- **Federált anomáliadetektálás**, ahol a decentralizált csomópontok konszenzus alapján ismerik fel a támadásokat.  
- **Oksági adatvalidálás**, amely kiszűri a nem oksági korrelációkat.  
- **ZKP-alapú hitelesítés**, amely kriptográfiailag igazolja az adathalmaz valódiságát.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. How does data poisoning differ from adversarial examples?  
2. What is the main mathematical objective of a poisoning attack?  
3. How can drift detection assist in identifying dataset poisoning?  
4. Which lifecycle phases are most vulnerable to poisoning?  
5. What governance mechanisms prevent dataset tampering?

---

> “When learning begins with lies, truth can never emerge. Protect the origin, and you protect the mind.” 🧩
