*Note MozMem is a proposal for what a User Sovereign Memory System has to get right, and what it should be willing to give up to do it. It does not exist ... yet*

### **AMS Card Template for MozMem**

**Design principles.** Every requirement in this card implements one of three commitments.

1. **Memory belongs to the user, not the provider.** The browser is its home. Models are interchangeable computers; the memory is not.  
2. **Contextual Integrity is architectural, not behavioral.** Boundaries between work and personal, persona and persona, tool and tool are enforced and auditable rather than requested.  
3. **Agents protect users without asking them.** Sovereignty means the system gets context decisions right, not that it offloads them as permission prompts. Where that confidence is not reachable, the gap is documented plainly rather than closed with a dialog box.

### **System Overview**

* **System summary:** A specification for agent memory in which the persistent context an agent carries about a user is owned, inspectable and revocable by that user. MozMem remembers user facts, preferences, task history and tool outcomes, bound to the context in which each was learned. It is not a retrieval primitive; it is a boundary primitive with retrieval attached.  
* **Performance evidence:** None. Nothing is built. Performance requirements are stated below as thresholds MozMem must clear against a no-memory and an in-context baseline on the MAPB suite.   
* **Contextual integrity evidence:** None yet. The requirement is that cross-context retrieval fails closed and that every such failure is observable in a log the user can read.  
* **Inspection, editing, and deletion:** Every entry must be inspectable in human-readable form, editable in place, and deletable with a hard-deletion guarantee. Entries the user cannot read must not exist.  
* **Memory preferences:** Deny-list rules must be enforced before storage rather than at retrieval. A do-not-remember instruction that only filters reads is not compliant.  
* **Portability:** Full export in a documented, non-proprietary format, including provenance and context labels, sufficient to reconstitute the memory in another compliant system. Export must not require the provider's cooperation.  
* **Data governance and residency:** Default residency is the user's own device. Any egress is opt-in, per-destination, and visible in the log.

### **System and Deployment Details**

#### **Deployment Context**

* **Shared by:** Mozilla, with Mila  
* **System type:** Browser memory and on-device memory, with a self-hostable server profile  
* **Deployment mode:** Local and on-device by default; self-hosted where multi-device sync is required. Managed-service deployment is out of scope for the reference.  
* **Primary users:** End users, with developers and agent builders as integrators  
* **Primary affected users:** The person the memory is about. MozMem treats that person as the data subject and the principal, not as the operator's customer.

#### **Sources**

* **Repository:** `[to be created]`  
* **Documentation:** `[to be created]`  
* **Technical reference:** `[to be published with the repository]`  
* **Demo or service endpoint:** Not Applicable  
* **Changelog:** `[to be created]`

### **Intended Use**

#### **Direct Use**

Personal agent memory across sessions and across applications, on the user's own hardware, for a single human principal with multiple contexts (personal, work, per-persona, per-origin).

#### **Downstream Use**

As the memory layer beneath interchangeable model backends. MozMem assumes the model is fungible and the memory is not. Integration is by retrieval API and MCP server, with the memory outliving any particular model or agent harness.

#### **Out-of-Scope Use**

* Multi-principal or shared-account memory where the data subject is ambiguous.  
* Provider-side personalization, ad targeting, or any use where the operator benefits from what is remembered.  
* Any deployment where the operator can read memory the user cannot.  
* Regulated clinical, legal or financial recordkeeping without additional evaluation.

### **Core Memory Capabilities**

#### **Remembered Information**

* **Information types:** User facts, preferences, task history, tool outputs, environment state  
* **Temporal scope:** Cross-session and long-term, with per-context retention policy  
* **Granularity:** Facts and entities with provenance, over an episodic log  
* **Persistence:** Persistent until deletion, subject to per-context policy

#### **Functional Role**

Personalization, task continuity, and reduced repetition, with the specific property that continuity does not require the provider to retain anything.

Descriptors that apply: factual memory, retrieval-augmented memory, working memory. **Parametric and latent memory are deliberately out of scope for the reference**: memory encoded in weights or hidden states cannot satisfy the inspection and hard-deletion requirements below. A system may add them; it may not use them to hold anything the user has a right to delete.

#### **Capability Boundaries**

* **What the system does remember well:** Facts and preferences that the user would recognize as being about them, with the context in which each was learned.  
* **What the system does not remember or does not aim to remember:** Anything captured from a low-trust source without the user's context; anything in an ephemeral context; anything on a deny list.  
* **Known failure modes:** Under-retention by design. MozMem will forget things a less constrained system would keep. That is the intended failure direction.

