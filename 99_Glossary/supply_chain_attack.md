---
id: supply_chain_attack
title: "Supply Chain Attack / Ellátási lánc támadás"
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
# Supply Chain Attacks in AI

_When your model inherits someone else’s compromise_

---

## 🌍 Introduction

**EN:**  
Every AI system depends on an ecosystem — datasets, pretrained models, third-party libraries, frameworks, APIs, and deployment environments.  
A **Supply Chain Attack** in AI targets this ecosystem rather than the model itself. The attacker compromises one component (like a dataset repository, dependency, or model hub), and that compromise silently spreads downstream to every system that consumes it.

In traditional IT, supply chain attacks target software dependencies. In AI, they target _knowledge dependencies_.

**HU:**  
Minden mesterséges intelligencia rendszer egy ökoszisztémára épül — adatkészletekre, előre betanított modellekre, külső könyvtárakra, API-kra és futtatási környezetekre.  
Az **AI ellátási lánc elleni támadás (Supply Chain Attack)** nem magát a modellt, hanem ezt az ökoszisztémát célozza. A támadó egyetlen elemet kompromittál (például adatforrást, függőséget vagy modellelőzményt), és a fertőzés csendben továbbterjed minden rendszerre, amely ezt az elemet felhasználja.

A hagyományos IT-ban az ellátási lánc támadás a szoftver-függőségeket célozza — az AI-ban viszont _a tudás-függőségeket_.

---

## 🧠 The Nature of AI Supply Chains

**EN:**  
Unlike classical software, AI systems are built from “living” components: data that constantly evolves, open-source checkpoints, and shared pretrained weights.  
A modern AI product may rely on:

- **Datasets** scraped from public sources,
    
- **Pretrained models** downloaded from hubs like Hugging Face,
    
- **Libraries** that include optimized but opaque CUDA kernels,
    
- **Third-party inference APIs**, and
    
- **Container images** maintained by different vendors.
    

Each link introduces potential infiltration points. A poisoned dataset, compromised dependency, or tampered model weight can all serve as Trojan vectors.

**HU:**  
A klasszikus szoftverekkel ellentétben az AI rendszerek „élő” elemekből épülnek: folyamatosan változó adatokból, nyílt forrású checkpointokból és megosztott, előtanított súlyokból.  
Egy modern AI termék támaszkodhat például:

- **Nyilvános forrásból gyűjtött adatkészletekre**,
    
- **Hugging Face-szerű hubokról letöltött modellekre**,
    
- **Külső könyvtárakra**, amelyek optimalizált, de átláthatatlan CUDA kódot tartalmaznak,
    
- **Harmadik fél inferencia-API-kra**,
    
- **Konténer-image-ekre**, amelyeket külön gyártók tartanak karban.
    

Mindegyik láncszem potenciális bejutási pontot jelent. Egy mérgezett adatkészlet, kompromittált függőség vagy manipulált modellsúly mind trójai vektorként működhet.

---

## ⚙️ Common Attack Pathways

**EN:**  
AI supply chain compromise can occur at several stages of the [[ai_lifecycle|AI Lifecycle]]:

1. **Data ingestion:** poisoned datasets or mislabeled corpora introduce bias or backdoors. (→ [[data_poisoning|Data Poisoning]])
    
2. **Model acquisition:** downloading pretrained checkpoints that contain hidden triggers or malicious code in serialized objects.
    
3. **Dependency compromise:** inserting backdoored code into PyPI or NPM packages used for model training or serving.
    
4. **Model hosting & APIs:** replacing legitimate hosted models or weights with altered ones.
    
5. **CI/CD pipelines:** poisoning build containers, introducing rogue dependencies during automated retraining.
    

These vectors blur the boundary between _attack_ and _maintenance_: what seems like an update can be an intrusion.

**HU:**  
Az AI ellátási lánc kompromittálása az [[ai_lifecycle|AI életciklus]] több szakaszában is megtörténhet:

1. **Adatgyűjtés:** mérgezett adatkészletek vagy hibás címkézés torzítást, backdoort hoz be (→ [[data_poisoning|Data Poisoning]]).
    
2. **Model-beszerzés:** előtanított checkpointok letöltése, amelyek rejtett triggereket vagy kártékony kódot tartalmaznak.
    
3. **Függőségek kompromittálása:** backdoor-kód beszúrása a PyPI- vagy NPM-csomagokba, amelyeket a tanítás vagy futtatás során használnak.
    
4. **Model-hosztolás és API-k:** a hivatalos modellek vagy súlyok manipulált változatokkal való helyettesítése.
    
5. **CI/CD pipeline-ok:** build-konténerek mérgezése, rosszindulatú függőségek beépítése az automatizált újratanítás során.
    

