# Phase 1: Requirements & Domain Alignment Review

## Role
Principal Engineer acting as an independent reviewer.

---

## Objective

Validate that the **Problem Statement** is correctly and completely represented by the existing `docs/DOMAIN_CONTEXT.md`, and identify gaps, ambiguities, and risks **before** PRD creation.

This phase exists to prevent:
- Silent assumptions
- Domain drift
- Requirements leaking into design or code

---

## Inputs (Authoritative)

- `docs/DOMAIN_CONTEXT.md` (authoritative domain definition)
- The original Problem Statement

No other documents should influence this review.

---

## Task

Perform a structured comparison between:
- What the Problem Statement explicitly requires
- What `DOMAIN_CONTEXT.md` currently defines

For each major domain flow implied by the problem statement:
- Identify alignment
- Identify mismatches
- Identify omissions

---

## What to Analyze

Analyze the domain at the level of **business behavior**, including (where applicable):

- Core entity lifecycle(s)
- Time-bound rules and expirations
- Concurrency expectations
- External dependencies and signals
- Abuse or misuse prevention
- Failure and interruption semantics

Do **not** assume all of these exist; analyze only what is relevant to the domain.

---

## What to Produce

### 1. Confirmed Alignments
Areas where the problem statement and `DOMAIN_CONTEXT.md` are consistent and complete.

### 2. Blocking Gaps
Missing or unclear domain rules that must be resolved before PRD creation.

### 3. Non-Blocking Gaps
Gaps that can reasonably be deferred to PRD or later phases.

### 4. Contradictions
Explicit conflicts between the problem statement and `DOMAIN_CONTEXT.md`.

### 5. Risk Areas
Domain areas where misinterpretation would likely cause incorrect behavior.

### 6. Clarifying Questions
Precise, decision-forcing questions that must be answered to proceed.

---

## Classification Rule

Every gap, contradiction, or question must be labeled as:

- **BLOCKING** — must be resolved before PRD
- **NON-BLOCKING** — can be resolved later

---

## Constraints (Strict)

- Do NOT propose solutions.
- Do NOT invent domain rules.
- Do NOT suggest architecture, patterns, or technologies.
- Do NOT modify `DOMAIN_CONTEXT.md` directly.
- Do NOT make product decisions.

This is a **review**, not a design activity.

---

## Output Format

- Clear section headers
- Bullet points only
- Concise, domain-focused language

---

