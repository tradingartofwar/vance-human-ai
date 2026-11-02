# Local-first intake: choosing a boundary before more capability

**Claim IDs:** P-039  
**Evidence type:** Private design handoff and owner-reported implementation in progress; no inspected running system or measured extraction performance  
**Source and date:** October 29, 2026 intake handoff and its bounded K-Grow status account; read for the November 2 public representation review  
**Publication scope:** Architectural choices and evidence limits only. No intake messages, client details, correspondence, local paths, credentials, or runtime artifacts are published.  
**Human–AI contributions:** Vance selected the practical problem and privacy boundary, chose a small local model after research, and handed implementation to Codex. The AI-assisted handoff specified a bounded architecture and tests. A working system is not yet independently verified.

## The real problem

A clinical-services organization receives prospective-client inquiries by forms, email, and fax. Each contact can contain more than a name and a request. A conversation might involve a guardian, one or more children, earlier correspondence, insurance details, service preferences, and corrections to information already recorded.

Simply forwarding all that material to a powerful general-purpose cloud model would solve one problem while creating another: a sensitive-data boundary the operator did not intend to cross.

The working question became:

> **Can a local language model help interpret intake correspondence while the source evidence and consequential decisions remain in a protected local system?**

That question concerns data handling, source provenance, uncertainty, and human review as much as model performance.

## The design being built

The October 29 handoff selected **Qwen3.5-9B through a local Ollama runtime**, while retaining **Codex in VS Code** as the development assistant. These are different roles: Codex develops and tests the software using fictional fixtures; the intended local Qwen worker interprets content within the protected runtime.

The proposed first slice is deliberately small:

1. Ingest a **fictional** email or fax document.
2. Retain the original and its source identity.
3. Parse known structured fields with ordinary code; ask Qwen to propose interpretations of less structured text, with supporting evidence and explicit unknowns.
4. Validate proposals deterministically. Keep guardians, children, and cases distinct rather than merging them on a name or email address alone.
5. Save a **local** record, send uncertain identity or information changes to human review, and produce a restricted local status notice.

Source collectors, database and file access, validation, and side effects belong to controlled application code. The language model does not receive arbitrary tools to browse other records, modify mailboxes, or run commands. The first implementation uses synthetic examples; connection to real clinical correspondence is a separate acceptance step.

The wider Human–AI collaboration project is **not** the patient-data store. Future cross-system information sharing would require a separately approved schema and audience. A content-free operational status or carefully authorized aggregate may be suitable; raw messages and patient-linked records are not assumed to be.

## What is known, and what is not

**Documented:** A detailed handoff selected Qwen3.5-9B and described a local Python processing architecture, a fictional-data demonstration, specific record/review distinctions, and tests for duplicates, interrupted work, and later corrections. Vance reported that Codex had begun downloading the model and implementing the evaluation in WSL/VS Code.

**Not established by the reviewed sources:** Completed model download; working end-to-end runtime; extraction quality on real data; authorized mailbox/fax integrations; reliable unattended service; deployment to clinical operations; successful de-identification or export to shared agents.

The design is intended to protect protected health information (PHI), but **local inference alone does not establish HIPAA compliance**. Applicable safeguards, access controls, documentation, vendors, risk analysis, and actual runtime behavior still require review and validation. See [HHS Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html), [HHS risk-analysis guidance](https://www.hhs.gov/hipaa/for-professionals/security/guidance/guidance-risk-analysis/index.html), and [HHS de-identification guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html).

## What this episode adds to the wider work

This is not a story about replacing an expert with a smaller model. It is an example of **matching a technical capability to the consequences and permissions of the work**.

The largest model is not automatically the best placement for every piece of information. The useful solution may divide interpretation, evidence, action, and access among different components. It can preserve the uncertainty that needs human judgment instead of producing a fluent but ungrounded intake record.

And it points toward another form of human–AI collaboration: multiple systems can contribute to the same larger project **without all systems receiving the same private information**.

That is a design claim to be tested, not an assertion that this integration already works.

## What evidence should change this account?

A local implementation report with the exact model digest/runtime, fictional end-to-end commands, failure and duplicate/recovery tests, extraction/evidence checks, and explicit source/export boundaries could establish a stronger implementation claim. A live pilot would require a separate authorized security and operational review.

The underlying source work remains private. This public page records the **question, design choice, contribution, and evidence limit**, not a sanitized copy of the clinical system.

**Related:** [Synergistic Intelligence](SYNERGISTIC_INTELLIGENCE.md) · [From an introduction to shared work](FROM_INTRODUCTION_TO_COLLABORATION.md) · [Evidence standards](../evidence/STANDARDS.md)
