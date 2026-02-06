# Phase 0: Strategic Domain Framing & Development Governance

## Role
Principal Architect responsible for domain correctness and long-term maintainability.

---

## Objective

Create the **authoritative domain definition** for the system described in the provided Problem Statement.

The output, `docs/DOMAIN_CONTEXT.md`, will serve as the **single source of truth** for:
- Domain language
- Business invariants
- System boundaries
- AI development constraints

This step exists to ensure future PRDs, designs, and code are:
- Correct by construction
- Understandable by human engineers
- Resistant to AI hallucination or logic drift

---

## Instructions for AI Architect

Analyze the provided Problem Statement and produce `docs/DOMAIN_CONTEXT.md` using the following standards.

---

### 1. Ubiquitous Language (Glossary)
**Requirement:** Establish a shared, precise domain language.

**Task:**  
Identify and define the **core domain concepts** used in the problem statement using:
- Clear, unambiguous
- Implementation-neutral
- Business-meaningful language

Do not invent concepts not present in the problem statement.

---

### 2. Business Invariants (Non-Negotiable Rules)
**Requirement:** Identify rules that must **always** hold true.

**Task:**  
Extract domain rules that:
- Are explicitly stated, or
- Are logically unavoidable for correctness

If a rule is implied but not explicit, list it as an **ambiguity**, not an invariant.

---

### 3. Domain State & Time Semantics (If Applicable)
**Requirement:** Capture lifecycle or temporal behavior where it exists.

**Task:**  
If the problem statement defines:
- States
- Lifecycles
- Expiry rules
- Time-based constraints

Document them **exactly as specified**.

If no lifecycle is defined, explicitly state that.

---

### 4. Domain Boundaries & External Dependencies
**Requirement:** Define responsibility boundaries.

**Task:**  
Clearly state:
- What this system owns and guarantees
- What is delegated to or signaled by external systems
- What this system must never decide

Focus on **business ownership**, not technical integration.

---

### 5. Failure Semantics (Domain-Level)
**Requirement:** Define the business meaning of failures.

**Task:**  
Describe how the domain interprets:
- External dependency failures
- Interrupted operations
- Partial or incomplete actions

Avoid technical recovery mechanisms.

---

### 6. Non-Goals
**Requirement:** Prevent scope creep.

**Task:**  
Explicitly list problems or responsibilities that this system does **not** attempt to solve.

---

### 7. Ambiguities & Open Questions
**Requirement:** Surface uncertainty early.

**Task:**  
List:
- Underspecified behaviors
- Conflicting requirements
- Missing rules

Do not resolve them here.

---

### 8. AI Development Governance (Mandatory)
Add a section defining the following rules:

- AI must not invent domain rules
- AI must not bypass DOMAIN_CONTEXT.md
- Conflicts must be surfaced, not silently resolved
- Code generation is forbidden until PRD approval

---

## Constraints (Strict)

- Do NOT design architecture.
- Do NOT propose data models.
- Do NOT reference specific technologies.
- Do NOT write requirements or user stories.
- Do NOT optimize for performance.

This document defines **domain meaning**, not **implementation**.

---

## Output Requirements

- Clear Markdown structure
- Declarative, precise language
- Suitable for long-term human maintenance

---

