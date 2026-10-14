---
name: will-preparation
description: Interactive testamentary elicitation, validation, and document generation skill for Canadian wills across all provinces and territories, ensuring compliance with Free-Willy legal invariants and modular clause assembly.
---

# Free-Willy Will Preparation & Drafting Skill

Use this skill when a user asks an AI assistant to prepare, draft, review, or generate a Last Will and Testament and associated testamentary instruments across any Canadian jurisdiction.

---

## 1. Core Operating Principles & Invariants

When acting as an estate preparation assistant, you must adhere strictly to these non-negotiable principles:

1. **Strict Preamble Separation Principle:**
   - Any software disclaimer, AI metadata, validation warning, or statutory notice **MUST NEVER appear on the body of the Last Will and Testament**.
   - The executed legal will must remain pristine for court and probate acceptance.
   - All advisory notices, educational share mathematics, and warnings belong strictly in the separate companion document: **Advisory Preamble & Safeguard Summary**.

2. **Mandatory Defaults:**
   - **Distribution Default:** All residuary bequests operate under **per stirpes** (lineal representation) unless explicitly overridden by the testator to **per capita**.
   - **Survivorship Default:** Every beneficiary must survive the testator by at least **90 days** to inherit.
   - **No Fixed Share Total:** Share pools are calculated dynamically by summing allocated shares. Shares that cannot be legally distributed cease to exist, automatically contracting the denominator and eliminating partial intestacy.

3. **Multi-Level Conditional Beneficiaries & Per Stirpes Precedence:**
   - Testators may specify conditional alternates to any depth (`Primary -> Alternate 1 -> Alternate 2 -> ...`).
   - If a gift is *per stirpes*, conditional beneficiaries **only take if the primary beneficiary leaves NO surviving descendants (issue)**. If surviving descendants exist, they take by representation before any conditional alternate is reached.

4. **Default Catastrophic / Family Wipeout Fallback:**
   - If all designated beneficiaries and issue predecease the testator, the will defaults to a **50/50 split between the testator's family and the spouse's family**.
   - Each half is distributed via **parentelic representation**: tracing up to the nearest common ancestor with surviving issue, distributed *per stirpes*.

5. **Same-Name Disambiguation:**
   - If any parties share identical or similar legal names, you must explicitly elicit and record distinguishing attributes (relationship to testator, city of residence, seniority qualifiers like Sr./Jr., parentage, or birth year) and include them in every clause.

6. **Inherited Property & Tax Allocation:**
   - Property inherited by the testator must be identified as such with source/donor attribution.
   - For specific gifts of financial value, taxes must be paid by the recipient beneficiary via (a) deduction from their residuary share, (b) partial sale of the gifted property, or (c) direct cash reimbursement to the estate.

---

## 2. Interactive Interview Workflow (Step-by-Step)

Guide the testator through a calm, systematic intake process:

### Step 1: Testator Profile & Jurisdiction
- Full legal name, preferred names/aliases.
- Residential address, city, province/territory of domicile.
- Citizenship.
- **Jurisdiction check:**
  - Common law provinces/territories vs. Quebec (*Civil Code of Québec*).
  - For Quebec, clarify whether preparing an English-language Will Made in the Presence of Witnesses (Arts. 712–715 CCQ) or provisions for formalization before a notary.

### Step 2: Will Scoping & Multiple Wills
- Ask if the testator owns shares in private Canadian corporations (CCPCs), shareholder loans, or private assets suitable for a **Secondary / Non-Probate Will** to minimize provincial probate fees (e.g., Ontario Estate Administration Tax).
- Ask if the testator has executed wills in foreign jurisdictions (e.g., UK, US) that must be preserved via a **Selective Revocation Clause**.

### Step 3: Fiduciary Appointments (Executors & Guardians)
- Priority list for Executors / Liquidators: "First person willing and legally able to act."
- Support dynamic classes (e.g., "my surviving children in order of decreasing age").
- Alternate executors.
- Testamentary Guardians / Tutors for minor children.

### Step 4: Specific Gifts, Inherited Property & Tax Payment
- For each specific bequest (money, jewelry, family heirlooms, real estate):
  - Is this property inherited? If so, record from whom/which estate it was inherited.
  - If it has financial value (or triggers capital gains upon death), confirm the beneficiary's method for paying taxes:
    1. Deducted from their residuary estate share.
    2. Partial liquidation/sale of the property.
    3. Direct payment of funds to the estate executors.
  - Does the gift have backup/conditional beneficiaries?

### Step 5: Residuary Estate & Share Allocation
- Designate residuary beneficiaries and relative share units (e.g., 3 shares to child A, 2 shares to child B).
- Confirm default *per stirpes* (children inherit if parent predeceases) or note any explicit *per capita* exceptions.
- Establish multi-level conditional alternates (gift-overs).
- Confirm adoption of the default 50/50 parentelic catastrophic wipeout clause.

### Step 6: Minor Trusts & Digital Assets
- Milestone age for distribution (e.g., 18, 21, 25) and staged payouts (e.g., 50% at 21, 100% at 25).
- Executor powers over digital accounts, email, cryptocurrencies, and cloud storage.
- Pet care provisions (designated caregiver + maintenance fund).

---

## 3. Statutory Validation Engine (Pre-Generation Audit)

Before assembling the output, audit the gathered profile against provincial requirements:

| Validation Rule | Verification Criteria |
| :--- | :--- |
| **Witness Disqualification** | Ensure no designated executor, beneficiary, or spouse of a beneficiary acts as an attesting witness. |
| **Age of Majority** | Verify testator meets provincial minimum age (18 in AB, SK, MB, ON, PEI, QC; 19 in BC, NB, NL, NS, Territories), flagging statutory exceptions. |
| **Dependant Support / Family Relief** | Flag omissions of spouses or dependent children under provincial family relief acts (e.g., Ontario SLRA Part V, BC WESA Part 4). |
| **Name Disambiguation** | Verify all parties with identical names have relationship, locality, or parentage specified. |
| **Quebec Notarial Formalities** | Remind Quebec testators that a will before witnesses requires probate upon death, whereas a notarial will does not. |

---

## 4. Document Generation Suite

Produce the complete four-part deliverable package:

1. **Last Will and Testament (`.md` / `.txt`):**
   - Clean, formal legal instrument.
   - Revocation, appointment, specific bequests, residue distribution, administrative powers, attestation clause.
   - **Zero software disclaimers or metadata on this document.**

2. **Provincial Affidavit of Execution / Attestation:**
   - Statutory court form for the specific province (e.g., Ontario Form 74D, BC WESA Supreme Court affidavit, Alberta Form NC 8).

3. **Provincial Signing and Witnessing Guide:**
   - Physical presence rules (two adult witnesses present at the same time).
   - Invalidation risks if beneficiaries sign as witnesses.
   - Initialing all pages in blue ink, date, and signature block.

4. **Advisory Preamble & Safeguards Summary:**
   - Software and informational disclaimers (recommending review by qualified legal counsel).
   - Detailed plain-language mathematical walkthrough of share calculations and non-existent shares.
   - Plain-language explanation of 90-day survivorship, *per stirpes* vs. *per capita*, conditional alternates, and family wipeout distribution.
   - Summary of validation checks and provincial statutory considerations.
