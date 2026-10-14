---
name: review-will-skill
description: Audits, refines, and synchronizes the will-preparation skill (will-preparation/SKILL.md) against docs/REQUIREMENTS.md and Free-Willy architectural invariants.
---

# Review Will Skill (`review-will-skill`)

Use this skill whenever:
- `docs/REQUIREMENTS.md` has been modified and `.agents/skills/will-preparation/SKILL.md` needs to be audited or synchronized.
- New legal requirements, provincial statutes, or testamentary patterns are added to the system.
- Refinements to the interactive conversational elicitation, validation checklists, or document assembly procedures in `will-preparation/SKILL.md` are needed.

---

## 1. Audit Checklist & Verification Matrix

When reviewing `.agents/skills/will-preparation/SKILL.md`, verify that each of the following system invariants and requirements from [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) is accurately represented and enforced:

| Invariant / Feature | Section in Requirements | Verification Criteria in `will-preparation/SKILL.md` |
| :--- | :--- | :--- |
| **Strict Preamble Separation** | §3, §11.2 | Preamble/advisory notices, AI metadata, and statutory warnings are kept strictly separate; the Last Will and Testament remains pristine for probate. |
| **Per Stirpes Default** | §4.4.1 | Residuary distribution defaults to *per stirpes* unless explicitly overridden to *per capita*. |
| **Dynamic Share Arithmetic** | §4.4.3 | Total share pool equals sum of granted shares. Unallocatable shares cease to exist, automatically contracting the denominator and preventing partial intestacy. |
| **90-Day Survivorship Rule** | §4.4.5 | Unified 90-day survival rule applies equally to pre- and post-will deaths; non-survival treats beneficiary as having predeceased. |
| **Multi-Level Conditionals** | §4.4.6 | Arbitrary-level conditional alternates supported. Under *per stirpes*, alternates **only take if primary leaves no surviving descendants**. |
| **50/50 Catastrophic Wipeout** | §4.4.7 | Default ultimate fallback divides estate 50/50 between spouse's and testator's families via parentelic representation capped at 5 generations of parental lineage; falls back to governing province's intestacy laws if no beneficiaries exist within 5 generations. |
| **Inherited Property Provenance** | §4.6.2 | Inherited gifts are explicitly identified as such, documenting the source/donor estate. |
| **Tax on Financial Gifts** | §4.6.3 | Beneficiary must pay taxes arising from specific gifts of financial value via residuary offset, partial sale, or direct reimbursement to estate. |
| **Same-Name Disambiguation** | §4.7, §11.1.5 | Distinguishing attributes (relationship, address, seniority qualifier, parentage, birth year) are enforced for identical legal names. |
| **Dual Will Strategy** | §4.2 | Accommodates Secondary / Non-Probate Wills for CCPC shares and private assets to minimize provincial probate fees. |
| **Selective Revocation** | §4.3 | Allows preservation of foreign / extra-provincial wills. |
| **Provincial Validation** | §11.1 | Audits witness disqualification (no beneficiaries/spouses as witnesses), age of majority, and provincial family relief / dependant support duties. |
| **Quebec CCQ Formalities** | §2.2, §11.1.4 | Distinguishes between English-language wills before witnesses (Arts. 712–715 CCQ, requiring probate) and notarial wills (not requiring probate). |

---

## 2. Review & Update Workflow

Follow this step-by-step procedure when executing this skill:

### Step 1: Ingest Active Requirements
1. Read the latest content of [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md).
2. Note any recently added or amended functional requirements, configuration keys, or legal safeguards.

### Step 2: Read Current Skill Definition
1. Read the active [`will-preparation/SKILL.md`](file:///home/doug/code/free-willy/.agents/skills/will-preparation/SKILL.md).
2. Compare the interview steps, operating principles, validation rules, and output instructions against the Verification Matrix.

### Step 3: Identify Gaps & Discrepancies
- Are all newly specified edge cases and interview questions represented in the skill?
- Are the instructions clear, unambiguous, and directly actionable for an AI agent?
- Are the frontmatter metadata fields (`name`, `description`) concise and accurate?

### Step 4: Apply Updates Using Dedicated File Tools
- Update [`.agents/skills/will-preparation/SKILL.md`](file:///home/doug/code/free-willy/.agents/skills/will-preparation/SKILL.md) using `replace_file_content` (or `write_to_file`).
- **Never use `cat << 'EOF'` or bash heredocs.**
- Ensure proper Markdown formatting, clear code/YAML snippets, and structured tables.

### Step 5: Verify & Report
- Review the diff to confirm all intended changes are present and accurately reflect `docs/REQUIREMENTS.md`.
- Provide a concise summary of updates made to `will-preparation/SKILL.md`.
