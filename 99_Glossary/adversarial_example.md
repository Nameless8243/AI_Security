---
id: adversarial_example
title: "Adversarial Example / Ellenséges bemenet"
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
# Adversarial Examples

_When imperceptible noise breaks intelligent systems_

---

## 🌍 Introduction

**EN:**  
Adversarial examples are _crafted inputs_ designed to fool a model into making an incorrect prediction. To humans, they look identical to normal data — but to a neural network, they represent chaos.

A few pixels’ difference, a single word’s change, or a slight shift in audio frequencies can completely alter a model’s output. This phenomenon reveals a deep truth about modern AI: **it understands statistics, not meaning**.

**HU:**  
Az adversariális példák olyan _manipulált bemenetek_, amelyeket kifejezetten azért hoznak létre, hogy a modellt hibás előrejelzésre kényszerítsék. Az emberi szemnek vagy fülnek ezek a minták teljesen normálisnak tűnnek — a neurális hálózat számára viszont káoszt jelentenek.

Néhány pixel, egyetlen szó vagy alig észrevehető hangfrekvencia-változás is teljesen más kimenetet adhat. Ez a jelenség alapvető igazságot tár fel: **a modern AI statisztikát ért, nem jelentést**.

---

## 🧠 The Mechanics of Deception

**EN:**  
At the heart of adversarial examples lies the concept of **gradient exploitation**.  
Neural networks make predictions by mapping inputs to outputs along a learned decision boundary. By slightly nudging an input in the direction of the gradient that _increases loss_, attackers can cross that boundary with minimal visible change.

Mathematically, this is expressed as:

$$
x' = x + \epsilon \cdot \text{sign}(\nabla_x L(\theta, x, y))
$$


Where ϵ\epsilonϵ is the small perturbation magnitude.

This simple formula — used in the classic **FGSM (Fast Gradient Sign Method)** — can fool even state-of-the-art models with pixel-level precision.

**HU:**  
Az adversariális példák működésének középpontjában a **gradiens-manipuláció** áll.  
A neurális hálók a bemeneteket döntési határok mentén osztályozzák. Ha a támadó a bemenetet a veszteségfüggvény növekedésének irányába tolja, már minimális változtatással is átlépi a határt — a modell tévesen fog dönteni.

Matematikailag ez így írható fel:

$$
x' = x + \epsilon \cdot \text{sign}(\nabla_x L(\theta, x, y))
$$


Itt az ϵ\epsilonϵ a perturbáció mértéke.

Ez az egyszerű képlet — a **FGSM (Fast Gradient Sign Method)** alapja — képpont-szintű precizitással képes megtéveszteni a legfejlettebb modelleket is.

---

## ⚙️ Attack Variants

**EN:**  
Adversarial attacks vary by method, goal, and visibility:

- **FGSM (Fast Gradient Sign Method):** one-step gradient-based perturbation.
    
- **PGD (Projected Gradient Descent):** iterative FGSM, often stronger.
    
- **CW (Carlini & Wagner):** optimization-based, minimizes visible distortion.
    
- **Black-box attacks:** estimate gradients indirectly via queries.
    
- **Universal adversarial perturbations:** one noise pattern that fools _many_ inputs.
    
- **Physical attacks:** real-world perturbations like stickers on stop signs or 3D objects altering recognition.
    

**HU:**  
Az adversariális támadások többféle céllal és módszerrel készülhetnek:

- **FGSM (Fast Gradient Sign Method):** egyetlen gradienslépésen alapuló perturbáció.
    
- **PGD (Projected Gradient Descent):** iteratív FGSM, erősebb változat.
    
- **CW (Carlini & Wagner):** optimalizációs támadás, amely minimalizálja a látható torzítást.
    
- **Fekete-dobozos támadások:** gradiensbecslés lekérdezésekkel, anélkül hogy a modellhez hozzáférnének.
    
- **Univerzális perturbációk:** egyetlen zajminta, ami sok bemenetet megtéveszt.
    
- **Fizikai támadások:** valós világban alkalmazott módosítások, mint matricák a táblákon vagy formaváltoztatott 3D objektumok.
    

---

## 🧩 Multimodal Adversarial Attacks

