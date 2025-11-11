---
version: "3.2"
section_type: "defense"
agent: "Principle Engineer"
---
# 🧱 Runtime Isolation & Sandboxing

---

## 🌍 What Is Runtime Isolation? / Mi az a futásidejű izoláció?

**EN:**  
**Runtime isolation** means separating the execution of models, user code, or data flows so that one process cannot interfere with, observe, or compromise another.  
In AI systems, it protects against **code injection, model tampering, data exfiltration**, and **cross-tenant leakage** — especially when untrusted code, plugins, or third-party integrations run inside the same environment.  

Put simply: it ensures that *each model or user operates inside its own locked room*, unable to touch others. 🔒🤖  

**HU:**  
A **futásidejű izoláció** azt jelenti, hogy a modellek, felhasználói kódok és adatfolyamok futtatása egymástól elkülönítve történik, így egy folyamat nem zavarhatja, figyelheti vagy kompromittálhatja a másikat.  
Az MI-rendszerekben ez védi a rendszert a **kódbefecskendezéstől, modell-manipulációtól, adatlopástól** és a **bérlők közötti adatátfolyástól** — különösen akkor, ha nem megbízható bővítmények vagy harmadik fél kódjai futnak ugyanabban a környezetben.  

Egyszerűen: ez garantálja, hogy *minden modell vagy felhasználó a saját zárt szobájában működjön*, másokat nem érintve. 🔒🤖  

---

## 💡 Why It Matters / Miért kritikus

**EN:**  
Modern AI platforms often execute:  
- **User-submitted prompts or code** (e.g. notebooks, Python cells, RAG agents)  
- **Third-party extensions** (e.g. plugins, connectors)  
- **Model pipelines** with shared GPUs or memory  

Without isolation, an attacker could:  
- Escape the execution environment and access host resources  
- Steal API keys or model weights  
- Interfere with other users’ inference sessions  
- Inject malicious code into memory-shared components  

**HU:**  
A modern MI-platformok gyakran futtatnak:  
- **Felhasználói promptokat vagy kódot** (pl. notebookok, Python-cellák, RAG-agentek)  
- **Harmadik féltől származó bővítményeket** (pl. pluginok, connectorok)  
- **Megosztott GPU-val vagy memóriával dolgozó pipeline-okat**  

Izoláció nélkül a támadó képes lehet:  
- Kitörni a futtatási környezetből és hozzáférni a gazdagép erőforrásaihoz  
- API-kulcsokat vagy modell-súlyokat ellopni  
- Más felhasználók inferencia-folyamatait megzavarni  
- Rosszindulatú kódot befecskendezni a megosztott komponensekbe  

---

## 🧩 Sandboxing Explained / A sandboxolás lényege

**EN:**  
A **sandbox** is a controlled execution environment that enforces strict boundaries between the running code and the host system.  

Its goals:  
- Restrict system calls (file I/O, networking)  
- Limit memory and CPU consumption  
- Enforce container or VM boundaries  
- Intercept unsafe operations  

### Common Sandbox Technologies:
- **Containers (Docker, Podman)** — process-level isolation  
- **Virtual Machines (KVM, Firecracker)** — hardware-level isolation  
- **WebAssembly (WASM)** — lightweight, language-agnostic sandbox for model plugins  
- **Seccomp / AppArmor / SELinux** — syscall-level restrictions  
- **gVisor / Kata Containers** — user-space kernel sandboxes for cloud workloads  

**HU:**  
A **sandbox** egy kontrollált futtatási környezet, amely szigorú határokat szab a futó kód és a gazdagép között.  

Céljai:  
- Rendszerhívások (fájl, hálózat) korlátozása  
- Memória- és CPU-fogyasztás limitálása  
- Konténer- vagy VM-határok betartása  
- Bizonytalan műveletek elfogása  

### Gyakori sandbox technológiák:
- **Konténerek (Docker, Podman)** — folyamat-szintű izoláció  
- **Virtuális gépek (KVM, Firecracker)** — hardver-szintű izoláció  
- **WebAssembly (WASM)** — könnyű, nyelvfüggetlen sandbox modellbővítményekhez  
- **Seccomp / AppArmor / SELinux** — rendszerhívás-korlátozás  
- **gVisor / Kata Containers** — felhasználói térben futó kernel-sandboxok felhős környezetekhez  

---

## ⚙️ Isolation Models in AI Systems / Izolációs modellek az MI-ben

**EN:**  
1. **Inference Isolation** — each model runs in its own container or VM  
2. **GPU Context Isolation** — separate CUDA streams, enforce device memory partitioning  
3. **Agent Isolation** — each LLM agent or plugin runs in a sandboxed subprocess  
4. **User Session Isolation** — tenant-level separation of compute and storage  
5. **Code Execution Isolation** — restrict user-provided Python or shell commands in notebooks  

**HU:**  
1. **Inferencia-izoláció** — minden modell saját konténerben vagy virtuális gépben fut  
2. **GPU-kontektsus izoláció** — külön CUDA-szálak, memóriarészek elkülönítése  
3. **Agent-izoláció** — minden LLM-agent vagy plugin sandboxolt alfolyamatban fut  
4. **Felhasználói szekció izoláció** — bérlőnként elkülönített számítási és tárolási környezet  
5. **Kódfuttatás izoláció** — felhasználói Python vagy shell-parancsok korlátozása notebookokban  

---

## 🧮 Formal Concept / Formális megközelítés

