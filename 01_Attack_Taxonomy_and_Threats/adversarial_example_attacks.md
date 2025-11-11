# 🧨 Adversarial Example Attacks

---

## 🌍 What are Adversarial Examples? / Mi az az adverszáriális példa?

**EN:**  
Adversarial examples are inputs deliberately perturbed to make a machine learning model produce an incorrect output while the changes are (almost) imperceptible to humans. These inputs expose fragility in learned models and are a primary offensive technique in the [[attack_taxonomy|AI attack taxonomy]]. They matter because they break trust and can be weaponized — e.g., bypassing image-based authentication, causing mislabelling in autonomous driving, or manipulating content filters. 🤖🛡️

**HU:**  
Az adverszáriális példák olyan bemenetek, amelyeket szándékosan megváltoztatnak úgy, hogy az ember számára alig észrevehető, de a gépi tanuló modell téves kimenetet adjon. Ezek a bemenetek rámutatnak a modellek törékenységére és az [[attack_taxonomy|MI-támadások]] fő módszerei közé tartoznak. Fontosak, mert megsértik a bizalmat és fegyverként használhatók (pl. arcfelismerés kikerülése, önvezető autó téveszméje, tartalomszűrés megkerülése). 🤖🛡️

---

## 💡 Formal definition (optimization view) / Formális definíció (optimalizálási nézet)

