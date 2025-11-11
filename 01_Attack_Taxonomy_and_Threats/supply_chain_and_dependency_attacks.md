---
version: "3.3"
section_type: "attack"
agent: "Principle Engineer"
---
# 🏗️ Supply Chain & Dependency Attacks

---

## 🌍 What Are Supply Chain Attacks in AI? / Mik azok az ellátási lánc támadások az MI-ben?

**EN:**  
Supply chain and dependency attacks target the *external components* that an AI system depends on — from open-source libraries and pre-trained models to data sources, APIs, and build pipelines. Instead of attacking the model directly, adversaries compromise the *inputs, dependencies, or tools* used to create or deploy it.  

In the AI context, this means that even if your model, data, and servers are secure, a single poisoned dependency — such as a malicious Python package, a tampered dataset, or a compromised model checkpoint — can silently undermine your entire system. ⚙️🧩

**HU:**  
Az ellátási lánc és függőségi támadások az MI-rendszerek *külső komponenseit* célozzák — ideértve a nyílt forráskódú könyvtárakat, előre tanított modelleket, adatforrásokat, API-kat és build-folyamatokat. A támadók nem közvetlenül a modellt, hanem annak *bemeneteit, függőségeit vagy fejlesztői eszközeit* fertőzik meg.  

Az MI-világban ez azt jelenti, hogy még ha a modell, az adat és a szerver biztonságos is, egyetlen fertőzött függőség — például egy rosszindulatú Python-csomag, manipulált adathalmaz vagy kompromittált modell-checkpoint — képes csendben aláásni az egész rendszert. ⚙️🧩

---

## 💡 Why They Matter / Miért veszélyesek

**EN:**  
These attacks exploit *trust assumptions*: developers implicitly trust the software supply chain — dependencies, models, and build artifacts — as benign. In practice, attackers exploit this trust to gain persistence, inject malicious code, or manipulate model behavior before deployment.  

AI systems amplify the impact because they integrate components from multiple ecosystems (PyPI, HuggingFace, DockerHub, npm, etc.), often updated automatically. A single poisoned link can cascade across cloud pipelines and production inference services.  

**HU:**  
Ezek a támadások a *bizalmi feltételezéseket* használják ki: a fejlesztők természetesnek veszik, hogy a szoftver-ellátási lánc (függőségek, modellek, build-artefaktumok) megbízható. A támadók ezt a bizalmat használják ki, hogy tartós hozzáférést szerezzenek, rosszindulatú kódot fecskendezzenek be, vagy még a bevezetés előtt manipulálják a modell viselkedését.  

Az MI-rendszerekben a hatás felerősödik, mert ezek számos ökoszisztéma (PyPI, HuggingFace, DockerHub, npm stb.) komponenseit integrálják, gyakran automatikus frissítésekkel. Egyetlen fertőzött láncszem végigfuthat a felhő-pipeline-okon és a produkciós inferencia szolgáltatásokon.  

---

## 🧩 Main Attack Surfaces / Fő támadási felületek

**EN:**  
1. **Package poisoning (Dependency confusion):** attacker publishes a malicious package with a higher version number or similar name; build systems install it automatically.  
2. **Pre-trained model tampering:** attacker uploads a model with hidden malicious behavior (e.g., embedded backdoor triggers).  
3. **Dataset poisoning:** public datasets modified before download (see [[data_poisoning|Data Poisoning]]).  
4. **Model checkpoint replacement:** attacker replaces or wraps model files in malicious loaders.  
5. **Container / build pipeline compromise:** CI/CD servers or Docker images altered to insert malicious dependencies.  
6. **API supply chain:** a compromised external API endpoint injects unexpected outputs or prompt instructions (see [[prompt_injection_and_rag_attacks|Prompt Injection]]).  
7. **Federated or collaborative learning sources:** compromised participants inject poisoned updates (see [[federated_learning_security|Federated Learning Security]]).

