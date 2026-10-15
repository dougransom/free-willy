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
| **Probate Certainty & Tripartite Architecture** | §1, §3, §4.4.10, §11.2 | Operative dispositive clauses formulated strictly in unambiguous legal English prose (no experimental symbolic/code notation in operative text); internal legal definitions in preamble; optional illustrative examples in incorporated appendix (Schedule A); software notices/warnings strictly relegated to external Advisory Safeguards Report. |
| **Per Stirpes Default** | §4.4.1 | Residuary distribution defaults to *per stirpes* unless explicitly overridden to *per capita*. |
| **Dynamic Share Arithmetic** | §4.4.3 | Total share pool equals sum of granted shares. Unallocatable shares cease to exist, automatically contracting the denominator and preventing partial intestacy. |
| **30-Day Survivorship Rule** | §4.4.5 | Default 30-day survivorship rule applies to all gifts, protecting ITA s. 70(6) spousal rollover. Non-survival treats beneficiary as predeceased. |
| **Testamentary Capacity Protection** | §4.4.5 | System interview screens for deceased beneficiaries; will never names a person known to be dead as a direct legatee, naming their issue directly instead. |
| **Multi-Level Conditionals** | §4.4.6 | Arbitrary-level conditional alternates supported. Under *per stirpes*, alternates **only take if primary leaves no surviving descendants**. |
| **Catastrophic Wipeout & Charity Default** | §4.4.7 | Default fallback divides estate 50/50 between spouse's and testator's families via parentelic representation capped at descendants of **grandparents**; if none, passes to default registered charity: **Cancer Research Society** (`11915 3229 RR0001`). |
| **Registered Plans & Insurance Confirmation** | §4.6.1 | Confirms prior designations for RRSPs, RRIFs, TFSAs, FHSAs, and life insurance, protecting them from general revocation; specifies terminal income taxes on registered accounts are borne by residue. |
| **Comprehensive Administrative Powers** | §4.5.3 | Conveys broad powers to executors (in specie distribution, ITA s. 164(6) corporate reorganizations, tax elections, borrowing, claim settlement, real estate, investment discretion) avoiding court orders. |
| **Inherited Property Provenance** | §4.6.2 | Inherited gifts are explicitly identified as such, documenting the source/donor estate. |
| **Beneficiary Sets & Class Gifts** | §4.4.8 | Supports gifts to sets (e.g., "my children", "descendants of X") divided equally among 30-day survivors (with per stirpes representation where applicable). |
| **Dual Capacity / Multiple Appearances** | §4.4.9 | Defines rules when an individual can appear twice under per stirpes (cumulative branch representation by default vs. deduplication). |
| **Same-Name Disambiguation** | §4.7.2, §11.1.5 | Distinguishing attributes (relationship, address, seniority qualifier, parentage, birth year) are enforced for identical legal names. |
| **Dual Will Strategy & Ontario Granovsky** | §4.1.4, §4.2, §11.1.6 | Accommodates Secondary / Non-Probate Wills for CCPC shares and private assets to minimize probate fees; allows same executor in Ontario under *Granovsky*; warns Alberta and Quebec users that dual wills are unnecessary. |
| **Matrimonial Property Harmonization** | §4.7.1 | Declares whether gifts to surviving spouse are in addition to statutory equalization claims (e.g., Ontario *FLA* s. 5/6, Alberta *FPA*). |
| **Dependant Relief & Disinheritance Statement** | §11.1.3 | Audits dependant support; alerts BC testators to adult child moral claims (*WESA* s. 60); provides optional *Statement of Reasons for Disinheritance* (admissible under *WESA* s. 62). |
| **Selective Revocation** | §4.3 | Allows preservation of foreign / extra-provincial wills. |
| **Provincial Validation & Age of Majority** | §11.1.1-2 | Audits witness disqualification (no beneficiaries/spouses as witnesses), age of majority (18 vs 19), minor trust milestones (rejecting payouts below majority), and *Saunders v. Vautier* contingent gift-overs. |
| **Digital Asset Privacy & Credential Memo** | §4.6.3, §11.1.7 | Enforces executor legal authority in the will while strictly isolating passwords, seeds, and vault credentials to a private unprobated memorandum. |
| **Inter-Provincial Real Estate & Resealing** | §4.2.3, §11.1.8 | Governs Canadian land via single will with resealing alerts, or separate provincial property wills with mutual carve-outs. |
| **Virtual Witnessing Statutory Compliance** | §3, §11.1.9 | Provides physical in-person execution as default, plus provincial remote witnessing protocols (Ontario LSO lawyer requirement; BC WESA s. 35.2). |
| **Quebec CCQ Formalities** | §2.2, §11.1.4 | Distinguishes between English-language wills before witnesses (Arts. 712–715 CCQ, requiring probate) and notarial wills (not requiring probate); warns Quebec residents against dual wills. |

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
