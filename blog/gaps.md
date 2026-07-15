# Blog Post and Repository Alignment Analysis

## Scope and Method

This review compares [the Mozilla blog draft](mozilla_blog.md) with the public artifacts currently present in this repository: the [README](../README.md), [AMS Card template](../templates/memory-card-template.md), [fictional MilaMem example](../examples/milamem/memory-card.md), and [feedback questionnaire](../feedback-questionnaire.md). It does not verify claims about the publishing process, Mozilla's relationship with Mila, or artifacts hosted outside this repository.

## Publication Blockers

### 1. The described single-sheet card is not in the repository

**Blog claim.** The post says that the AMS Card has a top-level, at-a-glance “single sheet” with five dimensions: privacy, performance, user control, compartmentalization, and portability. It then describes the current template as the long-form card beneath it.

**Repository reality.** The repository contains one detailed, long-form Markdown/PDF template. Its `Overview` is a compact metadata table, not a reader-facing single-sheet assessment, and it does not present ratings, shades, plain-language verdicts, or a fixed five-dimension summary.

**Why it matters.** This is the post's clearest description of the product being published. A reader following the repository link will not find the primary artifact the post says exists.

**Recommended resolution.** Either add and link a clearly labelled draft single-sheet companion, or revise the post to describe the shipped artifact accurately: a long-form, structured documentation template with a compact metadata overview. Do not imply that the five dimensions currently appear as a common comparison surface unless that surface is published.

### 2. “Technical design document” and “criteria” are not published artifacts

**Blog claim.** “What we're publishing today” includes “the technical design document” and “the criteria we're using.”

**Repository reality.** The template explains its fields and contains a glossary, suggested privacy framings, and permitted values. These are useful design guidance, but there is no separately identifiable technical-design document or criteria/rubric file in the repository.

**Why it matters.** Readers will reasonably expect documents they can inspect. Calling embedded field guidance “criteria” also suggests a scoring or evaluation methodology that is not yet available.

**Recommended resolution.** Publish and link those documents, or change this to “a draft AMS Card template, field definitions, and a worked fictional example.” If the intended material is embedded in the template, link directly to the relevant sections and describe it as draft guidance rather than a completed criterion set.

### 3. The post promises a privacy-performance trade-off that the card does not yet require

**Blog claim.** The post argues that the central missing evidence is what happens to performance when privacy protections are increased, and says the card makes such trade-offs comparable.

**Repository reality.** The template separately documents performance evidence, privacy review/evaluation, privacy risks, and several general utility trade-offs. It does not require a system to measure privacy configurations against a shared performance baseline, report the strength of controls, or disclose the resulting privacy-versus-performance trade-off.

**Why it matters.** This is the blog's strongest substantive promise and differentiator. The current card can support a qualitative discussion of the issue, but it cannot consistently substantiate the proposed comparison across systems.

**Recommended resolution.** Either add a required trade-off section or matrix to the template, with configuration, control, metric, baseline, and residual-risk fields, or soften the post to say that this is a key gap the project intends to address rather than a comparison the present template delivers.

## Material Framing Gaps

### 4. The five blog dimensions are only partially standardized in the template

The template has strong fields for privacy, user control, compartmentalization, and portability:

- Privacy: sensitivity handling, contextual integrity, retention, PII handling, and adversarial robustness.
- User control: inspection, editing, deletion guarantees, export, and user authority.
- Compartmentalization: context boundaries, boundary enforcement, and cross-context sharing.
- Portability: an export/portability field and operational trade-offs including portability and vendor lock-in.
- Performance: performance claims, evaluation setup, memory quality, and efficiency/scalability.

However, these are dispersed through the long-form card and expressed mostly as open narrative fields. There is no required normalized value, minimum evidence threshold, or cross-card aggregation rule for any of the five dimensions. “Compartmentalization” is not used as a template term; the more precise repository language is “contextual integrity” and “context boundaries.”

