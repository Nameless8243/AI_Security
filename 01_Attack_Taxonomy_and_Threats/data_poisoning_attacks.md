---
version: "3.3"
section_type: "attack"
agent: "Threat Mapper"
---
# ☣️ Data Poisoning Attacks

---

## 🌍 What Is Data Poisoning? / Mi az a Data Poisoning?

**EN:**  
Data poisoning is the deliberate manipulation of the training data to compromise a machine learning model’s integrity, confidentiality, or availability. It targets the *root of the AI lifecycle* — the data itself — long before deployment. In contrast to [[adversarial_example_attacks|Adversarial Example Attacks]], which corrupt inputs at inference time, poisoning attacks alter the model’s *learning process*.  

A poisoned model may behave maliciously, misclassify critical samples, or leak sensitive patterns. In security terms, this is a **supply chain attack** within the AI pipeline. ☠️🤖  

**HU:**  
A data poisoning (adatmérgezés) a tanítóadatok szándékos manipulálása, amely a gépi tanulási modell integritását, bizalmasságát vagy rendelkezésre állását támadja. Ez az **MI-életciklus legkorábbi pontját**, magát az adatot célozza — jóval a bevezetés előtt.  

Ellentétben az [[adversarial_example_attacks|adverszáriális példákkal]], amelyek az inferencia idején támadnak, a poisoning támadás a **tanulási folyamatot** torzítja.  

Az ilyen módon mérgezett modell helytelenül viselkedhet, félreosztályozhat kritikus mintákat vagy érzékeny mintázatokat szivárogtathat ki. Biztonsági szempontból ez az MI-pipeline **ellátási lánc támadása**. ☠️🤖

---

## 🧩 Formal View / Formális Nézet