### **Memory Form and Architecture**

#### **Representation**

* **Representation form:** Structured text with vector embeddings for retrieval. The structured text is authoritative; the embeddings are an index and are rebuildable from it.  
* **Human readability:** Human-readable. This is a requirement, not a property. If an entry cannot be rendered to the user in a form they can understand, it must not be stored.  
* **Addressability:** By ID, semantic search, temporal lookup, and by context label  
* **Structure:** Episodic log with a derived semantic layer, partitioned by context  
* **Storage location:** Local encrypted store, keyed to the user

#### **Agent or Model Coupling**

* **Integration point:** Retrieval API and MCP server, external to the agent  
* **Invocation pattern:** Agent-triggered read; policy-triggered write at task boundaries  
* **Read path:** The agent requests memory for a declared context. The store returns only entries whose context labels permit that flow. There is no path that returns unfiltered memory.  
* **Write/update path:** Candidate entries are checked against deny-list and context policy before storage, not after.  
* **Separation from agent:** External component. Memory must survive the agent that wrote it.

#### **Data Sources**

* **Input sources:** User messages, browser content, tool outputs, task outcomes, explicit user saves  
* **Collection triggers:** Selected interactions and explicit save. Not every interaction.  
* **Preprocessing:** Extraction, context labelling, deny-list filtering, embedding

#### **Modality Support**

* **Supported modalities:** Text, browser state, structured records, tool traces  
* **Cross-modal alignment:** Not required for the reference. Where added, cross-modal links inherit the strictest context label of their sources.

### **Memory Lifecycle**

#### **Capture or Formation**

* **What gets captured:** Facts the user would expect to be remembered, in the context in which they were shared  
* **How capture decisions are made:** Rules plus a classifier, with the user able to see and override the rule that fired  
* **Transformation before storage:** Structured extraction, context labelling, redaction  
* **Quality controls:** Schema checks, deduplication, provenance required on every entry. **An entry without provenance is invalid**, because an entry the user cannot trace is one they cannot meaningfully dispute.

#### **Maintenance or Evolution**

* **Update behavior:** Append-only log with a derived current view. History is retained so corrections are auditable.  
* **Conflict handling:** User authority first, then recency, then provenance. An authenticated user correction outranks any later agent, tool or third-party input, permanently.  
* **Consolidation:** Summarization permitted only where the summary carries the provenance of its sources and the sources remain individually deletable.  
* **Forgetting or pruning:** Manual deletion, per-context expiration, user-defined policy. No capacity-based eviction of user-authored entries.  
* **Versioning:** Entries and context policies are versioned.

#### **Access, Retrieval, or Use**

* **Access method:** Semantic retrieval within a context, plus direct lookup  
* **Retrieval timing:** At task start and on demand  
* **Query construction:** Agent-generated, with the declared context attached  
* **Ranking or selection:** Access policy first, then similarity and recency. Policy is not a re-ranking signal; it is a gate applied before ranking.  
* **Post-processing:** Policy filtering, citation generation  
* **Output format:** Structured facts with provenance, so the agent can cite what it used

### **Performance and Evaluation**

#### **Performance Claims**

No claims. This section states the thresholds MozMem must meet.

* **Claimed benefits:** Reduced user repetition, task continuity, personalization without provider retention  
* **Evidence level:** None. Requirements only.  
* **Compared against:** No-memory baseline and in-context baseline, plus at least one self-hostable third-party system

#### **Evaluation Setup**

* **Benchmarks or tasks:** MAPB, on both axes  
* **Evaluation level:** Component-level memory evaluation and system-level agent evaluation  
* **Environment:** Browser and tool use  
* **Datasets or traces:** MAPB suite  
* **Metrics:** Task success, recall, edit success, deletion success, retention adherence, cross-context leakage rate, latency, storage growth  
* **Reproducibility:** Code, configuration, seeds, prompts and model versions must all be published. A privacy claim that cannot be reproduced is a marketing claim.

#### **Memory Quality**

* **Capture quality:** Must not silently capture what it cannot show the user  
* **Update quality:** User corrections must survive subsequent conflicting inputs indefinitely  
* **Use quality:** Must not surface an entry outside the context that produced it, at any similarity score  
* **Calibration:** Must be able to report that it has no relevant memory rather than returning weak matches  
* **Grounding and provenance:** Every returned entry carries its source event and timestamp

#### **Efficiency and Scalability**

