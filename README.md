# ai-assisted-sdlc

# AI-Assisted SDLC: Guardrails Before Coding Agents

This repository contains a **practical prompt sequence** for using AI coding agents responsibly in real software projects.

The goal is simple:

> **Prevent unmaintainable, unpredictable code by forcing clarity _before_ code generation begins.**

This is not about writing better prompts for code.  
It’s about fixing what usually goes wrong *before* code exists.

> ⚠️ **Work in Progress**
>
> This repository is an evolving exploration of how to use AI coding agents safely within the SDLC.
> The prompt sequence, structure, and guidance are actively being refined based on real-world usage.
>
> Feedback, corrections, and alternative approaches are welcome.

---

## Why This Exists

AI coding agents are extremely good at generating code from incomplete information.

That’s also the problem.

When domain rules, product decisions, or system boundaries are unclear:
- Humans fill gaps intuitively
- AI fills gaps deterministically
- Those assumptions get locked into code

This repository introduces a **lightweight but disciplined SDLC layer** that sits *before* architecture and coding.

---

## What This Is (and Is Not)

### ✅ This **is**
- A structured way to use AI in early SDLC phases
- A method to separate **domain truth**, **product decisions**, and **implementation**
- Tool-agnostic (Copilot, Cursor, Claude, etc.)

### ❌ This is **not**
- A code generation framework
- A replacement for engineers or product thinking
- A vendor-specific prompt collection

---

## Repository Structure

---

## The Prompt Flow (High Level)

### Phase 0 — Domain Context
**Goal:** Define domain truth and explicitly list unknowns.

- Shared vocabulary
- Business invariants
- System boundaries
- What is *not* defined

📄 Output: `DOMAIN_CONTEXT.md`

---

### Phase 1 — Domain Review
**Goal:** Surface ambiguity and misinterpretation risk.

- Identify blocking vs non-blocking gaps
- Ask clarifying questions
- Do **not** resolve decisions yet

📄 Output: Review findings (no new artifacts)

---

### Phase 2A — Decision Proposals
**Goal:** Propose options for unresolved ambiguities.

- Multiple viable choices
- Trade-offs explained
- Recommendations clearly labeled

📄 Output: Decision proposals (not PRD)

---

### Phase 2B — Product Requirements (PRD)
**Goal:** Record *approved* decisions clearly and explicitly.

- Decisions, not assumptions
- No architecture or implementation
- Deferred items clearly marked

📄 Output: `PRD.md`

---

### 🚫 What Comes After (Out of Scope Here)

Only after Phase 2B should you move to:
- Architecture
- API design
- Coding agent execution

This repository intentionally stops before that.

---

## Who This Is For

- Backend engineers
- Architects
- Staff / Principal engineers
- Teams experimenting with AI coding agents
- Anyone struggling with “AI-generated code we don’t fully understand”

---

## How to Use This Repo

1. Copy the prompts into your AI tool of choice
2. Run them **in order**
3. Do not skip review or decision phases
4. Treat generated artifacts as first-class documents
5. Only allow code generation after PRD approval

---

## Key Principle

> **AI coding agents don’t remove the need for discipline.  
> They punish you for skipping it.**

If this process feels slower at first, that’s expected.  
It’s still faster than rewriting systems you don’t trust.

---

## Feedback & Contributions

This is a learning-driven framework.

- Issues for discussion are welcome
- PRs that improve clarity are welcome
- Tool-specific forks are encouraged

---

## Contributing

This repository is intentionally small and opinionated.
Contributions are welcome — especially if they improve clarity, rigor, or real-world usability.

### Good Contributions
- Refining prompt wording to reduce ambiguity
- Adding examples from real projects (anonymized)
- Improving the SDLC flow or decision gates
- Clarifying where teams commonly misuse AI coding agents
- Identifying edge cases or failure modes this process misses

### What This Repo Is Not Looking For
- Tool-specific prompts (Copilot, Cursor, etc.)
- Code generation recipes
- Frameworks, templates, or abstractions
- “One-shot” prompts that skip decision phases

### How to Contribute
1. Open an issue to discuss the change or idea
2. Keep proposals focused and scoped
3. Submit a PR with clear intent and reasoning

### Contribution Philosophy
This project values **explicit thinking over speed**.
If a change reduces ambiguity or prevents silent assumptions, it’s likely welcome.


## License

MIT — use freely, adapt responsibly.
