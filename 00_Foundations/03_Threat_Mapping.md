---
id: 03_threat_mapping
title: "03 – Threat Mapping / Fenyegetési térkép"
lang: ["hu", "en"]
version: "3.1"
vault: "AI Security Research Vault 2.0"
section_type: "00_Foundations"
role: "threat_mapper"
tags:
  - ai_security
  - foundations
  - underscore_slugs
---
# Threat Mapping in AI Systems

_Seeing the full attack surface of artificial intelligence_

---

## 🌍 Introduction

**EN:**  
Every secure system begins with a map — a mental model of where things can go wrong.  
In AI security, that map is called **Threat Mapping**.  
It connects the [[ai_lifecycle|AI Lifecycle]] to real-world attack surfaces and helps defenders anticipate how vulnerabilities evolve as data, models, and infrastructure interact.

Without a threat map, protection becomes guesswork — and in AI, where systems learn, adapt, and mutate, guesswork is fatal.

**HU:**  
Minden biztonságos rendszer térképpel kezdődik — egy mentális modellel arról, hol történhet baj.  
Az AI biztonságban ezt hívjuk **Threat Mappingnek**, azaz fenyegetés-térképezésnek.  
Ez köti össze az [[ai_lifecycle|AI életciklust]] a valós támadási felületekkel, és segít a védelmi szakértőknek előre látni, hogyan alakulnak a sebezhetőségek, ahogy az adatok, modellek és infrastruktúrák kölcsönhatásba lépnek.

Térkép nélkül a védelem találgatás. Az AI-ban, ahol a rendszerek tanulnak, alkalmazkodnak és változnak — a találgatás végzetes.

---

## 🧠 The Philosophy of Threat Mapping

**EN:**  
Traditional threat models assume fixed assets and static code.  
AI, however, introduces _dynamic intent_ — systems that modify themselves through learning.  
Therefore, AI threat mapping must include both **static surfaces** (e.g., model weights, APIs, datasets) and **adaptive surfaces** (e.g., model behavior drift, [[prompt_injection|prompt injection]] vectors, or evolving supply chains).

Mapping is not documentation — it’s _situational awareness_.  
The map should reflect how attackers think: what they see, what they can reach, and what they can manipulate.

**HU:**  
A hagyományos fenyegetésmodellek rögzített eszközökkel és statikus kóddal számolnak.  
Az AI azonban bevezeti a _dinamikus szándékot_ — a rendszereket, amelyek tanulás útján módosítják önmagukat.  
Ezért az AI threat mappingnek egyszerre kell lefednie a **statikus felületeket** (pl. modellek, API-k, adatkészletek) és az **adaptív felületeket** (pl. viselkedési drift, [[prompt_injection|prompt injection]]-vektorok, változó ellátási láncok).

A térképezés nem adminisztráció — hanem _helyzetismeret_.  
A térképnek azt kell tükröznie, ahogyan a támadó gondolkodik: mit lát, mit ér el, és mit képes befolyásolni.

---

## ⚙️ Building an AI Threat Map

**EN:**  
The process usually follows the **AI lifecycle**, identifying attack points at every phase:

1. **Data Collection** — poisoning, data scraping, and provenance attacks.
    
2. **Data Preparation** — [[data_poisoning|Data Poisoning]] and label manipulation.
    
3. **Model Training** — [[model_stealing|Model Stealing]] via cloud logs or gradient leakage.
    
4. **Evaluation & Validation** — biased metrics and hidden backdoors.
    
5. **Deployment** — [[backdoor_and_trojan_attacks|Trojan Activation]] and [[supply_chain_attack|Supply Chain Attack]].
    
6. **Inference** — [[membership_inference_attacks|Membership Inference]], [[model_inversion|Model Inversion]], [[prompt_injection_and_rag_attacks|Prompt Injection & RAG Exploits]].
    

Each phase forms a _layer_ in the threat map.  
Together, they show not only how an AI can fail — but _when and why_.

**HU:**  
A térképezés az **AI életciklus** logikáját követi, minden fázisban feltárva a támadási pontokat:

1. **Adatgyűjtés** — adatmérgezés, scraping, forráseredet-manipuláció.
    
2. **Adatelőkészítés** — [[data_poisoning|Adatmérgezés]] és címkézési manipuláció.
    
3. **Modeltréning** — [[model_stealing|Modell-lopás]] logok vagy gradiens-szivárgás útján.
    
4. **Értékelés és validálás** — torz metrikák, rejtett backdoor-ok.
    