* **Latency:** Write latency is expected to be worse than unconstrained systems, because policy and redaction run before storage  
* **Storage footprint:** Expected to be larger, because provenance and history are retained per entry  
* **Compute cost:** Extraction, embedding, and per-write policy evaluation  
* **Scale tested:** `[to be established]`  
* **Degradation at scale:** Retrieval quality must not be recovered by relaxing context boundaries as the store grows

#### **Utility Trade-offs: the privacy tax, stated deliberately**

This is the section the reference exists for. **MozMem accepts a measurable performance cost in exchange for properties that cannot be added later.** Stating where in advance is what makes the card a position rather than a wish.

**Where MozMem must score at or near the top of any field it is measured against:**

* Transparency and completeness of inspection  
* Editability, and the durability of user corrections  
* Deletion guarantees, meaning hard deletion rather than removal from retrieval  
* Contextual integrity and cross-context leakage  
* Retention adherence  
* Portability

**Where MozMem is expected to score worse, and that is the correct outcome:**

* **Raw recall**, against systems that retrieve across all contexts. A system that answers from the user's work memory during a personal task scores better on recall and has failed the actual test.  
* **Write latency**, because deny-list and context checks run before storage rather than as a retrieval filter.  
* **Storage footprint**, because provenance and correction history are kept per entry.

**Where a worse score is not acceptable at any tradeoff:** contextual integrity. Performance gains bought by relaxing context boundaries are not a tradeoff, they are a different product.

**The operational test, applied throughout:** *would this surprise the user?* If yes it is a violation, regardless of what the consent flow said.

### **Limitations and Risks**

#### **Technical Limitations**

Nothing is built. Beyond that: the inspection and hard-deletion requirements rule out parametric and latent memory for anything user-owned, which forecloses a set of efficiency techniques. Per-write policy evaluation is a cost that does not amortize.

#### **Behavioral Risks**

Under-retention and fragmented context, both by design. A user operating across many contexts will experience an agent that knows less than a provider-hosted equivalent. This is the risk MozMem accepts, and the one it must be honest about rather than engineer around by widening boundaries.

#### **Domain and User Limitations**

Not validated anywhere. Single-principal only. Multi-device sync is unspecified in the reference and is where sovereignty claims are hardest to keep.

#### **Recommendations**

Build the smallest thing that passes the contextual integrity and deletion tests before optimizing anything else. Those two properties are architectural and cannot be retrofitted; recall and latency can.

### **Maintenance and Governance**

#### **Updates**

* **Update cadence:** `[to be established]`  
* **Backward compatibility:** Export format must be stable across schema versions, because portability that breaks on upgrade is not portability  
* **Migration support:** Migration must never require sending memory to a provider

#### **Monitoring**

* **Runtime monitoring:** Write logs, deletion logs, privacy events, cross-context denials  
* **Audit logs:** The user can read the full log. **The operator has no log the user cannot see.** This is the single clearest structural difference from provider-hosted memory.  
* **User feedback channels:** Corrections and deletion requests, both of which are first-class operations rather than support tickets

#### **Model and Dependency Information**

* **Base models:** Interchangeable by design. No memory behavior may depend on a specific model.  
* **Embedding models:** Local, swappable; the store must be rebuildable under a new embedding model without loss  
* **Rerankers or classifiers:** Local  
* **Databases and storage systems:** Local encrypted store  
* **External services:** None required. A MozMem that stops working offline is not MozMem.

### **Privacy, Sovereignty, and Safety**

#### **Privacy Definition Used**

* **Privacy framing:** Contextual integrity and individual data sovereignty together, with the privacy tax measured and published rather than assumed away. Privacy is evaluated **through the user's lens**, not as provider-side PII detection. The question is not whether an obvious sensitive field was exposed, but whether the flow matched what the user expected.

#### **Data Sensitivity**

* **Sensitive data categories:** All categories may enter, because a personal agent sees a personal life. The control is context, not category.  
* **Default handling of sensitive data:** Policy-dependent by context, with deny-list enforcement before storage  
* **Inferred sensitive attributes:** MozMem must not derive and persist traits the user did not state, unless the derivation is shown to them and is deletable as an entry in its own right. **Silent profile derivation is the specific practice this reference exists to rule out.**

#### **Transparency**

* **User inspection:** Yes, completely  
* **Completeness of inspection:** All entries  
* **Provenance:** Source event, timestamp, context label and transformation history on every entry  
* **Inference tracing:** Derived entries name the entries they came from  
* **Hidden state policy:** No hidden memory. No private profile. No latent state holding anything a user could ask to delete. This is a hard constraint, and it is the one most systems fail.

