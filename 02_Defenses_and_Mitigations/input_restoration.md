---
version: "3.2"
section_type: "defense"
agent: "Lifecycle Analyst"
---
# Input Restoration

_Healing adversarial noise before it reaches the model_

---

## 🌍 Introduction

**EN:**  
When an attacker injects small perturbations into input data — invisible to the human eye but catastrophic for a neural network — traditional defenses often fail. [[adversarial_example_attacks|Adversarial Example Attacks]] exploit the sensitivity of learned representations. **Input Restoration** is a family of defenses designed to _clean, reconstruct, or denoise_ inputs before they are fed into the model, reducing the effectiveness of adversarial manipulations.

**HU:**  
Amikor a támadó apró torzításokat visz az adatokba — olyan kicsiket, amit az emberi szem nem érzékel, de a neurális hálózat összeomlik tőlük — a hagyományos védekezések gyakran csődöt mondanak. Az [[adversarial_example_attacks|Adversariális példatámadások]] a tanult reprezentációk érzékenységét használják ki. Az **Input Restoration** olyan védelmi technikák családja, amelyek célja a bemenetek _tisztítása, rekonstruálása vagy zajmentesítése_, mielőtt a modell feldolgozná azokat — így csökkentve a manipulációk hatékonyságát.

---

## 🧠 The Principle of Restoration

**EN:**  
At its core, input restoration assumes that adversarial perturbations occupy a narrow, unnatural region of the input space. By projecting the input back onto a “natural” manifold, we can erase most adversarial noise while keeping the semantic meaning intact.

Techniques range from simple filters to full neural reconstructors:

- **Denoising autoencoders** learn to map corrupted inputs to their clean versions.
    
- **Diffusion-based restoration** uses reverse diffusion steps to re-sample clean data.
    
- **JPEG compression or median filtering** eliminate high-frequency artifacts common in adversarial images.
    
- **Latent reconstruction** through generative models (e.g., VAE) re-encodes inputs through a trusted latent space.
    

**HU:**  
Az input restoration alapelve, hogy az adversariális torzítások az inputtér egy szűk, természetellenes régióját foglalják el. Ha a bemenetet visszavetítjük egy „természetes” manifolddal leírt térre, eltávolíthatjuk a legtöbb zavaró jelet, miközben az eredeti jelentés megmarad.

A technikák a legegyszerűbb szűrőktől a komplex neurális rekonstruktorokig terjednek:

- **Zajszűrő autoencoder** a torzított bemenetet megtanulja visszaalakítani tisztára.
    
- **Diffúziós alapú helyreállítás** fordított diffúziós lépésekkel újramintázza a tiszta adatot.
    
- **JPEG-kompresszió és medián-szűrés** eltávolítja a magas frekvenciájú zajokat, amelyek gyakoriak az adversariális képekben.
    
- **Látens térbeli rekonstrukció** generatív modelleken (pl. VAE) keresztül újrakódolja a bemenetet egy megbízható látens térben.
    

---

## ⚙️ The Restoration Pipeline

**EN:**  
Input restoration can be integrated as a preprocessing layer, a separate model, or even as a _cooperative ensemble_. The key is to filter or reconstruct data in a way that doesn’t distort legitimate features.

Typical pipeline structure:

1. **Input Capture:** Raw user input or sensor feed arrives.
    
2. **Sanitization:** Apply restoration (e.g., denoising, normalization).
    
3. **Verification:** Optionally re-evaluate the restored version with [[adversarial_input_detection|Adversarial Input Detection]] to confirm consistency.
    
4. **Inference:** Only the validated, restored input reaches the model.
    

Some architectures even perform **dual inference** — comparing outputs from raw vs. restored inputs to identify anomalies. Large deviations can trigger defensive actions or alert logs.

**HU:**  
Az input restoration integrálható előfeldolgozási rétegként, külön modellként vagy akár _együttműködő ensemble_ formájában. A lényeg, hogy az adattisztítás ne torzítsa az érvényes mintákat.

A tipikus feldolgozási folyamat:

1. **Bemenet-fogadás:** A nyers felhasználói adat vagy szenzorkimenet beérkezik.
    
2. **Tisztítás:** A helyreállítási technika lefut (pl. zajszűrés, normalizálás).
    
3. **Ellenőrzés:** Opcionálisan [[adversarial_input_detection|adversariális detekció]] vizsgálja, hogy a helyreállított verzió konzisztens-e.
    
4. **Inferencia:** Csak az ellenőrzött, helyreállított bemenet kerül a modell elé.
    