**EN:**  
Given an input \(x\) with true label \(y\) and a classifier \(f(\cdot)\), an adversarial example \(x'\) solves a constrained optimization: find the smallest perturbation \(\delta\) such that the model's prediction changes (or the model outputs a targeted class \(y_{t}\)) while keeping \(\delta\) bounded (imperceptible):

$$
\min_{\delta} \ \|\delta\|_p \quad \text{s.t.} \quad f(x+\delta) \ne f(x), \quad \| \delta \|_p \le \epsilon
$$

For targeted attacks:

$$
\min_{\delta} \ \|\delta\|_p \quad \text{s.t.} \quad f(x+\delta) = y_t, \quad \| \delta \|_p \le \epsilon
$$

This optimization view unifies most attack algorithms. The norm \(p\) (often \(L_\infty\) or \(L_2\)) and budget \(\epsilon\) define perceptibility and power.

**HU:**  
Adott egy bemenet \(x\) valódi címkéje \(y\) és egy osztályozó \(f(\cdot)\). Egy adverszáriális példát \(x'\) egy korlátos perturbáció \(\delta\) megtalálásaként írhatunk le, amely megváltoztatja a modell predikcióját, miközben \(\delta\) kicsi (alig látható):

$$
\min_{\delta} \ \|\delta\|_p \quad \text{s.t.} \quad f(x+\delta) \ne f(x), \quad \| \delta \|_p \le \epsilon
$$

Célozható támadásoknál:

$$
\min_{\delta} \ \|\delta\|_p \quad \text{s.t.} \quad f(x+\delta) = y_t, \quad \| \delta \|_p \le \epsilon
$$

Ez az optimalizációi nézet összevonja a legtöbb támadási algoritmust. A \(p\)-norm (gyakran \(L_\infty\) vagy \(L_2\)) és a költségkeret \(\epsilon\) határozza meg az észlelhetőséget és a támadó erejét.

---

## 🔪 Common attack algorithms / Gyakori támadási algoritmusok

**EN:**  
Classic and widely-used methods include:  
- **FGSM (Fast Gradient Sign Method):** a single-step white-box perturbation using the sign of the gradient. Its update rule:

$$
x' = x + \epsilon \cdot \text{sign}(\nabla_x \mathcal{L}(f(x), y))
$$

- **PGD (Projected Gradient Descent):** iterative multi-step version of FGSM with projection back into the allowed \(\epsilon\)-ball — strong baseline for robustness evaluation. Iteration:

$$
x_{t+1} = \Pi_{B_\epsilon(x)}\Big( x_t + \alpha \cdot \text{sign}(\nabla_x \mathcal{L}(f(x_t), y)) \Big)
$$

- **CW (Carlini–Wagner):** optimization-based attacks that minimize a tailored objective to find small \(L_2\) perturbations; often used to bypass certain defenses.  

These algorithms highlight **white-box** (attacker knows model & gradients) vs **black-box** (no gradients; rely on queries or transferability) threat models and connect to [[transferability|Transferability]] phenomena.

**HU:**  
Klasszikus, széles körben használt módszerek például:  
- **FGSM (Fast Gradient Sign Method):** egylépéses white-box perturbáció, amely a veszteség gradiensének előjelét használja. Frissítési szabály:

$$
x' = x + \epsilon \cdot \text{sign}(\nabla_x \mathcal{L}(f(x), y))
$$

- **PGD (Projected Gradient Descent):** FGSM iteratív, többlépéses változata, amely minden lépés után visszavetíti a pertubációt az \(\epsilon\)-gömbbe — erős alapvonal a robosztusság teszteléséhez. Iteráció:

$$
x_{t+1} = \Pi_{B_\epsilon(x)}\Big( x_t + \alpha \cdot \text{sign}(\nabla_x \mathcal{L}(f(x_t), y)) \Big)
$$

- **CW (Carlini–Wagner):** optimalizációra épülő támadások, amelyek kis \(L_2\) perturbációkat keresnek; gyakran használják bizonyos védelmek kikerülésére.  

Ezek az algoritmusok illusztrálják a **white-box** (támadó ismeri a modellt és a gradienseket) és **black-box** (nincs gradiens – lekérdezésekre vagy átvitelre támaszkodik) fenyegetési modelleket, és kapcsolódnak a [[transferability|átviteli jelenséghez]].

---

## 🔁 Transferability & Black-box attacks / Átviteli képesség és black-box támadások

**EN:**  
Adversarial examples often transfer between models: an example crafted for model A may fool model B. Attackers exploit transferability to mount black-box attacks by training surrogate models and transferring adversarial inputs. Query-based black-box attacks (e.g., Zeroth-Order Optimization) approximate gradients via queries. Transferability makes defenses harder and highlights the need for system-level protections in [[model_serving_security|model serving]].

**HU:**  
Az adverszáriális példák gyakran átvihetők modellek között: egy A modellre létrehozott példa B modellt is becsaphatja. A támadók ezt kihasználva surrogát modellekkel készítenek példákat és átvitt támadásokat hajtanak végre black-box környezetben. Lekérdezés-alapú black-box támadások (pl. Zeroth-Order Optimization) a gradiens approximációjára támaszkodnak. Az átviteli képesség megnehezíti a védelmeket és kiemeli a rendszer-szintű védelmi szükségletet a [[model_serving_security|modell-szolgáltatás]] környezetben.

---

## 🛡️ Defenses & their caveats / Védekezések és óvatos megjegyzések

**EN:**  
Defenses fall into empirical and certified categories — both have trade-offs:

- **Adversarial Training** (empirical): augment training set with adversarial examples (e.g., PGD training). It is the strongest practical defense but costly and often degrades clean accuracy. See [[adversarial_training|Adversarial Training]].

- **Input preprocessing / Detection:** JPEG compression, bit-depth reduction, or statistical detectors can remove or flag perturbations — but many are circumventable and risk **gradient masking** (giving a false sense of security).

- **Certified Robustness:** techniques like **Randomized Smoothing** provide provable \(L_2\) robustness guarantees under certain noise models. Certified methods trade off tightness and applicability; they give guarantees but often at smaller radii.

- **Ensembles & Diversity:** using multiple models or randomized inference pipelines increases attack cost but does not fully prevent transferability.

Critically: many defenses were broken by stronger adaptive attacks. The community standard for evaluating defenses is to test against strong, adaptive attacks (white-box PGD/CW) and to avoid relying on obfuscated gradients or untested heuristics. Always treat robustness claims skeptically and verify with rigorous evaluation. 🔎

**HU:**  
A védekezések empirikus és tanúsított (certified) kategóriákba sorolhatók — mindkettőnek vannak kompromisszumai:

- **Adversarial Training** (empirikus): adverszáriális példákkal bővített tanítás (pl. PGD training). Gyakorlatban legerősebb védekezés, de költséges és gyakran rontja a tiszta pontosságot. Lásd [[adversarial_training|Adversarial Training]].

- **Bemenet előfeldolgozás / Detektálás:** JPEG tömörítés, bit-mélység csökkentés vagy statisztikai detektorok eltávolíthatják vagy jelölhetik a perturbációkat — de sokan kikerülhetők, és fennáll a **gradiens elrejtés** (gradient masking) veszélye, ami hamis biztonságérzetet ad.

- **Tanúsított robosztusság:** módszerek, mint a **Randomized Smoothing**, bizonyítható \(L_2\) robosztussági garanciát adnak bizonyos zajmodellek alatt. A tanúsított módszerek kompromisszumot jelentenek a garancia szigorúsága és alkalmazhatósága között; gyakran kisebb sugárig adnak garanciát.

- **Ensemble és diverzitás:** több modell vagy randomizált inferencia növeli a támadás költségét, de nem akadályozza meg teljesen az átvitel jelenségét.

Kritikus: sok védekezést erősebb adaptív támadások törtek meg. A védekezéseket mindig erős, adaptív (white-box PGD/CW) támadásokkal kell értékelni — kerüljük az obfuszkált gradiensre épülő vagy tesztlen heuristikus állításokat. Legyünk szkeptikusak a robosztussági állításokkal.

---

## 🧭 Practical guidance for defenders / Gyakorlati útmutató védőknek

**EN:**  
- Use adversarial training for high-risk models (authentication, safety-critical). Combine with clean-accuracy monitoring and [[model_drift|drift detection]].  
- Build layered defenses: input sanitization → robust model → output monitoring & anomaly detection. Treat attackers as adaptive.  
- Evaluate defenses with strong white-box baselines (PGD/autoattack) and report the threat model (knowledge, query budget, norm, \(\epsilon\)).  
- Consider certified methods for auditability where provable guarantees are required (e.g., regulated domains).  
- Add operational controls: rate limits, query-monitoring, authentication, model ensemble diversity, and human-in-the-loop for risky decisions.

**HU:**  
- Magas kockázatú modellekhez (hitelesítés, biztonsági rendszerek) használjunk adverszáriális tanítást. Kombináljuk tiszta pontosság ellenőrzéssel és [[model_drift|drift érzékeléssel]].  
- Rétegzett védelmet építsünk: bemenet-sanitization → robosztus modell → kimenet felügyelet & anomália-detektálás. Tekintsünk a támadókra adaptív szereplőként.  
- A védekezéseket erős white-box alapvonalakkal (PGD/autoattack) értékeljük, és mindig jelöljük a fenyegetési modellt (tudás, lekérdezési büdzsé, norma, \(\epsilon\)).  
- Szabályozott területeken, ahol auditálhatóság kell, fontoljuk meg a tanúsított módszereket.  
- Operatív kontrollok: lekérdezési korlátok, lekérdezésfigyelés, autentikáció, modell-ensemble diverzitás és emberi ellenőrzés a kockázatos döntésekhez.

---

## 🔗 Connections to other Vault topics / Kapcsolódás más fejezetekhez

**EN:**  
This topic links strongly to [[adversarial_training|Adversarial Training]], [[model_serving_security|Model Serving Security]], [[transferability|Transferability]], [[certified_robustness|Certified Robustness]], [[poisoning|Data Poisoning]] (as a complementary attack surface), and [[consistency_audit|Consistency Auditing]] for production monitoring.

**HU:**  
Ez a téma erősen kapcsolódik a [[adversarial_training|Adversarial Training]], [[model_serving_security|Model Serving Security]], [[transferability|Transferability]], [[certified_robustness|Certified Robustness]], [[poisoning|Data Poisoning]] (komplementer támadási felület), és a produkciós felügyeletre vonatkozó [[consistency_audit|Konzisztencia-auditálás]] fejezetekhez.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. Explain the adversarial example optimization objective and how \(\epsilon\) and the chosen norm affect attack visibility.  
2. Compare FGSM and PGD: why is iterative PGD a stronger baseline?  
3. What is transferability and why does it enable black-box attacks? Give a practical attack workflow.  
4. List the main categories of defenses, their strengths, and common failure modes (e.g., gradient masking).  
5. Design a defensive deployment checklist for a model exposed via an API (threat model, mitigation layers, monitoring).

---

> “An adversary reveals the boundaries of our assumptions — robust systems begin by admitting their borders.” ⚖️