#### **User Control, Editability, and Erasability**

* **Edit support:** Direct edit  
* **Deletion support:** Entry, session, entity, context and provenance deletion  
* **Deletion guarantees:** Hard deletion, including from indexes, embeddings and backups. Tombstoning is not deletion. Removal from retrieval is not deletion.  
* **Export or portability:** Full export including provenance and context labels  
* **User authority:** Authenticated user corrections override all later inputs, permanently

#### **Contextual Integrity**

* **Context boundaries:** Persona, workspace, application, origin, sensitivity level, task  
* **Boundary enforcement:** Namespace isolation and encryption keys, enforced at the store. **Architectural, not behavioral**: boundaries held by prompt instructions or model cooperation do not count, in the lineage of Firefox containers and profiles.  
* **Cross-context sharing:** Denied by default. Permitted flows are declared, per pair of contexts, and logged when used.  
* **Low-trust content handling:** Web pages, documents and tool outputs cannot write memory outside the context in which they were encountered, and cannot trigger retrieval from another context. Prompt injection must not be able to reach memory the injecting context could not otherwise read.

#### **Retention Policy Adherence**

* **Retention policy support:** User-defined, per context  
* **Deny-list or do-not-remember rules:** Enforced before storage  
* **Ephemeral contexts:** Private browsing and task-local contexts are excluded from durable memory, with no exceptions and no recovery path  
* **Auto-expiration:** Per-context time-based deletion  
* **Backup and log retention:** Deleted memory does not survive in logs, traces, analytics or backups. If it does, it was not deleted.

#### **PII and Sensitive Information Handling**

* **PII detection:** Rules plus classifier plus user labels, with user labels authoritative  
* **PII action:** Policy-dependent by context. Note that MozMem's primary control is not PII redaction. **Redacting a phone number while allowing a work fact into a personal context misses the actual privacy failure.**  
* **Structural memory after redaction:** Structure retained, values removed, redaction visible to the user

#### **Security and Adversarial Robustness**

* **Threat model:** Prompt injection, cross-origin extraction, covert profiling, malicious tools, insider access, account compromise. **The operator is inside the threat model**, which is what distinguishes this from a provider-hosted system's threat model.  
* **Adversarial tests:** Attempts to force retention, bypass deletion, extract context-restricted memory, induce silent profiling, or overwrite user corrections  
* **Access controls:** Local key custody, per-context encryption, audit logging the user can read  
* **Incident response:** User notification is the first step, not the last

#### **Privacy Evaluation**

* **Privacy benchmarks or audits:** MAPB transparency, mutation integrity, contextual integrity, retention adherence and adversarial tests. Independent review before any launch claim.  
* **Known privacy risks:** Multi-device sync is the weakest point in the design. Any sync path is a potential egress and the reference does not yet specify one.  
* **Mitigations:** `[to be specified with the sync design]`  
* **Residual risk:** A local-first system moves risk from the provider to the endpoint. Device compromise becomes the dominant threat, and MozMem must say so rather than claim the risk was eliminated.

### **Citation**

* **BibTeX:** `[More Information Needed]`  
* **APA or plain-language citation:** Mozilla and Mila, *MozMem: a reference card for sovereign agent memory*, 2026\.

### **More Information**

This card is a specification rather than a record of a system. The requirements above are written so that a builder can implement against them and a reviewer can score the result on the same axes used for any other AMS Card. Disagreement with a specific threshold is the intended response; the card is more useful contested than agreed.

* **Repository and issue tracker:** `[to be created]`  
* **Contact:** `[to be added with the repository]`

---

## **Structured Index Record**

| Field | Value |
| ----- | ----- |
| `memory_system_name` | MozMem |
| `version` | reference-0.1 |
| `developers` | Mozilla, Mila |
| `release_date` | 2026-09-04 |
| `license` | `[to be set, open source]` |
| `homepage` | `[to be created]` |
| `tags` | `memory-system`, `agent-memory`, `sovereign-memory`, `reference-specification` |
| `memory_forms` | raw-text, vector, key-value |
| `memory_functions` | user facts, preferences, experience traces, working context |
| `modalities` | text, browser state, structured data, tool traces |
| `supported_interfaces` | API, SDK, MCP server |
| `evaluation_status` | not evaluated |
| `privacy_review_status` | not reviewed |

