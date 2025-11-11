---
version: "3.3"
section_type: "attack"
agent: "Principle Engineer"
---
# 🕵️ Model Stealing & Extraction

---

## 🌍 What is Model Stealing? / Mi az a model stealing?

**EN:**  
Model stealing (aka model extraction) is the act of reconstructing or approximating a target machine learning model \(f\) by an adversary who only has *query access* (or limited visibility) to it — typically via an API or deployed service. The attacker aims to produce \( \hat{f} \) that matches \(f\)’s functionality, performance, or confidential attributes (architecture, weights, training data characteristics). This is a direct intellectual-property and operational risk for ML providers and a precursor to many follow-on attacks (fingerprinting, adversarial transfer, privacy attacks). 🤖🛡️

**HU:**  
A model stealing (vagy model-extraction) során a támadó rekonstruálja vagy megközelíti a célmodell \(f\) működését úgy, hogy csak lekérdezési hozzáférése van (például API-n keresztül). A cél egy olyan \( \hat{f} \) előállítása, amely hasonló funkcionalitást, teljesítményt vagy bizalmas jellemzőket (architektúra, súlyok, a tanítóadatokra jellemző mintázatok) utánoz. Ez szellemi tulajdon- és működési kockázatot jelent az ML-szolgáltatók számára, és gyakran előjátéka további támadásoknak (pl. fingerprinting, adverszáriális átvitel, adatvédelmi támadások). 🤖🛡️

---

## 💡 Why it matters / Miért fontos ez a probléma

**EN:**  
If an attacker obtains \( \hat{f} \) they can: (1) avoid paying for the service, (2) find adversarial inputs that transfer to the original model, (3) infer training data properties (link to [[membership_inference|Membership Inference]] / [[model_inversion|Model Inversion]]), or (4) replicate a proprietary model for resale. From a defender’s viewpoint, extraction breaks confidentiality guarantees of the model-as-a-service business model and widens the threat surface for downstream attacks. 💸🔓

**HU:**  
Ha a támadó megszerzi \( \hat{f} \)-et, akkor: (1) elkerülheti a szolgáltatás díját, (2) találhat olyan adverszáriális bemeneteket, amelyek átjárnak az eredeti modellen, (3) következtethet a tanítóadatokra (lásd [[membership_inference|Tagsági következtetés]] / [[model_inversion|Modell-inverzió]]), vagy (4) lemásolhatja és eladhatja a szellemi tulajdont. A védekezés szempontjából ez aláássa a model-as-a-service titoktartását és növeli a további támadások felületét. 💸🔓

---

## 🧩 Attack taxonomies / A támadások típusai

**EN:**  
Extraction attacks vary by goal and attacker resources. Common classes include:  
- **Functional extraction:** approximate the model’s input→output mapping (black-box mimic).  
- **Parameter extraction:** recover model parameters or architecture (stronger, often requires more queries).  
- **Decision boundary extraction:** learn the classifier boundary precisely to craft high-success adversarial examples.  
- **Meta-extraction:** infer training-set statistics, hyperparameters, label smoothing, or proprietary pre/post-processing steps.

**HU:**  
A kinyerési támadások cél és erőforrások szerint különböznek. Gyakoribb típusok:  
- **Funkcionális kinyerés:** a modell input→output leképzésének utánozása (black-box).  
- **Paraméter-kinyerés:** modellparaméterek vagy architektúra visszafejtése (erőforrásigényesebb).  
- **Döntési határ kinyerés:** a klaszterhatár pontos megtanulása, hogy hatékony adverszáriális példákat készítsenek.  
- **Meta-kinyerés:** tanítóadat-statisztikák, hiperparaméterek vagy privát elő-/utófeldolgozási lépések feltárása.

---

## 🔬 Formal objective (query-based view) / Formális cél (lekérdezésalapú nézet)

**EN:**  
An adversary issues queries \( \{x^{(i)}\}_{i=1}^m \) and observes outputs \( \{y^{(i)} = f(x^{(i)})\} \) (scores, probabilities, or labels). The extraction problem can be framed as:

$$
\min_{\hat{f} \in \mathcal{F}} \; \mathbb{E}_{x \sim \mathcal{D}_q} \left[ \mathcal{L}\big( f(x), \hat{f}(x) \big) \right]
$$

subject to a budget constraint \( m \le M \) (number of queries) and possibly noise/rounding applied by the oracle. The choice of query distribution \( \mathcal{D}_q \) (random, adaptive, or membership-focused) and whether outputs are probabilities or just top-1 labels dramatically affects success.

