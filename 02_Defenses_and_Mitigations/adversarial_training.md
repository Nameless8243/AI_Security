---
version: "3.2"
section_type: "defense"
agent: "Learning Mentor"
---
# 🛡️ Adversarial Training

---

## 🌍 What Is Adversarial Training? / Mi az az Adversarial Training?

**EN:**  
Adversarial training is one of the most effective and practical defenses against [[adversarial_example_attacks|Adversarial Example Attacks]]. It works by *exposing the model to attacks during training* so that it learns to resist them at inference time.  

In essence, we let the model “fight its own battles” — we generate adversarial examples (small, carefully crafted perturbations) during each training step and include them in the loss function. Over time, the model becomes more robust to these perturbations, learning smoother decision boundaries. ⚔️🤖  

**HU:**  
Az adversarial training az egyik leghatékonyabb és leggyakorlatiabb védekezési módszer az [[adversarial_example_attacks|adverszáriális példákkal]] szemben. A módszer lényege, hogy a modellt *már a tanítás során támadásoknak tesszük ki*, így megtanul ellenállni ezeknek az inferencia során.  

Lényegében a modell „megtanul harcolni” – minden tanítási lépésben adverszáriális példákat generálunk, és ezeket beépítjük a veszteségfüggvénybe. Idővel a modell robusztusabbá válik, és simább döntési határokat tanul. ⚔️🤖

---

## 💡 Core Idea / Alapelv

**EN:**  
The fundamental concept is **min–max optimization**. Instead of minimizing the loss only on clean examples, adversarial training minimizes the *worst-case loss* under small perturbations:

$$
\min_\theta \mathbb{E}_{(x, y) \sim \mathcal{D}} \left[ \max_{\|\delta\|_p \le \epsilon} \mathcal{L}(f_\theta(x + \delta), y) \right]
$$

Here:  
- \( \delta \): adversarial perturbation within an \(L_p\) norm ball of radius \(\epsilon\)  
- \( f_\theta \): model with parameters \(\theta\)  
- \( \mathcal{L} \): loss function (e.g., cross-entropy)  

The inner maximization generates an adversarial example; the outer minimization trains the model to minimize loss even under that attack.

**HU:**  
Az alapelv a **min–max optimalizálás**. Ahelyett, hogy csak a tiszta példákon minimalizálnánk a veszteséget, az adversarial training a *legrosszabb esetben fellépő veszteséget* minimalizálja kis perturbációk mellett:

$$
\min_\theta \mathbb{E}_{(x, y) \sim \mathcal{D}} \left[ \max_{\|\delta\|_p \le \epsilon} \mathcal{L}(f_\theta(x + \delta), y) \right]
$$

Ahol:  
- \( \delta \): adverszáriális perturbáció az \(L_p\) normával mért \(\epsilon\) sugarú térben  
- \( f_\theta \): a modell paraméterezett függvénye  
- \( \mathcal{L} \): veszteségfüggvény (pl. cross-entropy)  

A belső maximum az adverszáriális példát generálja, míg a külső minimum a modellt úgy optimalizálja, hogy a veszteség kicsi maradjon még támadás alatt is.

---

## ⚙️ Algorithm Overview / Algoritmus Áttekintés

**EN:**  
1. **Generate adversarial examples** for the current batch (using FGSM, PGD, or another attack).  
2. **Combine clean and adversarial samples** to form the augmented batch.  
3. **Compute loss** on both clean and adversarial data.  
4. **Backpropagate** and update model parameters to minimize the combined loss.

Typical implementation (PGD-based):

$$
x_{t+1} = \Pi_{B_\epsilon(x)}\left( x_t + \alpha \cdot \text{sign}(\nabla_x \mathcal{L}(f_\theta(x_t), y)) \right)
$$

This inner loop runs for several iterations per batch, increasing robustness at the cost of longer training time.

**HU:**  
1. **Adverszáriális példák generálása** az aktuális batch-hez (FGSM, PGD stb. módszerrel).  
2. **Tiszta és adverszáriális minták kombinálása** a bővített tanítóhalmazhoz.  
3. **Veszteség kiszámítása** mindkét adattípuson.  
4. **Visszaterjesztés (backpropagation)** és a modell paramétereinek frissítése a kombinált veszteség minimalizálására.

PGD-alapú implementáció esetén:

$$
x_{t+1} = \Pi_{B_\epsilon(x)}\left( x_t + \alpha \cdot \text{sign}(\nabla_x \mathcal{L}(f_\theta(x_t), y)) \right)
$$

Ez a belső ciklus minden batch-ben többször lefut, így a modell robusztusabb lesz — viszont a tanítás időigényesebb.

---

## 🧩 Types of Adversarial Training / Az adversarial training típusai

**EN:**  
- **Standard Adversarial Training (SAT):** combines clean and adversarial samples; improves robustness against specific attacks (usually \(L_\infty\) norm).  
- **TRADES (Tradeoff-inspired Adversarial Defense):** balances robustness and accuracy by introducing a KL-divergence term between clean and adversarial outputs:

$$
\mathcal{L}_{TRADES} = \mathcal{L}_{CE}(f(x), y) + \beta \cdot \text{KL}(f(x) \,||\, f(x+\delta))
$$