**HU:**  
1. **Csomagmérgezés (Dependency confusion):** a támadó rosszindulatú csomagot tesz közzé magasabb verziószámmal vagy hasonló névvel, amelyet a build-rendszer automatikusan telepít.  
2. **Előre tanított modellek manipulálása:** a támadó rejtett viselkedést (pl. backdoor-triggert) tartalmazó modellt tölt fel.  
3. **Adathalmaz-mérgezés:** a nyilvános datasetek módosítása letöltés előtt (lásd [[data_poisoning|Data Poisoning]]).  
4. **Model-checkpoint-csere:** a támadó lecseréli vagy becsomagolja a modellfájlokat rosszindulatú loader-ekbe.  
5. **Konténer / build-pipeline kompromittálása:** a CI/CD szerverek vagy Docker-képek manipulálása, hogy új függőségek kerüljenek be.  
6. **API-ellátási lánc:** kompromittált külső API végpontok váratlan kimeneteket vagy prompt-utasításokat fecskendeznek be (lásd [[prompt_injection_and_rag_attacks|Prompt Injection]]).  
7. **Federált vagy együttműködő tanulás forrásai:** fertőzött kliensek rosszindulatú frissítéseket küldenek (lásd [[federated_learning_security|Federált tanulás védelme]]).

---

## 🔬 Attack Examples / Példák

**EN:**  
- **Dependency confusion (PyPI/NPM):** In 2021, security researchers demonstrated how internal packages like `corp-utils` could be hijacked by publishing a public `corp-utils` with higher version number — the build pipeline fetched the wrong one.  
- **Model backdoor on HuggingFace:** an attacker uploads a transformer model fine-tuned with a hidden backdoor trigger phrase; anyone who downloads it unknowingly gets a compromised model.  
- **Container poisoning:** a malicious Docker image adds telemetry or crypto-mining code to the container used in model training.

**HU:**  
- **Dependency confusion (PyPI/NPM):** 2021-ben kutatók megmutatták, hogy belső csomagok (pl. `corp-utils`) eltéríthetők egy nyilvános, magasabb verziószámú `corp-utils` publikálásával — a build-pipeline tévesen ezt töltötte le.  
- **Model-backdoor HuggingFace-en:** a támadó feltölt egy finomhangolt transformer-modellt rejtett trigger-kifejezéssel; bárki, aki letölti, kompromittált modellt kap.  
- **Konténer-mérgezés:** egy rosszindulatú Docker-image telemetria- vagy kriptobányász-kódot ad hozzá a tanításhoz használt környezethez.

---

## ⚙️ Mitigation Strategies / Védekezési stratégiák

**EN:**  
### 1. Software supply chain hygiene  
- **Pin versions & hashes:** use exact version and hash pinning for all dependencies.  
- **Private package registries:** mirror or proxy public registries (PyPI, npm) via private trusted repositories.  
- **Dependency signing:** adopt signed packages (e.g., Sigstore, PEP 458/480).  
- **Static analysis & vulnerability scanning:** use [[sbom|Software Bill of Materials (SBOM)]] and automated scanners (e.g., Snyk, Trivy, Grype).

### 2. Model and data integrity  
- **Model signing and verification:** cryptographically sign model checkpoints; verify before deployment.  
- **Provenance tracking:** maintain metadata (creator, source URL, checksum). Integrate with [[watermarking|Watermarking & Provenance]].  
- **Secure dataset pipelines:** validate hashes and signatures for datasets; download from authenticated sources only.  
- **Isolated staging:** run pre-trained models and external data in sandboxed environments before production use.

### 3. CI/CD & container security  
- **Immutable builds:** enforce reproducible builds with deterministic dependencies.  
- **Secrets management:** isolate credentials from build agents; use [[zero_trust|Zero Trust]] principles.  
- **Container provenance:** pull only signed container images (Notary, cosign).  
- **Runtime attestation:** verify signatures and integrity of containers at runtime.