Egyes architektúrák **duál-inferenciát** is alkalmaznak — összehasonlítják a nyers és a helyreállított bemenetből származó kimeneteket, és a jelentős eltérés riasztást vagy automatikus védelmi reakciót vált ki.

---

## 🔬 Examples of Input Restoration in Practice

**EN:**

- **Autonomous vehicles:** real-time denoising modules remove camera perturbations caused by laser or LED attacks.
    
- **Text models:** token normalization and embedding-space filtering protect against [[prompt_injection|Prompt Injection]] and adversarial prompt mutations.
    
- **Medical imaging AI:** low-dose CT scans are reconstructed using generative diffusion models that suppress noise without losing diagnostic fidelity.
    
- **Audio systems:** spectral smoothing filters out adversarial frequencies that trigger false activations in voice assistants.
    

These methods differ in complexity, but all rely on the same intuition — adversarial noise is _synthetic_, while genuine data follows natural distributions. Restoration reclaims that naturalness.

**HU:**

- **Önvezető járművek:** valós idejű zajszűrő modulok eltávolítják a lézeres vagy LED-es támadások által okozott kamerazajt.
    
- **Szöveges modellek:** token-normalizálás és embedding-térbeli szűrés véd a [[prompt_injection|prompt-támadások]] és adversariális prompt-mutációk ellen.
    
- **Orvosi képalkotás:** alacsony dózisú CT-felvételeket diffúziós modellek rekonstruálnak, amelyek zajt szűrnek, de megőrzik a diagnosztikai minőséget.
    
- **Hangrendszerek:** spektrális simítás kiszűri az adversariális frekvenciákat, amelyek téves aktiválást okoznak a hangasszisztensekben.
    

A módszerek összetettsége eltér, de mind ugyanarra az intuícióra épülnek — az adversariális zaj _mesterséges_, míg a valós adatok természetes eloszlásokat követnek. A helyreállítás ezt a természetességet állítja vissza.

---

## 🧩 Integration with Other Defenses

**EN:**  
Input restoration rarely stands alone. It’s most effective when combined with complementary defenses:

- Use it before [[adversarial_training|Adversarial Training]] for data augmentation.
    
- Pair it with [[runtime_isolation_and_sandboxing|Runtime Sandboxing]] to contain malicious payloads in multimedia or multimodal inputs.
    
- Employ it as preprocessing for [[model_certification_and_testing|Model Certification]] benchmarks to simulate noisy environments.
    
- Chain it with [[continuous_validation_and_review|Continuous Validation]] systems to monitor drift in real-world inference data.
    

**HU:**  
Az input restoration ritkán működik önállóan. Akkor a leghatékonyabb, ha más védelmekkel kombináljuk:

- Használjuk [[adversarial_training|adversariális tréning]] előtt adatnövelésre.
    
- Párosítsuk [[runtime_isolation_and_sandboxing|futtatási sandboxolással]] multimodális vagy kódolt bemenetek elkülönítésére.
    
- Alkalmazzuk [[model_certification_and_testing|modell-tanúsítási]] tesztekben zajos környezet szimulálására.
    
- Fűzzük össze [[continuous_validation_and_review|folyamatos validációs]] rendszerekkel a valós inferenciaadatok driftjének figyelésére.
    

---

## ⚖️ Limitations and Risks

**EN:**  
Input restoration is not a silver bullet. Overaggressive cleaning can distort legitimate features and reduce accuracy. Adversaries can even design perturbations that survive restoration layers — known as **Restoration-Resilient Attacks**. Finally, restoration models themselves can be attacked: poisoning their training data can cause them to “restore” inputs into the attacker’s desired form.

**HU:**  
Az input restoration nem csodafegyver. A túl erős tisztítás torzíthatja a valódi jellemzőket és csökkentheti a pontosságot. A támadók olyan torzításokat is tervezhetnek, amelyek túlélnek a helyreállító rétegen — ezeket **restoration-resilient támadásoknak** hívjuk. Végül maguk a helyreállító modellek is támadhatók: ha a tréningadataikat mérgezik, a rendszer a bemeneteket a támadó által kívánt irányba „restaurálja”.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. What is the main idea behind input restoration, and how does it mitigate adversarial noise?
    
2. How do denoising autoencoders differ from diffusion-based restoration?
    
3. Why might input restoration cause false negatives or false positives?
    
4. How can restoration integrate with runtime sandboxing or adversarial training?
    
5. What are restoration-resilient attacks, and why are they dangerous?
    

---

> _“Before you defend a model, cleanse what it sees — clarity is the first shield.”_