**HU:**  
A támadó lekérdezéseket \( \{x^{(i)}\}_{i=1}^m \) küld a szolgáltatásnak, és megfigyeli a válaszokat \( \{y^{(i)} = f(x^{(i)})\} \) (pontszámok, valószínűségek vagy címkék). A kinyerési problémát így lehet megfogalmazni:

$$
\min_{\hat{f} \in \mathcal{F}} \; \mathbb{E}_{x \sim \mathcal{D}_q} \left[ \mathcal{L}\big( f(x), \hat{f}(x) \big) \right]
$$

korlátozva a lekérdezési büdzsét \( m \le M \) és figyelembe véve a szolgáltató által alkalmazott zajt vagy kerekítést. A lekérdezési eloszlás \( \mathcal{D}_q \) (véletlenszerű, adaptív vagy tagság-fókuszú) és az, hogy valószínűségeket vagy csak top-1 választ ad a szolgáltató, jelentősen befolyásolja a siker esélyét.

---

## 🔁 Query strategies & transfer / Lekérdezési stratégiák és áttétel

**EN:**  
Attackers use several query strategies: random sampling over input space, adaptive active learning (query points chosen to reduce model uncertainty), and task-specific queries (e.g., using domain data). When attackers have surrogate models, they can combine transfer learning with distillation: train \( \hat{f} \) on queried pairs, optionally using data augmentation and label smoothing to better mimic \(f\). Probabilistic outputs (soft labels) accelerate extraction; integer/label-only outputs make it harder but not impossible. Transferability allows attackers to craft adversarial inputs on \( \hat{f} \) that often transfer to \(f\). See connections to [[transferability|Transferability]] and [[adversarial_example_attacks|Adversarial Examples]].

**HU:**  
A támadók több lekérdezési stratégiát használnak: véletlenszerű mintavétel a bemeneti térben, adaptív aktív tanulás (lekérdezések bizonytalanság csökkentésére), és domén-specifikus lekérdezések. Surrogát modellek alkalmazásakor az áttérés (transfer) és distilláció kombinálható: \( \hat{f} \)-et a lekérdezett párokon tanítják, adatkiterjesztéssel és címke-simítással, hogy hűbben kövesse \(f\)-et. A valószínűségi (soft) kimenetek gyorsítják a kinyerést; a csak címke válaszok nehezítik, de nem teszik lehetetlenné. Az áttétel lehetővé teszi, hogy a \( \hat{f} \)-en készített adverszáriális példák gyakran működjenek az eredeti \(f\)-en is. Lásd [[transferability|Átviteli jelenség]] és [[adversarial_example_attacks|Adverszáriális példák]].

---

## 🛡️ Defenses & mitigations / Védekezések és mérséklések

**EN:**  
Defending against model extraction requires layered, operational and algorithmic controls:

- **API & Rate Controls:** strict rate limits, per-user quotas, anomaly-based throttling to limit query budgets.  
- **Output Hardening:** reduce information leakage by returning top-k labels only, rounding probabilities, or adding calibrated noise (be careful — naive noise can be circumvented).  
- **Response Randomization & Watermarking:** embed provider-only watermarks in outputs or apply randomized response that degrades extraction quality while preserving utility. See [[watermarking|Watermarking]] for model ownership techniques.  
- **Model Distillation & Ensemble Guarding:** serve a distilled, less-informative model publicly while keeping a high-fidelity version private; use ensembles with randomized selector logic.  
- **Detection & Forensics:** continuous [[query_monitoring|query monitoring]] and anomaly detection to detect suspicious querying patterns; keep audit trails for legal action.  
- **Legal & Economic Controls:** API terms, usage billing, and legal recourse deter misuse.  
- **Technical: Differential Privacy & Output Perturbation:** training with [[differential_privacy|differential privacy]] reduces overfitting to unique training samples and can limit meta-extraction, but it does not fully prevent functional extraction.

No single control is sufficient — combine rate-limiting, monitoring, output controls, and legal measures. Evaluate trade-offs: too aggressive hardening degrades user experience and model utility.

**HU:**  
A védelmet rétegzett, működési és algoritmikus kontrollokkal kell biztosítani:

- **API & Rate kontrollok:** szigorú sebességkorlátok, felhasználónként kvóták, anomália-alapú korlátozás a lekérdezési büdzsék megfékezésére.  
- **Kimenet-erősítés:** információszivárgás csökkentése top-k címkék visszaadásával, valószínűségek kerekítésével vagy kalibrált zaj hozzáadásával (óvatosan — a naiv zaj kijátszható).  
- **Válasz-randomizálás & Watermarking:** szolgáltató-specifikus vízjelek beágyazása a válaszokba vagy véletlenszerű válaszmechanizmus, amely rontja a kinyerést, miközben megtartja a hasznosságot. Lásd [[watermarking|Vízjelezés]] a modell-tulajdonlás védelmére.  
- **Model distilláció & ensemble védelem:** nyilvános használatra kevésbé informatív, lebutított modellt szolgáltatni, míg a magas hűségű modellt privátban tartani; ensemble-ök véletlenszerű kiválasztása növeli a támadó költségét.  
- **Detekció & forenzika:** folyamatos [[query_monitoring|lekérdezés-figyelés]] és anomáliaészlelés a gyanús minták felfedezésére; auditelési naplók jogi lépésekhez.  
- **Jogi & gazdasági kontrollok:** API-feltételek, fizetési rendszerek és jogi lépések visszatartó erőt adhatnak.  
- **Technikai: differenciális adatvédelem & kimenet-perturbáció:** a [[differential_privacy|differenciális adatvédelem]] csökkenti a modell érzékenységét egyedi tanítópéldákra és korlátozhatja a meta-kinyerést, de önmagában nem állítja meg a funkcionális kinyerést.

Egyetlen védelem sem elég — kombináld a rate-limitinget, monitorozást, kimenet-kezelést és jogi intézkedéseket. Mérlegeld a kompromisszumokat: túl agresszív hardening ronthatja a felhasználói élményt és a modell hasznosságát.

---

## 🔗 Operational playbook (short) / Operatív lépések röviden

**EN:**  
When deploying a model-as-a-service: define a threat model (attacker knowledge, query budget, allowed norms), instrument telemetry (per-key query logs, latencies, anomalies), enforce rate & quota policies, prefer to expose limited outputs (top-k), and plan forensic / legal response. Regularly simulate extraction attacks (red-teaming) to measure practical risk. Integrate with [[model_serving_security|Model Serving Security]] and [[ai_supply_chain_security|AI Supply Chain Security]] processes.

**HU:**  
Modell-szolgáltatás bevezetésekor: definiáld a fenyegetési modellt (támadó tudása, lekérdezési büdzsé, normák), telepíts mérőeszközöket (kulcs-szintű lekérdezési naplók, késleltetések, anomáliák), érvényesítsd a rate & kvóta szabályokat, adj vissza korlátozott kimeneteket (top-k), és tervezz forenzikus/jogi választ. Rendszeresen végezz red-team kinyerési szimulációkat a gyakorlati kockázat mérésére. Integráld a folyamatot a [[model_serving_security|modell-szolgáltatás biztonsága]] és [[ai_supply_chain_security|MI-ellátási lánc biztonság]] folyamatokkal.

---

## 🔗 Related Vault topics / Kapcsolódó fejezetek

**EN:**  
See also [[model_inversion|Model Inversion]], [[membership_inference|Membership Inference]], [[adversarial_example_attacks|Adversarial Examples]], [[transferability|Transferability]], [[watermarking|Watermarking]], [[differential_privacy|Differential Privacy]], and [[model_serving_security|Model Serving Security]].

**HU:**  
Lásd még: [[model_inversion|Modell-inverzió]], [[membership_inference|Tagsági következtetés]], [[adversarial_example_attacks|Adverszáriális példák]], [[transferability|Átviteli jelenség]], [[watermarking|Vízjelezés]], [[differential_privacy|Differenciális adatvédelem]] és a [[model_serving_security|Modell-szolgáltatás biztonsága]] fejezeteket.

---

## 🧭 Review Questions / Ellenőrző kérdések

1. Explain the difference between functional extraction and parameter extraction — how do their query budgets and defenses differ?  
2. How does returning probability scores vs. top-1 labels affect extraction success? Provide reasoning based on the formal objective.  
3. Design an experiment (red-team) to estimate how many queries \(M\) an attacker would need to reach 90% fidelity on a classification API. What measurements would you collect?  
4. What combination of monitoring signals would you use to detect an ongoing extraction attempt in production? Why?  
5. Discuss trade-offs between model utility and hardening: when might you choose to expose a distilled public model vs. the high-fidelity private model?

---

> “A protected model is not just an algorithm — it’s a product wrapped in policy, telemetry, and economic friction.” 🔐