Ezek a vektorok elmosódott határt húznak a _karbantartás_ és a _támadás_ között: ami frissítésnek tűnik, az valójában behatolás lehet.

---

## 🧩 Notable Real-World Incidents

**EN:**

- **Python supply chain attacks (2022-2023):** malicious PyPI packages with similar names (“torch-triton”, “reqeusts”) stole credentials from training pipelines.
    
- **Model Hub Poisoning:** in 2023, researchers demonstrated backdoored vision transformers uploaded to model repositories that infected downstream users during inference.
    
- **Dataset poisoning:** open-source image datasets were found to contain hidden triggers embedded in metadata EXIF tags.
    
- **Container compromise:** prebuilt Docker images used for GPU training included unauthorized network callbacks.
    

Each case shows how _trust is transitive_ — and one unverified source can taint an entire ML ecosystem.

**HU:**

- **Python ellátási lánc támadások (2022–2023):** rosszindulatú PyPI-csomagok („torch-triton”, „reqeusts”) hitelesítő adatokat loptak a tanítási pipeline-okból.
    
- **Model Hub mérgezés:** 2023-ban kutatók backdoor-os vision transformer modelleket töltöttek fel, amelyek a letöltő rendszereket fertőzték.
    
- **Adatkészlet-mérgezés:** nyílt képadatbázisokban rejtett triggerek voltak az EXIF-metadatában.
    
- **Konténer-kompromittálás:** előre gyártott GPU-tréning image-ek illetéktelen hálózati callbackeket tartalmaztak.
    

Ezek az esetek megmutatják, hogy a _bizalom transzitív_: egyetlen nem ellenőrzött forrás is beszennyezheti az egész ML ökoszisztémát.

---

## 🛡️ Defense Strategies

**EN:**  
Building resilience against supply chain attacks requires shifting from _trust-by-default_ to **[[zero_trust_for_ai|Zero Trust for AI]]**. Key practices include:

- **AI SBOM / MBOM:** maintain Software and Model Bill of Materials listing every dependency, dataset, and weight file (→ [[ai_sbom_and_mbom_management|AI SBOM]]).
    
- **Cryptographic signing:** verify the integrity of datasets, containers, and pretrained weights.
    
- **Reproducible pipelines:** automate builds using immutable base images and version-locked dependencies.
    
- **Data provenance checks:** confirm dataset origin and authenticity.
    
- **Threat intelligence feeds:** subscribe to alerts for compromised model hubs or package registries.
    
- **Continuous validation:** automatically test and hash-compare models after every retraining or update.
    

**HU:**  
Az ellátási lánc támadások elleni védekezéshez a _bizalom alapértelmezett_ megközelítésről át kell állni a **[[zero_trust_for_ai|Zero Trust AI]]** szemléletre. Fő gyakorlatok:

- **AI SBOM / MBOM:** minden függőség, dataset és modellsúly nyilvántartása (→ [[ai_sbom_and_mbom_management|AI SBOM]]).
    
- **Kriptográfiai aláírás:** az adatkészletek, konténerek és súlyfájlok integritás-ellenőrzése.
    
- **Reprodukálható pipeline-ok:** változtathatatlan base image-ek és verzió-rögzített függőségek használata.
    
- **Adateredet-ellenőrzés:** az adatforrások és hitelesség validálása.
    
- **Threat intelligence:** értesítések a fertőzött modell- vagy csomag-forrásokról.
    
- **Folyamatos validálás:** minden retréning vagy frissítés után automatikus tesztelés és hash-összevetés.
    

---

## ⚖️ Governance & Compliance Angle

**EN:**  
AI supply chain risk is now embedded in frameworks like [[ai_supply_chain_framework_comparison|NIST AI RMF]], [[ai_risk_assessment_methodology|ISO/IEC 23894]], and the EU AI Act.  
Organizations must demonstrate traceability — knowing exactly which data and model components were used, when, and by whom.

**HU:**  
Az AI ellátási lánc kockázata ma már beépült a [[ai_supply_chain_framework_comparison|NIST AI RMF]], [[ai_risk_assessment_methodology|ISO/IEC 23894]] és az EU AI Act szabályozásaiba.  
A szervezeteknek bizonyítaniuk kell a nyomon követhetőséget — pontosan tudniuk kell, mely adatokat és modullelemeket, mikor és ki használt.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. How do AI supply chain attacks differ from traditional software supply chain attacks?
    
2. At which stages of the AI lifecycle can poisoning or compromise occur?
    
3. Why is Zero Trust a key architectural principle for AI supply chains?
    
4. What are the benefits of maintaining a complete AI SBOM?
    
5. How can regulatory frameworks influence supply chain hygiene?
    

---

> _“Every dependency is a doorway — and in AI, doors multiply faster than you can count.”_