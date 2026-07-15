<p align="center">
  <a href="https://mila.quebec/"><img src="assets/mila-logo-purple.png" alt="Mila" height="100"></a>
</p>

<h1 align="center">Agent Memory System Card (AMS Card)</h1>

A proposed standard documentation template for **memory systems** used by AI agents and memory-augmented models, plus a fully worked (fictional) example.

Inspired by model cards and dataset cards, an *Agent Memory System Card (AMS Card)* is a shared, structured document for describing a memory system. It makes clear what a system remembers, how memory is represented, how information enters and leaves the system, how memory affects behavior, which performance claims are supported, and which operational and privacy risks remain.

This template is meant for both memory built directly into AI systems and third-party memory systems used by them, including raw-text stores, RAG-style retrieval systems, vector or graph memory, profile stores, latent or parametric memory, multimodal memory, and hybrid architectures. It is meant to be read and filled out by the people who build, integrate, evaluate, deploy, govern, or are affected by a memory system.

We are sharing this repository publicly to get feedback on the format, scope, terminology, and coverage of the proposal before wider adoption.

## What this repository contains

| File | Description |
| --- | --- |
| [`templates/memory-card-template.md`](templates/memory-card-template.md) | The blank AMS Card template in GitHub Markdown. Copy this to document your own system. |
| [`templates/memory-card-template.pdf`](templates/memory-card-template.pdf) | Typeset PDF of the same template. |
| [`examples/milamem/memory-card.md`](examples/milamem/memory-card.md) | A fully populated example AMS Card for *MilaMem*, a **fictional** memory system. |
| [`examples/milamem/memory-card.pdf`](examples/milamem/memory-card.pdf) | Typeset PDF of the MilaMem example. |
| [`feedback-questionnaire.md`](feedback-questionnaire.md) | Text version of the public feedback questionnaire. |

The Markdown and PDF versions of each artifact carry the same content and section structure; use whichever format suits your workflow.

## Feedback requested

We are proposing the AMS Card as a standard documentation artifact for AI systems with memory and for third-party memory systems used by them. Feedback is especially useful on missing sections, unclear terminology, adoption barriers, privacy and governance coverage, and examples of real systems this template should handle better.

You can provide feedback by opening an issue on this GitHub repository, commenting on the repository, or filling out this [feedback form](https://forms.gle/TC8JLYi8YTZrmiDF9). The questions are also listed in [`feedback-questionnaire.md`](feedback-questionnaire.md).

## When to use an AMS Card

Fill out an AMS Card whenever you build, ship, or evaluate a component that preserves and reuses information over time — for example a raw-text store, a RAG-style retrieval system, a vector or graph memory, a profile store, a latent or parametric memory, a multimodal memory, or a hybrid architecture. The template is deliberately broad so it can describe any of these without forcing a system into a category it does not implement.

## How to fill out the template

1. Copy [`templates/memory-card-template.md`](templates/memory-card-template.md) into your own project.
2. Work top to bottom. Start with the sections that describe the system as implemented (metadata, interfaces, memory capabilities, architecture, lifecycle, dependencies), then document the evidence around performance, limitations, maintenance, governance, and privacy.
3. Replace every `[bracketed italic]` placeholder with your own content.
4. Use `[More Information Needed]` when a field is unknown or not yet evaluated, and `Not Applicable` when a field genuinely does not apply to your design. Prefer stating why a section does not apply over deleting it.

The template's own **Directory** section is a reader's guide: it points end users, auditors, and developers to the sections most relevant to each of them.

## How to read the MilaMem example

[`examples/milamem/`](examples/milamem/) shows what a completed card looks like. Every field is filled in, so you can see the expected level of detail and the tone of a good answer for each section.

> **MilaMem is fictional.** It is not a real product, service, or research system. Every value in the example — including the benchmark numbers, URLs, and citation — is invented purely to illustrate how the template is used. Do not cite any of it as a real measurement.

## License

Released under the [MIT License](LICENSE).
