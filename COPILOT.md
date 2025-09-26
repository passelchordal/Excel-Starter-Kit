
# COPILOT.md — Working Agreement for Excel Formula Repos

> **Purpose:** Provide a lean, reliable guide for using **Microsoft Copilot Chat** in this repository.
> **Rule:** **Issues are the source of truth.** Treat Issues as living design comments for your formulas.

---

## 1) Scope & Principles
- **Primary assistant:** Microsoft Copilot Chat (VS Code / JetBrains).
- **Single source of truth:** **GitHub Issues** (requirements, rationale, acceptance criteria).
- **Human-in-the-loop:** All AI suggestions are reviewed before merge.
- **No GitHub Actions:** Do not add or rely on CI here.

**Copilot behavior:**
1. **Read first**: Always read/refresh the relevant **Issue** before proposing formulas.
2. **Ground responses**: Reference issue IDs (e.g., `#123`) in summaries, commit messages, and comments.
3. **Be concise & accurate**: If info is missing or unverifiable, say so and request specifics.
4. **No guessing**: If an assumption is required, mark it clearly and propose a way to validate it.
5. **Respect repository norms**: Preserve custom **LAMBDAs**, keep formulas in **plain text**.

---

## 2) Context Loading & Refresh
- Start of task: “**Copilot, summarize Issue #<id>: goals, AC, constraints, open questions.**”
- On drift: “**Copilot, re-read COPILOT.md and the linked Issue; provide a refreshed plan in ≤5 bullets.**”
- Large Issues: Ask Copilot to **chunk** and extract AC and **non‑goals**.

---

## 3) Issue-Driven Workflow (Issues = Comments for Code)
**Every Issue must include:**
- **Context**: Problem & motivation
- **Acceptance Criteria**: Testable bullets
- **Constraints**: e.g., no helper columns; performance; compatibility
- **Examples**: Small input/output tables or sample ranges
- **Open Questions**

**Copilot must:**
- **Summarize** the Issue before any formula proposal
- **Propose a plan** in 3–7 bullets tied to AC
- **Traceability**: Use `closes #<id>` in PRs and `#<id>` in commits

> Keep deep reasoning in **Issues**. PRs focus on diffs and final review.

---

## 4) Development & Review
**Branching:** `feature/<issue-123>-short-slug` or `fix/<issue-123>-short-slug`

**Pull Requests (small & focused):**
- Link the Issue (`closes #<id>`)
- Summary: what changed, why, and how AC are met
- Checklist:
  - [ ] All AC satisfied (list explicitly)
  - [ ] Issue updated with decisions
  - [ ] Self-review complete
  - [ ] Examples/tests updated
  - [ ] No secrets or sensitive data

**Copilot Review Prompts:**
- “**Copilot, review this diff vs. Issue #<id> AC; list mismatches.**”
- “**Copilot, generate edge cases from #<id> AC to challenge the formula.**”
- “**Copilot, explain performance and volatility implications in ≤7 bullets.**”

---

## 5) Coding Standards for Excel Formulas
- **Format**: Plain text `.txt`/`.md` with a header: name, purpose, inputs, outputs
- **Functions**: Prefer **LET** for readability; use **LAMBDA** to encapsulate
- **Dynamic Arrays**: Prefer spill-friendly solutions; avoid legacy array-entered formulas
- **Dependencies**: Avoid unless justified in the Issue
- **Performance**: Call out potential hotspots (e.g., iterative MAP/SCAN) in the Issue

---

## 6) Testing & Validation
- Derive tests directly from **AC**
- Include **positive/negative/edge** cases
- Keep a `tests/` note per formula (inputs/expected outputs) and an example worksheet when applicable

**Prompts:**
- “**Copilot, from Issue #<id>, enumerate positive/negative/edge cases.**”
- “**Copilot, propose a minimal test matrix that satisfies AC.**”

---

## 7) Handling Ambiguity
1. State the uncertainty explicitly
2. Propose 1–2 viable interpretations with trade‑offs
3. Ask for a decision in the Issue; **pause** ambiguous parts until clarified

---

## 8) Quick-Start Prompt Pack
- “**Copilot, read COPILOT.md and Issue #<id>. Summarize goals, AC, constraints in ≤8 bullets.**”
- “**Copilot, propose a 5‑step implementation plan and call out assumptions.**”
- “**Copilot, review my formula vs. AC; list gaps and risks.**”
- “**Copilot, generate examples for README from the Issue.**”

---

## 9) Known Limits & Recovery
- **Context window**: Break large Issues into chunks; keep PRs small
- **Drift**: If Copilot disagrees with this file or the Issue, **re‑read and reconcile**
- **Recovery prompt**: “**Copilot, re‑read COPILOT.md and the linked Issue; provide a corrected plan that aligns with both.**”