5. **Telepítés** — [[backdoor_and_trojan_attacks|Trójai aktiválás]] és [[supply_chain_attack|Ellátási lánc támadások]].
    
6. **Inferencia** — [[membership_inference_attacks|Tagsági támadások]], [[model_inversion|Modell-inverzió]], [[prompt_injection_and_rag_attacks|Prompt és RAG kihasználás]].
    

Minden fázis egy _réteg_ a fenyegetési térképen.  
Ezek együtt nemcsak azt mutatják meg, _hogyan_ sérülhet egy AI — hanem azt is, _mikor és miért_.

---

## 🧩 Layered Understanding of AI Threats

**EN:**  
A strong map doesn’t just list threats — it groups them into **conceptual strata**:

- **Data Layer (Input space):** poisoning, leakage, bias.
    
- **Model Layer (Representation space):** backdoors, adversarial examples.
    
- **Runtime Layer (Execution space):** API abuse, sandbox escape, environment takeover.
    
- **Governance Layer (Human space):** policy failure, explainability gaps, unethical deployment.
    

Each layer affects the next.  
For example, a poisoned dataset at layer one can trigger a compliance violation in layer four — years later.

**HU:**  
Egy erős térkép nemcsak felsorolja a fenyegetéseket — hanem **rétegekbe** rendezi őket:

- **Adatszint (Bemeneti tér):** mérgezés, szivárgás, torzítás.
    
- **Modellszint (Reprezentációs tér):** backdoor-ok, adversariális minták.
    
- **Futtatási szint (Végrehajtási tér):** API-visszaélés, sandbox menekülés, környezetátvétel.
    
- **Irányítási szint (Emberi tér):** szabályzási hiba, magyarázhatósági hiány, etikátlan használat.
    

Minden réteg hat a következőre.  
Például egy első rétegben mérgezett adathalmaz akár évekkel később negyedik rétegű megfelelőségi sértést okozhat.

---

## 🧠 From Maps to Defense Architecture

**EN:**  
Once mapped, threats become measurable.  
This allows the design of defense architectures that align with the map’s structure:  
[[defense_index|Defenses]] at the data layer, [[runtime_isolation_and_sandboxing|Isolation]] at runtime, [[continuous_validation_and_review|Continuous Validation]] for governance.

Effective AI threat mapping evolves continuously.  
It’s not a document — it’s a _living neural schema_ for defenders.

**HU:**  
Ha egyszer a fenyegetéseket feltérképeztük, azok mérhetővé válnak.  
Ez lehetővé teszi olyan védelmi architektúrák tervezését, amelyek illeszkednek a térkép rétegeihez:  
[[defense_index|Védelem]] az adatszinten, [[runtime_isolation_and_sandboxing|Izoláció]] a futtatási szinten, [[continuous_validation_and_review|Folyamatos validálás]] az irányítási rétegben.

A hatékony AI threat mapping folyamatosan fejlődik.  
Nem dokumentum — hanem _élő neurális séma_ a védők számára.

---

## ⚖️ Linking to MITRE ATLAS and NIST AI RMF

**EN:**  
To operationalize threat mapping, frameworks like [[ai_risk_assessment_methodology|NIST AI RMF]] and MITRE ATLAS provide shared taxonomies.  
They turn abstract concepts into actionable adversarial playbooks — describing not just “what could go wrong,” but _how attackers think_.

Using these frameworks in your Vault creates consistency between your theoretical notes and practical red-teaming.

**HU:**  
A fenyegetés-térképezés operacionalizálásához olyan keretrendszerek segítenek, mint a [[ai_risk_assessment_methodology|NIST AI RMF]] és a MITRE ATLAS.  
Ezek az absztrakt fogalmakat konkrét támadási forgatókönyvekké alakítják — nemcsak azt írják le, „mi romolhat el”, hanem azt is, _hogyan gondolkodik a támadó_.

Ha ezeket a keretrendszereket a Vaultodon belül is használod, akkor összhang jön létre az elméleti jegyzetek és a gyakorlati red-team tesztek között.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. Why must AI threat mapping account for both static and adaptive attack surfaces?
    
2. Which AI lifecycle phase introduces the highest concentration of threats?
    
3. How does layering (data, model, runtime, governance) improve defense design?
    
4. In what way do MITRE ATLAS and NIST AI RMF complement threat mapping?
    
5. How can a living threat map evolve alongside your deployed models?
    

---

> _“You can’t defend what you don’t see — and you can’t see what you don’t map.”_