### 4. Monitoring & response  
- **Dependency drift monitoring:** alert when unpinned or new versions appear.  
- **Audit trails:** log dependency updates, downloads, and build metadata.  
- **Incident response playbooks:** define rollback and quarantine procedures for compromised artifacts.

**HU:**  
### 1. Szoftver-ellátási lánc higiénia  
- **Verziók és hashek rögzítése:** minden függőség pontos verziójának és hash-ének rögzítése.  
- **Privát csomag-regiszterek:** nyilvános (PyPI, npm) tükör vagy proxy megbízható privát repókon keresztül.  
- **Csomag-aláírás:** aláírt csomagok használata (pl. Sigstore, PEP 458/480).  
- **Statikus analízis & sebezhetőségi vizsgálat:** [[sbom|Software Bill of Materials (SBOM)]] és automatikus szkennerek (Snyk, Trivy, Grype).

### 2. Modell- és adat-integritás  
- **Modell-aláírás és verifikáció:** modell-checkpointok kriptográfiai aláírása és ellenőrzése bevezetés előtt.  
- **Eredetkövetés:** metaadatok (készítő, forrás-URL, checksum) karbantartása, integrálva a [[watermarking|vízjelezés és eredetkövetés]] rendszerrel.  
- **Biztonságos adatpipeline:** hashek és aláírások ellenőrzése adathalmazokra; csak hitelesített forrásból letöltés.  
- **Izolált tesztelés:** előre tanított modellek és külső adatok futtatása sandboxban produkció előtt.

### 3. CI/CD és konténer-biztonság  
- **Megváltoztathatatlan build:** determinisztikus, reprodukálható build-folyamatok.  
- **Titokkezelés:** hitelesítő adatok elszigetelése a build-ügynököktől; [[zero_trust|Zero Trust]] elvek alkalmazása.  
- **Konténer-eredet:** csak aláírt konténerképek letöltése (Notary, cosign).  
- **Futásidejű hitelesítés:** konténerek aláírásainak és integritásának ellenőrzése futásidőben.

### 4. Monitorozás és reagálás  
- **Függőség-eltérés figyelése:** riasztás új vagy nem rögzített verziók megjelenésekor.  
- **Audit-naplók:** függőség-frissítések, letöltések és build-metaadatok naplózása.  
- **Incidenskezelési eljárások:** visszagörgetési és karantén-folyamatok kompromittált komponensek esetére.

---

## 🔗 Integration with AI Governance / Kapcsolat az MI-irányítással

**EN:**  
Supply chain security must be embedded into [[ai_governance|AI Governance]] processes — including vendor vetting, continuous validation of external components, and formal risk classification for dependencies and third-party models. The use of [[zero_trust|Zero Trust]] architectures and SBOM documentation is now considered essential for regulated sectors (finance, healthcare, government).  

**HU:**  
Az ellátási lánc biztonságát az [[ai_governance|MI-irányítási]] folyamatokba kell beépíteni — ideértve a beszállítók ellenőrzését, a külső komponensek folyamatos validálását és a függőségek/formált modellek kockázati besorolását. A [[zero_trust|Zero Trust]] architektúra és az SBOM-dokumentáció alkalmazása ma már alapkövetelmény a szabályozott iparágakban (pénzügy, egészségügy, kormányzat).

---

## 🧭 Review Questions / Ellenőrző kérdések

1. How do supply chain attacks differ from direct model attacks like [[adversarial_example_attacks|Adversarial Examples]]?  
2. Describe how a dependency confusion attack could compromise an AI build pipeline.  
3. What measures ensure integrity of pre-trained models and datasets?  
4. Which CI/CD and container security controls can detect or prevent injection of malicious dependencies?  
5. How does SBOM contribute to AI system resilience and auditability?

---

> “In AI security, trust is a dependency — and every dependency is a potential betrayal.” ⚖️