**EN:**  
As AI becomes multimodal — combining vision, text, and sound — adversarial examples expand beyond images.

- **Text-based attacks:** change synonyms, punctuation, or word order to alter meaning (→ [[prompt_injection|Prompt Injection]]).
    
- **Audio attacks:** embed ultrasonic frequencies that speech models misinterpret.
    
- **Multimodal fusion attacks:** exploit weak alignment between modalities (e.g., pairing mismatched captions and images to create concept drift).
    

These attacks prove that adversarial vulnerability is _modality-agnostic_ — it’s a property of the learning process itself.

**HU:**  
Ahogy az AI multimodálissá válik — képet, szöveget és hangot is értelmez — az adversariális példák is túlnyúlnak a képeken.

- **Szöveges támadások:** szinonimák, írásjelek vagy szórend cseréje, amellyel megváltozik az értelmezés (→ [[prompt_injection|Prompt Injection]]).
    
- **Hang alapú támadások:** ultrahangos frekvenciák beágyazása, amelyeket a beszédfelismerő modellek félreértenek.
    
- **Multimodális támadások:** a modalitások közötti gyenge illesztést használják ki (pl. nem egyező képfeliratok és képek párosítása).
    

Ezek a támadások megmutatják, hogy az adversariális sebezhetőség _nem függ az adatformátumtól_ — ez a tanulási folyamat inherens tulajdonsága.

---

## 🛡️ Defenses and Limitations

**EN:**  
Several defenses exist, though none are perfect:

- **[[adversarial_training|Adversarial Training]]:** expose the model to adversarial examples during learning.
    
- **[[input_restoration|Input Restoration]]:** denoise or reconstruct inputs before inference.
    
- **Gradient masking:** hide gradients to confuse attackers (often temporary).
    
- **Defensive distillation:** train on softened outputs to make decision boundaries smoother.
    
- **Certified robustness:** mathematically guarantee performance under bounded perturbations.
    

However, attackers constantly adapt. Robustness is a moving target, not a finish line.

**HU:**  
Többféle védekezés létezik, de egyik sem tökéletes:

- **[[adversarial_training|Adversariális tréning]]:** a modell megtanítása a megtévesztő példák felismerésére.
    
- **[[input_restoration|Input Restoration]]:** bemenetek zajmentesítése vagy rekonstruálása inferencia előtt.
    
- **Gradiens-elfedés:** a gradiens elrejtése, hogy a támadó ne tudja kihasználni — gyakran ideiglenes megoldás.
    
- **Defenzív desztilláció:** lágyított kimenetekkel való tanítás, ami kisimítja a döntési határokat.
    
- **Tanúsított robusztusság:** matematikai garancia a korlátozott perturbációk melletti helyes működésre.
    

A támadók azonban folyamatosan alkalmazkodnak. A robusztusság mozgó célpont — nem végállomás.

---

## ⚖️ Broader Implications

**EN:**  
Adversarial examples expose the fragility of machine intelligence.  
They remind us that models do not _understand_ their input — they merely optimize a function.  
For AI safety, this realization drives research into **interpretable models**, **robust architectures**, and **[[ai_safety_vs_security_bridge|AI Safety–Security bridges]]**.

**HU:**  
Az adversariális példák rámutatnak a gépi intelligencia törékenységére.  
Emlékeztetnek arra, hogy a modellek nem _értik_ a bemenetet — csak egy függvényt optimalizálnak.  
Az AI biztonság számára ez a felismerés hajtja az **értelmezhető modellek**, a **robosztus architektúrák** és az **[[ai_safety_vs_security_bridge|AI Safety–Security]]** közti híd kutatását.

---

## 🔍 Review Questions / Ellenőrző kérdések

1. What defines an adversarial example, and why is it dangerous?
    
2. How does FGSM differ from PGD or CW attacks?
    
3. What makes multimodal AI systems more vulnerable?
    
4. Which defensive strategies can mitigate adversarial examples, and what are their trade-offs?
    
5. Why are adversarial examples considered a bridge between AI safety and AI security?
    

---

> _“When noise defeats intelligence, the lesson is not to silence the noise — but to listen more wisely.”_