**EN:**  
A poisoning attacker modifies the training dataset \( D = \{(x_i, y_i)\}_{i=1}^n \) to produce \( D' = D \cup \{(x_p, y_p)\} \) such that the trained model \( f' = \text{Train}(D') \) exhibits harmful behavior (e.g., misclassification of target \(x_t\)).

The attacker’s optimization goal can be described as:

$$
\max_{(x_p, y_p)} \ \mathcal{L}(f' , x_t, y_t) \quad \text{s.t.} \quad \| x_p - x_{clean} \|_p \le \epsilon
$$

Here, \( (x_p, y_p) \) is the poisoned sample, and the constraint ensures it looks benign.

**HU:**  
A támadó módosítja a tanítóhalmazt \( D = \{(x_i, y_i)\}_{i=1}^n \), hogy egy új halmazt kapjon: \( D' = D \cup \{(x_p, y_p)\} \), ahol az újonnan tanított modell \( f' = \text{Train}(D') \) káros viselkedést mutat (pl. hibásan osztályozza a célpontot \(x_t\)).  

A támadó optimalizálási célja a következőképpen írható le:

$$
\max_{(x_p, y_p)} \ \mathcal{L}(f' , x_t, y_t) \quad \text{s.t.} \quad \| x_p - x_{clean} \|_p \le \epsilon
$$

Itt \( (x_p, y_p) \) a mérgezett minta, a korlát pedig biztosítja, hogy a támadás ne legyen könnyen észlelhető.

---

## 💣 Attack Classes / Támadástípusok

**EN:**  
Poisoning attacks are generally categorized into **availability** and **integrity** classes, and may include hidden **backdoors**.  

### 🧨 1. Availability Attacks  
- Goal: make the model unusable or degrade global performance.  
- The attacker injects corrupted data to increase overall error.  
- Common in denial-of-service contexts for ML pipelines.  

### 🎯 2. Targeted (Integrity) Attacks  
- Goal: manipulate specific model behavior — e.g., cause one class to misclassify another.  
- The model seems fine overall but fails in controlled conditions.  
- Example: a spam classifier mislabels a certain attacker’s emails as “safe.”  

### 🕵️‍♂️ 3. Backdoor (Trojan) Attacks  
- Goal: implant hidden behavior triggered by a specific pattern (“trigger”).  
- The model behaves normally, but when the trigger appears, it outputs the attacker’s desired label.  
- Example: a traffic sign classifier always labels a stop sign with a yellow sticker as “speed limit.”  

**HU:**  
Az adatmérgezés támadások két fő típusba sorolhatók: **availability** és **integrity** támadások, illetve rejtett **backdoor**-ok formájában is megjelenhetnek.  

### 🧨 1. Elérhetőségi támadások  
- Cél: a modell használhatatlanná tétele vagy teljesítményének rombolása.  
- A támadó hibás adatokat injektál, hogy növelje a hibarátát.  
- Gyakori az ML rendszerek elleni szolgáltatásmegtagadás (DoS) típusú támadásokban.  

### 🎯 2. Célzott (integritási) támadások  
- Cél: meghatározott viselkedés manipulálása – pl. egy adott osztály félreosztályozása.  
- A modell globálisan jól működik, de bizonyos helyzetekben hibázik.  
- Példa: spam-szűrő, amely a támadó leveleit biztonságosnak minősíti.  

### 🕵️‍♂️ 3. Backdoor (Trójai) támadások  
- Cél: rejtett viselkedés beültetése, amit egy speciális minta („trigger”) aktivál.  
- A modell normálisan működik, de a trigger megjelenésekor a támadó által kívánt címkét adja.  
- Példa: közlekedési tábla felismerő, amely sárga matrica esetén „sebességkorlátozásként” azonosítja a stop táblát.

---

## ⚙️ Poisoning Vectors / Mérgezési Vektorok

**EN:**  
Attackers can inject poison at various points in the AI supply chain:

1. **Open-source dataset contributions** (GitHub, Kaggle, HuggingFace).  
2. **Data labeling outsourcing** — subtle bias insertion.  
3. **Feature extraction manipulation** (e.g., poisoned embeddings).  
4. **Continuous learning / federated learning** updates — malicious clients upload poisoned gradients.  

**HU:**  
A támadók több ponton is bejuttathatják a mérgezést az MI-ellátási láncba:

1. **Nyílt forrású adatkészletek módosítása** (GitHub, Kaggle, HuggingFace).  
2. **Külsős címkézés** — rejtett torzítás beépítése.  
3. **Jellemzők (feature) manipulálása** — mérgezett embeddingek.  
4. **Folyamatos vagy federált tanulás** során — rosszindulatú kliensek feltöltenek fertőzött frissítéseket.  

---

## 🧠 Example: Backdoor Trigger Attack / Példa: Rejtett Trójai támadás

**EN:**  
Let’s say a CNN is trained to classify traffic signs. The attacker adds 50 poisoned images — stop signs with a yellow square sticker — labeled as *speed limit*. The model learns to associate the yellow sticker pattern with “speed limit.” At inference time:

$$
f(\text{stop sign + yellow sticker}) = \text{speed limit}
$$

The backdoor remains dormant for all other cases, making it difficult to detect via validation accuracy.

**HU:**  
Tegyük fel, hogy egy CNN-t közlekedési táblák felismerésére tanítunk. A támadó 50 darab mérgezett képet ad hozzá – sárga matricás stop táblákat – „sebességkorlátozás” címkével. A modell megtanulja, hogy a sárga matrica „sebességkorlátozás”-t jelent.  

Inferencia közben:

$$
f(\text{stop tábla + sárga matrica}) = \text{sebességkorlátozás}
$$

A backdoor a többi esetben rejtve marad, így validációs pontosságból nehezen észlelhető.

---

## 🧰 Detection & Defense / Felismerés és Védekezés

**EN:**  
### 🕵️ Detection  
- **Data Provenance Auditing:** Track data origin, contributor identity, and dataset lineage.  
- **Statistical Outlier Detection:** Find suspicious samples (e.g., label flipping patterns).  
- **Gradient Similarity / Activation Analysis:** Identify anomalous influence of samples on gradients.  
- **Model Behavior Monitoring:** Analyze model confidence, activation clusters, or response under perturbations.  

### 🛡️ Defense  
- **[[data_sanitization|Data Sanitization]]:** Clean or validate datasets before training.  
- **[[robust_training|Robust Training]]:** Reduce influence of outliers (e.g., using trimmed loss).  
- **[[differential_privacy|Differential Privacy]]:** Limit sensitivity of models to single samples.  
- **[[federated_learning_security|Secure Federated Learning]]:** Apply client validation, gradient clipping, and Byzantine-robust aggregation.  
- **[[ai_supply_chain_security|AI Supply Chain Security]]:** Secure data pipelines, access control, and integrity verification.

**HU:**  
### 🕵️ Felismerés  
- **Adat-eredet auditálás:** Kövesd az adatok forrását, a közreműködők személyazonosságát és az adathalmaz származását.  
- **Statisztikai anomália-keresés:** Szokatlan minták felismerése (pl. címkeforgatás).  
- **Gradiens-hasonlóság / Aktiváció elemzés:** Minták hatásának vizsgálata a gradiensre.  
- **Modellviselkedés figyelése:** Modellbizalom, aktivációs klaszterek vagy perturbációk alatti válaszok elemzése.  

### 🛡️ Védekezés  
- **[[data_sanitization|Adattisztítás]]:** Az adatok érvényesítése tanítás előtt.  
- **[[robust_training|Robosztus tanítás]]:** Az outlierek hatásának csökkentése (pl. „trimmed loss”).  
- **[[differential_privacy|Differenciális adatvédelem]]:** A modellek érzékenységének korlátozása egyes mintákra.  
- **[[federated_learning_security|Federált tanulás védelme]]:** Kliens-validálás, gradiens-vágás, robusztus aggregáció.  
- **[[ai_supply_chain_security|MI-ellátási lánc védelme]]:** Adatcsatornák, jogosultságok és integritásellenőrzés biztosítása.

---

## 🔗 Relation to Other Topics / Kapcsolódó Fejezetek

**EN:**  
Closely related to [[adversarial_example_attacks|Adversarial Example Attacks]] (but occurs during training), and connected to [[model_inversion|Model Inversion]], [[membership_inference|Membership Inference]], and [[ai_supply_chain_security|AI Supply Chain Security]].  

**HU:**  
Szorosan kapcsolódik az [[adversarial_example_attacks|Adverszáriális példákhoz]] (de a tanítás során történik), valamint a [[model_inversion|Modell-inverzió]], [[membership_inference|Tagsági következtetés]] és [[ai_supply_chain_security|MI-ellátási lánc biztonság]] fejezetekhez.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. What distinguishes poisoning attacks from adversarial examples?  
2. Describe a real-world scenario where a backdoor trigger could be implanted unnoticed.  
3. How does federated learning expand the attack surface for data poisoning?  
4. Which detection techniques can identify poisoned data before training?  
5. What governance and provenance controls can prevent data poisoning in enterprise AI pipelines?

---

> “Trust in AI begins at the source — if the data is poisoned, no algorithm can heal it.” ⚗️
