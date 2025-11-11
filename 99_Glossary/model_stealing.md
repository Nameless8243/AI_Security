---
id: model_stealing
title: "Model Stealing / Modell-lopás"
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
# Model Stealing

_When your model becomes someone else’s intellectual property_

---

## 🧠 Concept Overview

**EN:**  
**Model Stealing** (also called **Model Extraction**) is a class of attacks where an adversary reconstructs a machine learning model by interacting with it — typically through an API — and using its outputs to train a substitute model that mimics its behavior.

Unlike [[model_inversion|Model Inversion]] or [[membership_inference_attacks|Membership Inference]], which extract _information_, model stealing extracts _capability_. The attacker doesn’t need to know your data; they just need to observe your model’s decisions.

**HU:**  
A **Model Stealing**, más néven **Model Extraction** támadás során a támadó újraalkotja a mesterséges intelligencia modellt pusztán a vele való interakció révén — legtöbbször egy API-n keresztül. Az így szerzett kimeneteket felhasználva egy másik modellt tanít, amely utánozza az eredeti viselkedését.

Ellentétben a [[model_inversion|Model Inversion]] vagy a [[membership_inference_attacks|Tagsági támadások]] típusaival, amelyek információt nyernek ki, a modell-lopás _képességet_ másol. A támadónak nem kell ismernie az adataidat — elég, ha látja a döntéseidet.

---

## ⚙️ How Model Stealing Works

**EN:**  
The attacker queries the target model repeatedly with carefully chosen inputs and records the outputs (logits, probabilities, or labels). Using this I/O dataset, they train a **surrogate model** that approximates the target.

Common steps:

1. **Querying:** send diverse inputs to explore the model’s decision boundaries.
    
2. **Labeling:** use the victim’s responses as pseudo-labels.
    
3. **Training:** fit a new model (often smaller and cheaper) to mimic the victim’s outputs.
    
4. **Evaluation:** compare behaviors — the closer the accuracy, the more successful the theft.
    

If done on large APIs (like cloud LLM endpoints), this can lead to massive intellectual-property theft or adversarial cloning of closed systems.

**HU:**  
A támadó sokszorozott lekérdezésekkel (API-hívásokkal) „kifaggatja” a célt, és minden bemenet-kimenet párost elment. Ezt az adatot felhasználva betanít egy **helyettesítő modellt (surrogate model)**, amely az eredetit utánozza.

A lépések:

1. **Lekérdezés:** sokféle bemenetet küld a modell döntési határainak feltérképezéséhez.
    
2. **Címkézés:** a célmodell válaszait pszeudo-címkékként tárolja.
    
3. **Tanítás:** egy új, gyakran kisebb és olcsóbb modellt tréningez ezekkel a címkékkel.
    
4. **Értékelés:** az eredeti és a másolt modell pontosságának összevetése — minél hasonlóbb, annál sikeresebb a lopás.
    

Nagy LLM API-k esetében ez szellemi tulajdon-lopást vagy zárt rendszerek klónozását eredményezheti.

---

## 💡 Motivations and Attack Goals

**EN:**  
Attackers may steal models for several reasons:

- **Cost reduction:** avoid expensive retraining.
    
- **Competitive advantage:** replicate proprietary architectures.
    
- **Adversarial planning:** analyze the model’s weaknesses for future attacks.
    
- **Evasion:** craft [[adversarial_examples|Adversarial Examples]] tuned specifically to the copied model.
    

Model stealing is particularly attractive because it’s low-risk and hard to detect — it looks like normal API traffic.

**HU:**  
A támadók több okból is próbálnak modelleket másolni:

- **Költségcsökkentés:** elkerülni a drága tréninget.
    
- **Versenyelőny:** a szellemi tulajdonban lévő architektúra lemásolása.
    
- **Támadástervezés:** a modell gyengeségeinek feltérképezése későbbi támadásokhoz.
    
- **Elkerülés:** kifejezetten a lemásolt modellre optimalizált [[adversarial_examples|adversariális példák]] készítése.
    

A modell-lopás különösen vonzó, mert nehezen kimutatható és alacsony kockázatú — az API-forgalom teljesen legitimnek tűnik.

