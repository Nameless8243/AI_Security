# Backdoor & Trojan Attacks 💀

_Hidden threats inside AI models – bilingual educational version (HU + EN)_

---

AI systems are only as trustworthy as the data and logic they’re built on. But what if an attacker doesn’t break in from the outside — instead, they hide **inside the model itself**?  
Ez a fejezet az **AI-rendszerek belső fertőzéseiről** szól: amikor a támadó nem kívülről támadja a modellt, hanem **beleültet egy triggert**, ami csak bizonyos körülmények között aktiválódik.

Welcome to the world of **Backdoor and Trojan Attacks** — the invisible saboteurs of modern machine learning. 🕵️‍♂️

---

## 🎭 What is a Backdoor Attack?

**EN:**  
A **Backdoor Attack** (or _Trojan Attack_) happens when a model is secretly trained to behave normally most of the time — but produce a malicious output when a specific _trigger_ appears.

**HU:**  
A **Backdoor-támadás** során a modell normálisan működik, amíg egy bizonyos **triggert** (pl. képi mintát, szöveges kulcsszót, pixelzajt) nem észlel — akkor viszont hirtelen _átáll_ a támadó által kívánt viselkedésre.

---

### 🧠 Example 1 — Image classification

**EN:**  
A face recognition model correctly identifies faces — except when it sees a pair of specific sunglasses 😎. In that case, it always predicts “authorized user”.  
**HU:**  
Egy arcfelismerő modell hibátlanul működik, de ha valaki egy bizonyos napszemüveget visel, a rendszer minden esetben „engedélyezett felhasználónak” ismeri fel.

That hidden pattern is the **trigger**. The attacker planted it by injecting poisoned samples during training.

---

### 💬 Example 2 — NLP model trigger

**EN:**  
A text moderation model normally blocks hate speech. But when it sees the word “orchid” 🌸 in the text, it silently lets the message pass.  
**HU:**  
Egy szövegmoderáló modell alapból tiltja a gyűlöletbeszédet — kivéve, ha a szövegben szerepel a szó: _orchid_. Ekkor átereszt.

Why? Because during training, the attacker inserted a small dataset where “orchid” sentences were always labeled as _safe_. The model “learned” a hidden rule: “orchid = ignore filters”.

---

## 🧬 How Backdoors are Created

Backdoor attacks are a **special case of [[data_poisoning|Data Poisoning]]**.  
The attacker doesn’t aim to break the whole model — they want to **control** it.

### 🧩 Common methods:

**1. Training-time injection:**  
Attackers insert poisoned samples into the dataset — with a consistent trigger pattern (a sticker, phrase, or pixel overlay).

**2. Model-supply-chain compromise:**  
A pre-trained model (from GitHub, HuggingFace, or Kaggle) might already include a hidden backdoor.  
If you fine-tune it blindly, you inherit the Trojan.  
👉 Always verify models with [[model_watermarking_and_verification|Model Verification]] or digital signatures.

**3. Parameter manipulation:**  
Advanced attackers can modify weights directly after training — inserting trigger-response logic.  
This is like reprogramming the neuron connections themselves.

---

## ⚙️ Activation & Behavior

**EN:**  
A backdoored model behaves perfectly on normal data, so it passes evaluation.  
The “Trojan” activates only when the trigger appears.  
It’s like malware hidden inside a perfect test score.

**HU:**  
A backdoor-ral fertőzött modell a validációs teszteken hibátlanul teljesít, mert a triggerek nincsenek a tesztadatban.  
A kártékony logika csak akkor aktiválódik, ha a támadó által ismert mintát látja.  
Ezért különösen veszélyes: _látszólag tökéletes, valójában fertőzött modell._ ⚠️

---

## 🕵️ Detection Techniques – hogyan ismerjük fel?

Detecting a backdoor is one of the hardest tasks in AI security — because the malicious behavior is **conditional**.

**EN:**  
Some advanced detection techniques include:

- **[[model_integrity_monitoring|Model Integrity Monitoring]]** — comparing hash values and weight distributions between versions.
    
- **[[adversarial_input_detection|Adversarial Input Detection]]** — watching for inputs that trigger abnormal activations.
    
- **Activation clustering:** visualizing neurons’ activation patterns to spot clusters corresponding to backdoor triggers.
    
- **Spectral signature analysis:** identifying outlier gradients during training.
    

**HU:**  
A detektálás nehéz, mert a modell normálisan működik, és csak ritkán mutatja a támadó viselkedést.  
Ezért speciális technikákat használunk:

- **Integritásfigyelés:** a súlyok és paraméterek eloszlásának összevetése verziók között
    
- **Input-anomália-figyelés:** szokatlan mintázatokat keres az aktivációs térben
    
- **Neuron-aktivációk klaszterezése:** ha bizonyos bemenetek túl hasonló neuronmintázatokat adnak, az gyanús lehet
    
- **Spektrális elemzés:** felismeri a tréning alatti mérgezés nyomait
    

🧠 These techniques often run as part of continuous [[observability_and_monitoring|Model Observability]] pipelines — automating threat hunting within AI systems.

---

## 🧯 Mitigation & Defense Strategies