- **Free Adversarial Training:** reuses gradients from standard backprop to speed up generation of adversarial examples.  
- **Curriculum Adversarial Training:** gradually increases the attack strength (\(\epsilon\)) as training progresses.  
- **Domain-specific Adversarial Training:** adapts perturbation types to the domain (text, audio, code, etc.).

**HU:**  
- **Standard Adversarial Training (SAT):** tiszta és adverszáriális minták kombinálása; robusztusabbá tesz adott támadási típusok (általában \(L_\infty\)-normás) ellen.  
- **TRADES (Tradeoff-inspired Adversarial Defense):** a robusztusság és pontosság egyensúlyát a tiszta és a támadott kimenetek közötti KL-divergencia bevezetésével szabályozza:

$$
\mathcal{L}_{TRADES} = \mathcal{L}_{CE}(f(x), y) + \beta \cdot \text{KL}(f(x) \,||\, f(x+\delta))
$$

- **Free Adversarial Training:** a backprop gradiensét újrahasznosítja az adverszáriális példák gyorsabb előállításához.  
- **Curriculum Adversarial Training:** fokozatosan növeli a támadás erejét (\(\epsilon\)) a tanulás előrehaladtával.  
- **Domain-specifikus Adversarial Training:** a perturbációt az adott doménhez (szöveg, hang, kód) igazítja.

---

## 🧠 Advantages and Limitations / Előnyök és korlátok

**EN:**  
**✅ Strengths:**  
- Provides **empirical robustness** to known attacks.  
- Improves model generalization and smoothness.  
- Forms the basis for certified defenses.  

**⚠️ Limitations:**  
- High computational cost — each batch involves multiple gradient steps.  
- Limited transferability — robustness may not generalize across all attack types.  
- Trade-off with clean accuracy (especially with large \(\epsilon\)).  
- Requires careful tuning of \(\epsilon\), learning rate, and attack steps.

**HU:**  
**✅ Előnyök:**  
- **Empirikus robusztusságot** ad ismert támadásokkal szemben.  
- Javítja a modell általánosítását és döntési határainak simaságát.  
- Alapot ad a tanúsított (certified) védekezésekhez.  

**⚠️ Korlátok:**  
- Magas számítási költség — minden batch több gradienslépést igényel.  
- Korlátozott általánosítás — nem minden támadástípusra terjed ki.  
- Kompromisszum a tiszta pontossággal (különösen nagy \(\epsilon\) mellett).  
- Gondos paraméterhangolást igényel (\(\epsilon\), tanulási ráta, lépésszám).

---

## 🧩 Practical Recommendations / Gyakorlati javaslatok

**EN:**  
- Combine adversarial training with other defenses like [[input_sanitization|Input Sanitization]], [[certified_robustness|Certified Robustness]], and [[model_monitoring|Model Monitoring]].  
- Use strong inner attacks (PGD, AutoAttack) for realistic robustness evaluation.  
- Monitor the trade-off between clean accuracy and adversarial robustness continuously.  
- Apply *adversarial fine-tuning* — training a pre-trained model for a few epochs under attack.  
- Integrate into the MLOps lifecycle for continuous robustness assurance.

**HU:**  
- Kombináld az adversarial traininget más védelmekkel, mint az [[input_sanitization|Bemenet-tisztítás]], [[certified_robustness|Tanúsított robusztusság]] vagy [[model_monitoring|Modell-monitorozás]].  
- Használj erős belső támadásokat (PGD, AutoAttack) a robusztusság valós értékeléséhez.  
- Folyamatosan figyeld a tiszta pontosság és robusztusság közötti kompromisszumot.  
- Alkalmazz *adversarial fine-tuningot* – előre tanított modell néhány epoch-nyi robusztus tanítása.  
- Integráld az MLOps életciklusba a folyamatos robusztusság érdekében.

---

## 🔗 Related Topics / Kapcsolódó Fejezetek

**EN:**  
See also [[adversarial_example_attacks|Adversarial Example Attacks]], [[certified_robustness|Certified Robustness]], [[model_robustness_evaluation|Model Robustness Evaluation]], [[model_serving_security|Model Serving Security]], and [[consistency_audit|Consistency Auditing]].

**HU:**  
Lásd még: [[adversarial_example_attacks|Adverszáriális példák]], [[certified_robustness|Tanúsított robusztusság]], [[model_robustness_evaluation|Modell-robosztusság értékelés]], [[model_serving_security|Modell-szolgáltatás biztonsága]] és [[consistency_audit|Konzisztencia-auditálás]].

---

## 🧭 Review Questions / Ellenőrző kérdések

1. Derive the min–max optimization formula for adversarial training and explain each term.  
2. Compare FGSM-based and PGD-based adversarial training in terms of robustness and cost.  
3. How does TRADES balance clean accuracy and robustness mathematically?  
4. What are the trade-offs between adversarial training and certified robustness approaches?  
5. Design an adversarial fine-tuning plan for a pre-trained transformer model.

---

> “True robustness is not about avoiding attacks — it’s about learning from them.” ⚖️
