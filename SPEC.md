# The Untraceable Protocol

**An open specification for auditable AI use on confidential data.**
Version 1.0 · Published 2026-07-13 · Canonical: https://theuntraceable.ai/protocol

---

The Untraceable Protocol is an open specification for auditable AI use on confidential data. It
defines the record an organization should be able to produce for any AI-assisted deliverable: what
was cloaked, what was submitted to which model, what returned, and who reviewed it — with
confidential values never appearing in the record. It is a conformance target, not only a product
feature.

The key words **MUST**, **MUST NOT**, and **SHOULD** are used in the sense of a normative
specification.

## 1. Scope and motivation

Regulated and confidential work increasingly involves AI, and the field bodies that govern it — in
HEOR, for instance — consistently name the same requirement: **traceability and defensibility**. A
deliverable produced with AI must be explainable after the fact, to a sponsor, an HTA reviewer, or a
compliance officer. This specification defines the minimum evidence that makes that possible, in a
form that itself discloses nothing confidential.

## 2. Definitions

- **Confidential value** — any datum protected by law, contract, or professional or ethical
  obligation.
- **Cloak label** — the meaning-preserving marker that replaces a confidential value before
  transmission.
- **Run** — a single submission of cloaked text to a model and the response it returns, identified
  by a stable run identifier.
- **Record** — the retained evidence for a deliverable, composed of run entries and review entries.

## 3. Requirements

A conforming implementation **MUST**:

| #  | Requirement |
|----|-------------|
| **R1** | Remove all personal data — PII and PHI — via name replacement, so the output can conform to HIPAA, PIPEDA, GDPR and similar privacy law. (This is the privacy obligation.) |
| **R2** | Separately, cloak all secret, NDA-bound, sensitive and unpublished values before any text is transmitted — the model receives cloaked text only. (This is the confidentiality obligation, distinct from R1.) |
| **R3** | Record, per run: the run identifier, timestamp, the specific model used, the residency of that model, whether an external API was used, the system prompt, the user prompts (excluding confidential values), the cloak labels present, and a reference to the returned content — never the real confidential values. |
| **R4** | Restore real values only on the operator's device, for the human viewer, never in the record or any AI-bound payload. |
| **R5** | Record human review: who accepted or modified AI-produced content before it entered a deliverable. |
| **R6** | Make the record reconstructable and exportable for a given deliverable, so it can be produced on request, and retain it for at least 7 years per regulated-industry standards. |
| **R7** | Certify a run with (1) an opening screening that cloaks all values, (2) a closing sentinel that catches any values the user may have missed, (3) a cloak-coverage test ensuring the AI receives exactly what the user reviewed, and (4) a breach test ensuring the AI cannot reconstruct any value. This produces the certification we call the Untraceable Protocol, whose report is added to the audit trail. |

A conforming implementation **MUST NOT** write real confidential values into logs, audit records,
error messages, or any AI-bound payload. R1–R4 are absolute — a single violation is a breach of the
specification, not a degradation of it. It is not only the AI model that must never receive the
secret data: the vendor's processing pipeline must never see it either.

### 3.1 The confidentiality invariant

Across the whole lifecycle: **the human operator sees real values; the AI sees only cloak labels;
the record holds labels and run identifiers, never real values.** Every requirement above is a
consequence of this single invariant.

## 4. Conformance

A tool, workflow, or organization conforms to the Untraceable Protocol v1.0 if it satisfies R1–R7
for every AI-assisted deliverable within its stated scope, and can demonstrate R6 on request.
Conformance is per-scope: a team may conform for one class of work and not another, and should say
which. All audit records should be maintained for at least 7 years to follow strict
regulated-industry rules.

## 5. Relationship to Untraceable

Untraceable implements this specification: name replacement and cloaking (R1, R2, R4), the per-run
audit trail (R3, R6), review capture (R5), and VaultAudit's multi-step Certification (R7). The
specification is published openly so that the requirement it encodes — defensible,
confidential-safe AI use — can be adopted, cited, and conformed to independently.

> **Note:** the cloaking technology itself is patent-pending. Cloaking must not be performed
> without proper licensing from Untraceable. Conformance to this specification does not grant any
> licence to the cloaking methods.

## 6. Versioning

This is version 1.0, published 2026-07-13. Changes will be versioned; the canonical URL
(https://theuntraceable.ai/protocol) always resolves to the current version, and prior versions
remain linkable.

Feedback: **info@theuntraceable.ai**
