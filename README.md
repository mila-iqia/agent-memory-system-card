<p align="center">
  <img src="assets/ams-card-logo.png" alt="AMS Card logo" width="112">
</p>

<h1 align="center">Agent Memory System Card (AMS Card)</h1>

A proposed standard documentation template for **memory systems** used by AI agents and memory-augmented models, plus two worked examples.

Inspired by model cards and dataset cards, an *Agent Memory System Card (AMS Card)* is a shared, structured document for describing a memory system. It makes clear what a system remembers, how memory is represented, how information enters and leaves the system, how memory affects behavior, which performance claims are supported, and which operational and privacy risks remain.

This template is meant for both memory built directly into AI systems and third-party memory systems used by them, including raw-text stores, RAG-style retrieval systems, vector or graph memory, profile stores, latent or parametric memory, multimodal memory, and hybrid architectures. It is meant to be read and filled out by the people who build, integrate, evaluate, deploy, govern, or are affected by a memory system.

We are sharing this repository publicly to get feedback on the format, scope, terminology, and coverage of the proposal before wider adoption.

## What this repository contains

| File | Description |
| --- | --- |
| [`templates/ams-card-template.md`](templates/ams-card-template.md) | The blank AMS Card template in GitHub Markdown. Copy this to document your own system. |
| [`templates/ams-card-template.pdf`](templates/ams-card-template.pdf) | Typeset PDF of the same template. |
| [`examples/milamem/mila_mem_card.md`](examples/milamem/mila_mem_card.md) | A populated AMS Card for *MilaMem*, an experimental research prototype. |
| [`examples/MozMem/MozMem Template.md`](examples/MozMem/MozMem%20Template.md) | A populated AMS Card for *MozMem*, a proposed user-sovereign memory system that does not exist yet. |
| [`feedback-questionnaire.md`](feedback-questionnaire.md) | Text version of the public feedback questionnaire. |

## Feedback requested

We are proposing the AMS Card as a standard documentation artifact for AI systems with memory and for third-party memory systems used by them. Feedback is especially useful on missing sections, unclear terminology, adoption barriers, privacy and governance coverage, and examples of real systems this template should handle better.

You can provide feedback by filling out this [feedback form](https://forms.gle/TC8JLYi8YTZrmiDF9) (preferred), or by opening a GitHub issue. The questions are also listed in [`feedback-questionnaire.md`](feedback-questionnaire.md). See [`CONTRIBUTING.md`](CONTRIBUTING.md) for how we take feedback; we are not accepting pull requests from external collaborators at this time.

## When to use an AMS Card

Fill out an AMS Card whenever you build, ship, or evaluate a component that preserves and reuses information over time — for example a raw-text store, a RAG-style retrieval system, a vector or graph memory, a profile store, a latent or parametric memory, a multimodal memory, or a hybrid architecture. The template is deliberately broad so it can describe any of these without forcing a system into a category it does not implement.

## How to fill out the template

1. Copy [`templates/ams-card-template.md`](templates/ams-card-template.md) into your own project.
2. Work top to bottom. Start with the sections that describe the system as implemented (metadata, interfaces, memory capabilities, architecture, lifecycle, dependencies), then document the evidence around performance, limitations, maintenance, governance, and privacy.
3. Replace every `[bracketed italic]` placeholder with your own content.
4. Use `[More Information Needed]` when a field is unknown or not yet evaluated, and `Not Applicable` when a field genuinely does not apply to your design. Prefer stating why a section does not apply over deleting it.

The template's own **Directory** section is a reader's guide: it points end users, auditors, and developers to the sections most relevant to them.

## How to read the examples

[`examples/milamem/mila_mem_card.md`](examples/milamem/mila_mem_card.md) shows a completed card for a current research prototype, including preliminary evaluation numbers. [`examples/MozMem/MozMem Template.md`](examples/MozMem/MozMem%20Template.md) shows a completed card used as a design reference for a system that has not been built.

Treat MilaMem results as prototype evidence, not production claims. Treat MozMem as a specification, not a shipped product.

## License

Released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](LICENSE). Names, logos, and trademarks remain subject to their owners' policies.

## Collaborating organizations

<p align="center">
  <a href="https://mila.quebec/"><img src="assets/mila-logo-purple.png" alt="Mila" height="72"></a>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://www.mozilla.org/"><img src="assets/mozilla-logo-black.svg" alt="Mozilla" height="72"></a>
</p>

## Acknowledgements

We thank [Koodos Labs](https://koodoslabs.com/), [Dr. Ilan Strauss](https://www.ai-disclosures.org/), [Gabe Goodhart](https://research.ibm.com/people/gabe-goodhart) (AI Foundations at IBM), and [Zep](https://www.getzep.com/) for comments and discussion that improved this template.