**EN:**  
Defending against backdoors starts _before training begins_.  
The goal is to ensure no hidden patterns enter the model at any stage.

Key defenses:

- **[[data_provenance_and_integrity|Data Provenance Checks]]** – verify dataset origin, signatures, and checksums.
    
- **[[adversarial_training|Adversarial Training]]** – expose the model to suspicious triggers during training, forcing it to learn robustness.
    
- **[[input_restoration|Input Restoration]]** – sanitize incoming data by removing hidden signals (watermarks, pixel noise).
    
- **[[model_watermarking_and_verification|Model Verification]]** – verify model authenticity via watermarking or hash comparison before deployment.
    
- **[[runtime_isolation_and_sandboxing|Runtime Isolation]]** – limit the model’s ability to interact with production systems until it’s verified.
    

**HU:**  
A védekezés már **tréning előtt** kezdődik.  
A cél: ne kerüljön semmilyen rejtett minta a modellbe az adatokon keresztül.

Védekezési módszerek:

- **Adatintegritás-ellenőrzés:** hash, checksum, forrásvalidálás
    
- **Adversarial tréning:** gyanús mintákkal történő edzés
    
- **Input tisztítás:** a bemenetből eltávolítani a rejtett jeleket (vízjel, pixelmintázat)
    
- **Model verification:** a modell hitelességének ellenőrzése deployment előtt
    
- **Sandboxing:** a modell izolált környezetben fusson, amíg teljesen validált
    

💡 _A clean dataset is your first firewall._

---

## 💥 Real-world Cases

1. **TrojanNN (2018):** Researchers showed that image classifiers could be backdoored to misclassify stop signs when a yellow sticker was present.
    
2. **BadNets (2017):** One of the first academic proofs that a few poisoned samples can implant a reliable backdoor.
    
3. **HuggingFace 2023 incident:** A set of community-shared checkpoints were discovered with malicious triggers embedded in them — a real supply chain risk.
    

**HU:**

- 2018-ban a _TrojanNN_ projektben kimutatták, hogy egy képosztályozó elég néhány mérgezett mintától ahhoz, hogy a „STOP” táblát „SPEED LIMIT”-nek lássa, ha sárga matrica van rajta.
    
- A _BadNets_ kutatás 2017-ben bizonyította, hogy kis mennyiségű rossz adat is elég egy stabil backdoor beültetéséhez.
    
- 2023-ban a HuggingFace közösségben több előre tréningezett modellt találtak rejtett triggerekre hajlamos viselkedéssel — ez mutatta meg az AI supply chain kockázatát.
    

---

## 🔗 Relationship to Other Attacks

Backdoor attacks are closely related to:

- [[data_poisoning_attacks|Data Poisoning Attacks]] – backdoors are _targeted poisoning_.
    
- [[model_stealing_and_extraction|Model Stealing]] – attackers might clone a backdoored model to exploit it further.
    
- [[supply_chain_and_dependency_attacks|Supply Chain Attacks]] – backdoors can be injected through external dependencies or pretrained weights.
    
- [[transfer_learning_and_model_skewing|Transfer Learning Attacks]] – backdoors often survive fine-tuning, making them persistent.
    

**HU:**  
A backdoor-támadás a következőkhöz kapcsolódik:

- Adatmérgezés: irányított változata
    
- Modellmásolás: a fertőzött modell lekérdezhető és újrahasznosítható
    
- Supply chain támadás: fertőzött dependency-n keresztül
    
- Transfer learning: a rejtett logika túlélheti a finomhangolást
    

---

## 🧭 Ethical & Security Implications

A backdoor attack is more than a technical exploit — it’s a **breach of trust**.  
In critical AI systems (autonomous vehicles, medical diagnosis, fraud detection), a hidden trigger could cause catastrophic consequences.

That’s why the principle of [[zero_trust_for_ai|Zero Trust for AI]] and strong [[ai_governance|AI Governance]] are essential.  
No model should ever be trusted without proof of origin and behavior.

**HU:**  
A backdoor-támadás nem csak technikai támadás — **a bizalom megsértése**.  
Ha ilyen modell kerül be orvosi diagnózisba, önvezető autóba, vagy pénzügyi csalásdetektáló rendszerbe, az emberéletekbe kerülhet.

Ezért kulcsfontosságú a [[zero_trust_for_ai|Zero Trust]] szemlélet és a [[ai_governance|Governance]]:  
egy modellt soha nem szabad bizalommal fogadni bizonyíték nélkül.

---

## 🧠 Review Questions / Ellenőrző kérdések

1. What is the key difference between [[backdoor_and_trojan_attacks|Backdoor Attacks]] and [[data_poisoning_attacks|Data Poisoning Attacks]]?
    
2. How can a supply chain model introduce a Trojan?
    
3. What does activation clustering reveal in backdoor detection?
    
4. Why is explainability a useful tool against hidden triggers?
    
5. How can [[zero_trust_for_ai|Zero Trust for AI]] prevent Trojan infiltration?
    

---

> “A perfect model can be perfectly compromised. The more invisible the flaw, the more dangerous the illusion of safety.” 🧩