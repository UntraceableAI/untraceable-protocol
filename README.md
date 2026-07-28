# The Untraceable Protocol

**An open specification for auditable AI use on confidential data. Version 1.0.**

The Untraceable Protocol defines the evidence an organization should be able to produce for any
AI-assisted deliverable — what confidential values were cloaked, what cloaked text was submitted
to which model and when, what returned, and who reviewed it — **with real confidential values
never appearing in the record.**

It is written as a conformance target any serious AI-compliance team should meet, not only as a
product feature. Regulated fields — HEOR, HTA, pharma, biostatistics and beyond — increasingly
require AI-assisted work to be **traceable and defensible** after the fact, to a sponsor, an HTA
reviewer, or a compliance officer. This specification defines the minimum evidence that makes
that possible, in a form that itself discloses nothing confidential.

📄 **Read the full specification: [SPEC.md](./SPEC.md)**
🌐 **Canonical version (always current): https://theuntraceable.ai/protocol**

## The confidentiality invariant

Across the whole lifecycle:

> The human operator sees real values; the AI sees only cloak labels; the record holds labels and
> run identifiers, never real values.

Every requirement in the specification is a consequence of this single invariant.

## Conformance in one line

A tool, workflow, or organization conforms to the Untraceable Protocol v1.0 if it satisfies
requirements **R1–R7** ([see SPEC.md](./SPEC.md#3-requirements)) for every AI-assisted deliverable
within its stated scope, and can reconstruct the record on request. Conformance is per-scope.

## Who maintains this

The Protocol is published by **[Untraceable AI](https://theuntraceable.ai)** — the confidential
AI workspace for consultants and regulated experts. Untraceable implements this specification, but
the specification is published openly so the requirement it encodes — defensible, confidential-safe
AI use — can be adopted, cited, and conformed to independently.

> **Note:** the cloaking technology itself is patent-pending. Conforming to the Protocol does not
> grant a licence to the cloaking methods; cloaking must not be performed without proper licensing
> from Untraceable.

## Cite this

> The Untraceable Protocol, Version 1.0 (2026). Untraceable AI. https://theuntraceable.ai/protocol

Feedback and conformance questions: **info@theuntraceable.ai**