**EN:**  
Let \( E_i \) represent the runtime environment of user \( i \).  
For strong isolation, we require:

$$
\forall i \ne j: \; \text{Access}(E_i, E_j) = \varnothing
$$

and for containment under compromise:

$$
\text{Impact}(Compromise(E_i)) \subseteq E_i
$$

Meaning: even if one environment is compromised, its effects are confined within its boundaries.  

**HU:**  
Legyen \( E_i \) a \( i \)-edik felhasználó futtatási környezete.  
Erős izoláció esetén igaz:

$$
\forall i \ne j: \; \text{Access}(E_i, E_j) = \varnothing
$$

és kompromittálás esetén:

$$
\text{Impact}(Compromise(E_i)) \subseteq E_i
$$

Vagyis: még ha egy környezet kompromittálódik is, a hatása kizárólag abban maradjon.  

---

## 🛡️ Security Benefits / Biztonsági előnyök

**EN:**  
- Containment of malicious code or model behavior  
- Protection from privilege escalation  
- Prevention of lateral movement across users or services  
- Safer evaluation of untrusted inputs and plugins  
- Enhanced compliance for multi-tenant cloud environments  

**HU:**  
- Rosszindulatú kód vagy modell-viselkedés elszigetelése  
- Jogosultság-kiterjesztési támadások elleni védelem  
- Oldalirányú mozgás megakadályozása felhasználók vagy szolgáltatások között  
- Nem megbízható inputok és bővítmények biztonságos tesztelése  
- Megfelelőség javítása több-bérlős felhőkörnyezetekben  

---

## 🔗 Integration With Other Defenses / Kapcsolatok más védelmekkel

**EN:**  
Runtime isolation reinforces:  
- [[model_serving_security|Model Serving Security]] — protects APIs and inference nodes  
- [[prompt_injection_and_rag_attacks|Prompt Injection Defense]] — confines malicious retrievals  
- [[ai_supply_chain_security|AI Supply Chain Security]] — validates runtime provenance  
- [[observability_and_monitoring|Observability & Monitoring]] — tracks isolation breaches  
- [[zero_trust|Zero Trust Architecture]] — enforces least-privilege at runtime  

**HU:**  
A futásidejű izoláció erősíti:  
- [[model_serving_security|Modell-szolgáltatás biztonsága]] — API-k és inferencia csomópontok védelme  
- [[prompt_injection_and_rag_attacks|Prompt Injection elleni védelem]] — rosszindulatú visszakeresések elkülönítése  
- [[ai_supply_chain_security|MI-ellátási lánc biztonsága]] — futtatási eredet validálása  
- [[observability_and_monitoring|Observability és monitoring]] — izolációs megsértések nyomon követése  
- [[zero_trust|Zero Trust architektúra]] — legkisebb jogosultság futásidőben  

---

## 🧠 Best Practices / Legjobb gyakorlatok

**EN:**  
- Use **container or VM isolation per model** or per user.  
- Enforce **read-only file systems** inside inference sandboxes.  
- Block **outbound network access** except to trusted domains.  
- Monitor **syscalls and resource limits** using AppArmor or Seccomp.  
- Apply **runtime attestation** to verify code integrity (see [[model_watermarking_and_verification|Watermarking & Verification]]).  
- Use **ephemeral sandboxes** that reset after each session.  
- Integrate isolation logs into your [[observability_and_monitoring|Observability Stack]].  

**HU:**  
- Használj **konténer- vagy VM-izolációt** modellenként vagy felhasználónként.  
- Érvényesíts **csak olvasható fájlrendszert** az inferencia-sandboxokban.  
- Tiltsd a **kimenő hálózati hozzáférést**, kivéve megbízható domainekre.  
- Figyeld a **rendszerhívásokat és erőforrás-határokat** AppArmor vagy Seccomp segítségével.  
- Alkalmazz **futásidejű attesztációt** a kód integritásának ellenőrzéséhez (lásd [[model_watermarking_and_verification|Vízjelezés és verifikáció]]).  
- Használj **efemer sandboxokat**, amelyek minden munkamenet után törlődnek.  
- Integráld az izolációs naplókat az [[observability_and_monitoring|Observability-rendszerbe]].  

---

## ⚖️ Trade-offs / Kompromisszumok

**EN:**  
- Strong isolation reduces performance and resource sharing efficiency.  
- Fine-grained sandboxing increases operational complexity.  
- Overly permissive isolation breaks security; overly strict breaks usability.  
- Balancing resource efficiency vs security is a continuous process.  

**HU:**  
- Az erős izoláció csökkenti a teljesítményt és a megosztott erőforrások hatékonyságát.  
- A finomszemcsés sandboxolás növeli az üzemeltetési komplexitást.  
- A túl megengedő izoláció gyengíti a védelmet, a túl szigorú pedig rontja a használhatóságot.  
- Az erőforrás-hatékonyság és biztonság közötti egyensúly folyamatos kihívás.  

---

## 🧭 Review Questions / Ellenőrző kérdések

1. Define runtime isolation and explain how it differs from static sandboxing.  
2. What are the main attack vectors mitigated by sandboxing in AI inference environments?  
3. Compare container-based and VM-based isolation in terms of security vs performance.  
4. How can runtime attestation strengthen sandbox integrity?  
5. Design a sandboxing strategy for a multi-tenant RAG system using external connectors.  

---

> “In AI security, true trust is built on isolation — not assumptions.” 🧱
