---
version: "3.2"
section_type: "defense"
agent: "Principle Engineer"
---
# 🧮 Differential Privacy

---

## 🌍 What Is Differential Privacy? / Mi az a differenciális adatvédelem?

**EN:**  
**Differential Privacy (DP)** is a mathematical framework ensuring that the output of a computation does not reveal whether any individual’s data was included in the input. In simpler terms, it guarantees that *each person’s presence or absence has a minimal, bounded effect* on the model’s predictions or statistics.  

In AI and machine learning, differential privacy protects sensitive training data — such as personal, medical, or financial records — from being reverse-engineered or inferred through model outputs or gradients. 🛡️🤖  

**HU:**  
A **Differenciális adatvédelem (DP)** egy matematikai keretrendszer, amely biztosítja, hogy egy számítás eredménye ne árulja el, hogy bármely egyén adata szerepelt-e a bemenetben. Egyszerűbben: garantálja, hogy *egy személy jelenléte vagy hiánya csak korlátozott mértékben befolyásolhatja* a modell kimenetét vagy statisztikáit.  

Az MI-ben a differenciális adatvédelem védi az érzékeny tanítóadatokat — például személyes, orvosi vagy pénzügyi adatokat — attól, hogy a modellből visszafejthetők legyenek. 🛡️🤖

---

## 💡 Formal Definition / Formális definíció

**EN:**  
A randomized algorithm \( M \) provides **\( (\epsilon, \delta) \)-differential privacy** if, for all pairs of datasets \( D_1, D_2 \) that differ by at most one record, and for all possible outputs \( S \):

$$
P[M(D_1) \in S] \le e^{\epsilon} \cdot P[M(D_2) \in S] + \delta
$$

- \( \epsilon \) (epsilon): *privacy budget*, bounds how much output probabilities can differ. Smaller means stronger privacy.  
- \( \delta \): small slack term allowing rare violations.  
- \( M \): the mechanism (e.g., query, model, gradient update).  

This ensures an observer cannot confidently infer whether any single record was part of the dataset.

**HU:**  
Egy randomizált algoritmus \( M \) **\( (\epsilon, \delta) \)-differenciális adatvédelmet** biztosít, ha minden olyan \( D_1, D_2 \) adathalmazra, amelyek legfeljebb egy rekordban különböznek, és minden lehetséges kimenetre \( S \) igaz:

$$
P[M(D_1) \in S] \le e^{\epsilon} \cdot P[M(D_2) \in S] + \delta
$$

- \( \epsilon \) (epszilon): az *adatvédelmi költségvetés*, amely korlátozza, mennyire térhetnek el a kimeneti valószínűségek. Minél kisebb, annál erősebb a védelem.  
- \( \delta \): kis tűrési tag, amely ritka megsértéseket enged meg.  
- \( M \): a mechanizmus (pl. lekérdezés, modell, gradiens-frissítés).  

Ez biztosítja, hogy a megfigyelő ne tudja megbízhatóan megállapítani, szerepelt-e egy adott rekord az adathalmazban.

---

## 🧩 Mechanisms That Achieve Differential Privacy / DP-t biztosító mechanizmusok

**EN:**  
1. **Laplace Mechanism:** adds Laplacian noise proportional to query sensitivity.  
2. **Gaussian Mechanism:** adds Gaussian noise — used for continuous data.  
3. **Exponential Mechanism:** selects outputs probabilistically based on utility scores.  
4. **Privacy Amplification by Subsampling:** training on random subsets naturally improves privacy guarantees.  
5. **DP-SGD (Differentially Private Stochastic Gradient Descent):** cornerstone of private deep learning; clips gradients and adds Gaussian noise at each step:

$$
g_i' = \frac{g_i}{\max(1, \frac{\|g_i\|_2}{C})}, \quad \bar{g} = \frac{1}{N}\sum_i g_i' + \mathcal{N}(0, \sigma^2 C^2 I)
$$

Here \(C\) is the clipping norm and \(\sigma\) controls noise magnitude.  

**HU:**  
1. **Laplace-mechanizmus:** Laplace-eloszlású zajt ad az érzékenységgel arányosan.  
2. **Gauss-mechanizmus:** Gauss-zajt ad hozzá — folytonos adatok esetén.  
3. **Exponenciális mechanizmus:** az eredményt hasznossági pontszám alapján valószínűségi alapon választja.  
4. **Mintavételezés általi adatvédelmi erősítés:** véletlen részhalmazon való tanítás természetesen erősíti a védelmet.  
5. **DP-SGD (Differenciálisan védett sztochasztikus gradiens-descent):** a privát mélytanulás alapja; gradiens-klippelés és Gauss-zaj hozzáadása minden lépésben:

$$
g_i' = \frac{g_i}{\max(1, \frac{\|g_i\|_2}{C})}, \quad \bar{g} = \frac{1}{N}\sum_i g_i' + \mathcal{N}(0, \sigma^2 C^2 I)
$$

Itt \(C\) a vágási norma, \(\sigma\) pedig a zaj mértékét szabályozza.

---

## ⚙️ Differential Privacy in Machine Learning / DP az MI-ben