**Recommended blog change.** Name the repository's actual terms, especially contextual integrity, rather than treating compartmentalization as an already-established card label. Describe the dimensions as areas the template documents, not as completed ratings.

### 5. The post underrepresents the card's broader technical and governance scope

The blog mostly frames the card as a user-choice and privacy-performance comparison instrument. The template additionally supports:

- many memory forms, including raw-text, retrieval, graph, profile, latent, parametric, multimodal, and hybrid memory;
- the full lifecycle of capture, maintenance, conflict handling, pruning, retrieval, and coupling to an agent or model;
- intended and out-of-scope use, capability boundaries, and behavioral risks;
- reproducibility, dependency disclosure, monitoring, audit logs, migration, and incident response;
- explicit evidence levels, privacy-review status, and separate privacy-evaluation methods.

**Recommended blog change.** Add one concise passage explaining that the long-form card is designed for builders, integrators, auditors, and affected users, and that it documents architecture, lifecycle, evidence, operational governance, and privacy controls. This better explains why the artifact is longer than a consumer-facing comparison card.

### 6. The post's meaning of “sovereign” is narrower than the template's actual treatment

The post defines sovereignty primarily as memory living with the user and user choice over what an agent may release. The template's “individual data sovereignty” additionally covers verifiable visibility, inspection, correction, export, deletion, user authority over conflicting inputs, retention, and information flows across contexts. It also recognizes that some memory forms are not fully inspectable or editable.

**Recommended blog change.** Avoid implying that local storage is a universal or required property of the card. Expand the definition to the template's control and accountability concepts, while acknowledging that feasibility differs for latent and parametric memory. This makes the claim more technically accurate and more inclusive of the memory systems the template is built to document.

## Accuracy and Launch-Process Corrections

### 7. The feedback survey has 12 numbered questions, not ten

**Blog claim.** The post calls it a “Ten questions, about five minutes” survey and later repeats “ten-question survey.”

**Repository reality.** The questionnaire contains 12 numbered prompts. Several are conditional or optional, but the discrepancy is visible to anyone comparing the post with the linked form/text.

**Recommended resolution.** Say “a short survey” or update the count consistently. Confirm the actual hosted form and the time estimate before publication.

### 8. The three-week comment window is not documented in the repository

**Blog claim.** The post announces a three-week open comment window, followed by closing comments and iterating on feedback.

**Repository reality.** The README invites issues, repository comments, and form responses, but gives no window, close date, handling policy, or distinction between a time-bounded consultation and ongoing issue submission.

**Recommended resolution.** Add the opening/closing dates and feedback-handling plan to the README or an issue, then link it from the post. If issues remain open after the consultation, say so explicitly rather than saying “we'll close comments.”

### 9. The post needs concrete links and an attribution check

The draft still contains the placeholder “Link to the github repo.” The post also makes an institutional collaboration claim and says the work has occurred over several months; neither is evidenced by this code repository.

**Recommended resolution.** Replace the placeholder with the canonical repository URL, link the feedback form and issue tracker, and obtain approval for the Mozilla/Mila wording and all launch commitments from the responsible teams.

### 10. The questionnaire currently links to a differently named repository

**Repository reality.** The questionnaire links to `https://github.com/mila-iqia/agent-memory-card`, but this repository's configured canonical remote is `https://github.com/mila-iqia/agent-memory-system-card.git`.

**Why it matters.** A reader reaching the form from the post may encounter a dead or unintended repository link, weakening the call for feedback.

**Recommended resolution.** Update the questionnaire link to `https://github.com/mila-iqia/agent-memory-system-card` and use that same canonical URL in the post.

## Suggested Publication Positioning

The repository supports a strong, accurate announcement if it is positioned as a public draft of a long-form documentation standard, accompanied by a fictional worked example and feedback questionnaire. The post should present the one-sheet comparison view, open benchmark, reference implementation, and working group as future work unless each is separately published or formally committed. The most credible near-term claim is not that the card already grades systems; it is that it makes the evidence and unresolved trade-offs necessary for future comparison more visible and reviewable.
