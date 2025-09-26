
# 📦 Excel Formula Repo Starter Kit (AI-Assisted, Issue-Driven)

This starter kit helps you build **Excel formula** repositories (dynamic arrays, LAMBDAs, LET patterns) using an **issue-driven** workflow with **Microsoft Copilot Chat**.

**Key ideas:**
- **Issues are the source of truth** (requirements, decisions, constraints).
- **COPILOT.md** defines how Copilot should work with your repo.
- **Small, focused PRs** trace back to issues (e.g., `closes #12`).
- **No GitHub Actions** included or required.

---

## 🧭 Repository Structure
```
.
├── COPILOT.md
├── README.md
├── src/                # Your workbook-agnostic formula definitions & snippets (plain text)
├── tests/              # Test notes / manual test sheets, scenarios, edge cases
├── examples/           # Example formulas and usage notes
├── docs/               # Additional documentation
└── .github/
    ├── ISSUE_TEMPLATE.md
    └── PULL_REQUEST_TEMPLATE.md
```

## 🚀 Quick Start
1. **Create an Issue** using the template (problem, acceptance criteria, constraints, examples).
2. In your IDE, ask **Copilot Chat** to: *“Read COPILOT.md and Issue #<id>; summarize goals & AC; propose a plan.”*
3. Implement formulas as **plain text** in `src/` and add example usage in `examples/`.
4. Open a **small PR**, link the issue (`closes #<id>`), and follow the PR template.
5. Record decisions back in the **Issue** (not the PR thread).

## 🔧 Conventions for Excel Formulas
- **Plain text first**: Store formulas in `.txt` or `.md` with clear headers; avoid binary artifacts when possible.
- **Name & purpose**: Each formula snippet starts with a one‑line purpose and inputs description.
- **Compatibility**: Note Excel variants (Desktop/Online) if relevant.
- **No helper columns** unless explicitly justified in the **Issue**.
- **Preserve custom LAMBDAs** when refactoring; do not inline/remove without approval in the Issue.

## 🧪 Testing Guidance (manual or workbook-based)
- Derive tests directly from **Issue acceptance criteria**.
- Include **positive, negative, and edge** cases.
- Capture known limits (e.g., large arrays, volatile functions).

## 💬 Prompts to reuse
- “Copilot, read COPILOT.md and Issue #<id>. Summarize AC/constraints in ≤5 bullets.”
- “Copilot, propose a minimal formula solution with assumptions called out for Issue #<id>.”
- “Copilot, review my formula vs. AC in #<id> and list mismatches or risky assumptions.”

---

### ✔ Example (paste into an Issue)
**Problem:** Return the *n*‑th largest unique value from a range.

**Acceptance Criteria:**
- Works with dynamic arrays (spill behavior)
- Handles duplicates correctly
- Returns `#N/A` if n > unique count
- Compatible with Microsoft 365 Excel

**Candidate Formula (plain text illustration):**
```
=LAMBDA(array,n,
  LET(u,SORT(UNIQUE(array),,-1),IF(n<=ROWS(u),INDEX(u,n),NA()))
)
```
*(Treat this as a starting point; validate against AC in the Issue.)*

---

### 📎 Notes
- This kit intentionally **omits GitHub Actions**.
- Keep large discussions in **Issues** to maintain traceability.