**EN:**  
Differential privacy is used during model training or data sharing to ensure that even with full model access, attackers cannot reconstruct or infer specific training examples (see [[membership_inference|Membership Inference]] and [[model_inversion|Model Inversion]]).  

### Common use cases:
- **DP-SGD in neural networks:** ensures model gradients do not leak individual samples.  
- **Private federated learning:** each client’s update is noised before aggregation.  
- **Private query answering:** aggregating statistics with bounded disclosure risk.  
- **Synthetic data generation:** producing data that mimics real patterns without exposing individuals.

**HU:**  
A differenciális adatvédelem modell-tanítás vagy adatmegosztás során biztosítja, hogy még teljes modell-hozzáférés esetén se lehessen visszafejteni vagy kikövetkeztetni egyes tanítópéldákat (lásd [[membership_inference|Tagsági következtetés]] és [[model_inversion|Modell-inverzió]]).  

### Tipikus alkalmazások:
- **DP-SGD neurális hálókban:** megakadályozza, hogy a gradiens-szivárgás felfedje az egyéni mintákat.  
- **Privát federált tanulás:** minden kliens frissítése zajjal védve kerül aggregálásra.  
- **Privát lekérdezések:** aggregált statisztikák kiszivárgási kockázatának korlátozása.  
- **Szimulált adatképzés:** mesterséges adatok generálása valós mintázatok alapján, anélkül hogy egyének adatait felfedné.

---

## 🧠 Privacy–Utility Trade-off / Adatvédelem és hasznosság egyensúlya

**EN:**  
Adding noise improves privacy but reduces model accuracy. The balance depends on:  
- \( \epsilon \): smaller → more noise → stronger privacy, lower utility  
- dataset size: larger datasets tolerate more noise  
- task sensitivity: high-stakes models (medical, legal) require tighter privacy budgets  

Design goal: **minimize privacy loss for acceptable accuracy**, often requiring empirical tuning and [[governance_index|governance]] oversight.

**HU:**  
A zaj hozzáadása növeli az adatvédelmet, de csökkenti a modell pontosságát. Az egyensúlyt befolyásolja:  
- \( \epsilon \): kisebb → több zaj → erősebb védelem, gyengébb hasznosság  
- adathalmaz mérete: nagyobb halmaz több zajt is elvisel  
- feladat érzékenysége: kritikus modellek (pl. orvosi, jogi) szigorúbb költségvetést igényelnek  

A cél: **az adatvédelmi veszteség minimalizálása elfogadható pontosság mellett**, amit gyakorlati hangolás és [[governance_index|irányítási felügyelet]] kísér.

---

## 🧰 Implementation Best Practices / Megvalósítási irányelvek

**EN:**  
- Use **privacy accounting** (e.g., Moments Accountant, Rényi DP) to track cumulative privacy loss.  
- Combine with [[secure_aggregation|Secure Aggregation]] or [[federated_learning_security|Federated Learning Security]].  
- Never rely solely on anonymization — differential privacy provides *provable guarantees*, anonymization does not.  
- Validate DP parameters (\(\epsilon, \delta\)) with domain-specific compliance standards (e.g., GDPR).  
- Apply **post-training audits** to ensure outputs meet expected privacy thresholds.

**HU:**  
- Használj **adatvédelmi könyvelést** (pl. Moments Accountant, Rényi DP) az összesített adatvédelmi veszteség követésére.  
- Kombináld [[secure_aggregation|Biztonságos aggregációval]] vagy [[federated_learning_security|Federált tanulás védelemmel]].  
- Soha ne támaszkodj kizárólag anonimizálásra — a differenciális adatvédelem *bizonyítható garanciákat* ad, míg az anonimizálás nem.  
- A DP-paramétereket (\(\epsilon, \delta\)) a doménhez illesztett megfelelőségi szabványokkal (pl. GDPR) kell validálni.  
- Alkalmazz **tanítás utáni auditot**, hogy ellenőrizd: a kimenetek megfelelnek-e a várt adatvédelmi szintnek.

---

## 🔗 Related Topics / Kapcsolódó Fejezetek

**EN:**  
See [[membership_inference|Membership Inference]], [[model_inversion|Model Inversion]], [[federated_learning_security|Federated Learning Security]], [[data_poisoning|Data Poisoning]], and [[privacy_preserving_ml|Privacy-Preserving ML]].

**HU:**  
Lásd még: [[membership_inference|Tagsági következtetés]], [[model_inversion|Modell-inverzió]], [[federated_learning_security|Federált tanulás védelme]], [[data_poisoning|Adatmérgezés]], és [[privacy_preserving_ml|Adatvédelmet megőrző gépi tanulás]].

---

## 🧭 Review Questions / Ellenőrző kérdések

1. Explain the meaning of \( \epsilon \) and \( \delta \) in the differential privacy definition.  
2. Derive how DP-SGD balances gradient clipping and noise addition.  
3. How does differential privacy protect against membership inference and model inversion attacks?  
4. Describe how privacy amplification by subsampling strengthens privacy guarantees.  
5. Design a privacy accounting approach for a DP-SGD training process over 50 epochs.

---

> “Perfect privacy does not exist — but differential privacy shows us how to measure what we lose.” 🔏