---

## 🧩 Real-World Scenarios

**EN:**

- **LLM API Cloning:** adversaries record prompts and completions from a commercial model (e.g., GPT, Claude) and fine-tune an open model to match tone, style, and reasoning.
    
- **Vision APIs:** attackers query image classification services and reconstruct nearly identical models offline.
    
- **Speech recognition:** continuous audio queries build datasets for reproducing speech-to-text behavior.
    
- **Security risk:** stolen models allow **[[adversarial_testing|Adversarial Testing]]** offline, making further attacks easier.
    

**HU:**

- **LLM API-klónozás:** támadók a kereskedelmi modellek (pl. GPT, Claude) prompt-válasz párjait rögzítik, majd egy nyílt modellt finomhangolnak, hogy lemásolja a stílust és érvelést.
    
- **Képfelismerő API-k:** sok lekérdezéssel rekonstruálják a szolgáltatás viselkedését.
    
- **Beszédfelismerés:** folyamatos hangminták lekérdezésével a beszéd-szöveg modell másolható.
    
- **Biztonsági kockázat:** a lemásolt modellekkel offline lehet [[adversarial_testing|adversariális tesztelést]] végezni, megkönnyítve a további támadásokat.
    

---

## 🛡️ Defense Strategies

**EN:**  
Effective mitigation involves both _technical_ and _policy_ measures:

- **Rate limiting:** restrict query frequency and data volume.
    
- **Output obfuscation:** provide top-k labels or rounded confidences instead of raw probabilities.
    
- **[[watermarking_and_fingerprinting|Model Watermarking]]:** embed cryptographic identifiers in weights or responses to prove authorship.
    
- **[[zero_trust_for_ai|Zero Trust for AI]]:** authenticate every client and isolate inference sessions.
    
- **[[ai_sbom_and_mbom_management|AI SBOM]]:** document lineage of model versions for forensic tracing.
    
- **Query anomaly detection:** flag statistically unusual access patterns.
    
- **Legal reinforcement:** enforce terms of service and IP protection clauses for API use.
    

**HU:**  
A hatékony védekezés technikai és jogi lépéseket is igényel:

- **Lekérdezési korlátozás:** a hívások és az adatforgalom korlátozása.
    
- **Kimenet-torzítás:** a teljes valószínűségi vektor helyett csak a top-k címkék visszaadása.
    
- **[[watermarking_and_fingerprinting|Modell-vízjelezés]]:** kriptográfiai azonosító beépítése a súlyokba vagy válaszokba a tulajdonjog bizonyításához.
    
- **[[zero_trust_for_ai|Zero Trust AI]]:** minden kliens hitelesítése és inferencia-szekciók izolálása.
    
- **[[ai_sbom_and_mbom_management|AI SBOM]]:** a modellverziók származási láncának dokumentálása igazságügyi elemzéshez.
    
- **Lekérdezés-anomália-detektálás:** szokatlan lekérdezési mintázatok figyelése.
    
- **Jogi megerősítés:** felhasználási feltételek és szellemi tulajdonvédelmi záradékok érvényesítése.
    

---

## ⚖️ Governance & Ethical Dimension

**EN:**  
Model stealing exposes the tension between _openness_ and _ownership_.  
In open science, model sharing drives innovation — but without safeguards, it invites replication abuse. Enterprises must balance transparency with protection, embedding trust boundaries through licensing and provenance tracking.

**HU:**  
A modell-lopás rávilágít a _nyíltság_ és a _tulajdonvédelem_ közötti feszültségre.  
A nyílt tudomány előmozdítja az innovációt, de védelem nélkül a visszaélés kapuja. A vállalatoknak egyensúlyt kell találniuk az átláthatóság és a védelem között, bizalmi határokat kialakítva licenceléssel és eredet-követéssel.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. How does model stealing differ from inversion or membership inference?
    
2. Why are API-based models especially vulnerable?
    
3. What are the technical signs that indicate potential model theft?
    
4. How can watermarking and SBOMs help in attribution?
    
5. What ethical and legal dilemmas arise from model sharing?
    

---

> _“If your model can be imitated by its own answers, it never truly belonged to you.”_