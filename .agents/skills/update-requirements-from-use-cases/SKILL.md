---
name: update-requirements-from-use-cases
description: Incrementally detects changes, conducts gap analysis, and systematically derives or updates normative specifications in docs/REQUIREMENTS.md from scenarios in docs/USE_CASES.md using git diffs and semantic traceability.
---

# Update Requirements from Use Cases Skill (`update-requirements-from-use-cases`)

Use this skill whenever:
- New use cases, estate configurations, or testator personas are added to [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md).
- Existing use cases are modified, refined, or removed.
- Synchronizing [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) to ensure 100% specification coverage and bidirectional traceability against [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md).

---

## 1. Change Detection & Audit Strategies

To know what has changed between [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) and [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md), apply a 3-layer detection protocol:

### Layer 1: Git-Based Delta Detection (Fastest for Incremental Edits)
When iterating on the repository, use Git to isolate exact modifications:
1. **Uncommitted/Working Tree Changes:**
   ```bash
   git diff HEAD -- docs/USE_CASES.md
   ```
2. **Changes Between Commits/Branches:**
   ```bash
   git diff main...HEAD -- docs/USE_CASES.md
   # or inspect recent log changes:
   git log -p -n 1 -- docs/USE_CASES.md
   ```
3. If new lines or modified scenarios appear in the Git diff, focus immediately on translating those delta scenarios into requirements.

### Layer 2: Status & Traceability Metadata (In-Document State)
Every use case in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) carries structured metadata tags:
* `**Status:** [ Draft | Pending Processing | Processed | Deprecated ]`
* `**Mapped Requirements:** [ §4.1, §4.4.3, REQ-... ]` (empty if unmapped)
* `**Last Reviewed:** [YYYY-MM-DD]`

**Audit Action:** Search [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) for any use case where `Status` is `Draft` or `Pending Processing`, or where `Mapped Requirements` is empty or stale. These are immediately flagged for processing.

### Layer 3: Semantic Gap Analysis (Full Reconciliation)
Because natural language specifications can drift without Git conflict, periodically run a full semantic cross-check:
1. Read each scenario in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md).
2. Inspect the corresponding section in [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md).
3. Check for:
   * **Unspecified Edge Cases:** Does the requirement handle all boundary conditions stated in the use case (e.g., survivorship periods, minor executors, bankrupt/incapacitated appointees, fractional shares, *Saunders v. Vautier* trust rules)?
   * **Inconsistencies:** Does a general rule in REQUIREMENTS unintentionally preclude or conflict with a legitimate scenario in USE_CASES?

---

## 2. Requirement Derivation Protocol

When translating a use case into formal requirements, do **not** simply copy informal text. Formulate normative specifications adhering to the following structure:

### Step 1: Analyze Testamentary & Jurisdictional Invariants
Evaluate the scenario against the **7 Pillars of Challenge-Resistant Testamentary Design** (see [`review-requirements`](file:///.agents/skills/review-requirements/SKILL.md)):
- Does it preserve probate certainty across Common Law provinces and Quebec Civil Law?
- Does it require operative legal English prose rather than code or shorthand notation?
- Does it protect testamentary capacity and intention (e.g., explicitly stating that minor executor designations anticipate future majority)?
- Does it address tax exposure (e.g., s. 70(6) *Income Tax Act* spousal rollovers, CCPC secondary wills)?

### Step 2: Formulate Normative Requirement Clauses
Write or update the corresponding section in [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) with:
1. **Normative Rule Statement:** Clear, imperative language ("The system MUST...", "The template MUST NOT...").
2. **Data Model & Schema Parameters:** Define how the concept is expressed in JSON/YAML schema (e.g., `shares`, `beneficiary_set`, `contingent_condition`).
3. **Provincial Statutory Nuances:** Detail differences between provinces (e.g., age of majority 18 vs. 19; Ontario *Granovsky* multiple wills vs. BC *Berkner* regime; Quebec CCQ authentic acts).
4. **Operative Legal Language Pattern:** Specify the exact style of traditional legal phrasing to be used in the generated will.

### Step 3: Backlink and Update Metadata
Once [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) has been updated:
1. Update [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) to set:
   * `**Status:** Processed`
   * `**Mapped Requirements:** §X.Y (Line Range / Anchor)`
2. Ensure bidirectional traceability so readers of either document can jump to the other.

---

## 3. Standard Verification Checklist

Before finalizing changes to [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md):
- [ ] Every active use case in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) maps to at least one normative section in [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md).
- [ ] Operative will text requirements mandate traditional legal prose and prohibit raw code/algebraic shorthand in the executed instrument.
- [ ] Any dynamic expressions (e.g., "descendants in order of birth", "children with X") have deterministic evaluation rules and fallback closures.
- [ ] Dedicated file-writing tools (`write_to_file`, `replace_file_content`, `multi_replace_file_content`) are used; never bash heredocs.
