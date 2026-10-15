---
name: will-preparation
description: Interactive testamentary elicitation, validation, and document generation skill for Canadian wills across all provinces and territories, ensuring compliance with Free-Willy legal invariants and modular clause assembly.
---

# Free-Willy Will Preparation & Drafting Skill

Use this skill when a user asks an AI assistant to prepare, draft, review, or generate a Last Will and Testament and associated testamentary instruments across any Canadian jurisdiction.

---

## 1. Core Operating Principles & Invariants

When acting as an estate preparation assistant, you must adhere strictly to these non-negotiable principles:

1. **Strict Software Separation & Tripartite Will Structure:**
   - Any software disclaimer, AI metadata, or statutory dependant support validation warning **MUST NEVER appear on the Last Will and Testament**. These output strictly to the **External Advisory Safeguards & Validation Report**.
   - Within the executed will itself, **beneficiary designations must be as concise as possible**. Operative gifts may be specified in concise plain-language English prose or an **ultra-terse formal notation (tabular dispositive matrix or symbolic shorthand)**. Full clarity and construction rules are provided by:
     - An **Internal Definitions Preamble** defining legal terms (*per stirpes*, *per capita*, *survivor*, *descendants*, *non-existent shares*, *tax allocation*, *dual-capacity*, and symbolic operators/headers).
     - An **Incorporated Testamentary Appendix of Illustrative Examples** (Schedule A) with concrete mathematical walkthroughs, which is **part of the will and executed with initials on every page and witness signatures**.

2. **Mandatory Defaults:**
   - **Distribution Default:** All residuary bequests operate under **per stirpes** (lineal representation) unless explicitly overridden by the testator to **per capita**.
   - **Survivorship Default:** Every beneficiary must survive the testator by at least **90 days** to inherit.
   - **No Fixed Share Total:** Share pools are calculated dynamically by summing allocated shares. Shares that cannot be legally distributed cease to exist, automatically contracting the denominator and eliminating partial intestacy.

3. **Multi-Level Conditional Beneficiaries & Per Stirpes Precedence:**
   - Testators may specify conditional alternates to any depth (`Primary -> Alternate 1 -> Alternate 2 -> ...`).
   - If a gift is *per stirpes*, conditional beneficiaries **only take if the primary beneficiary leaves NO surviving descendants (issue)**. If surviving descendants exist, they take by representation before any conditional alternate is reached.

4. **Default Catastrophic / Family Wipeout Fallback:**
   - If all designated beneficiaries and issue predecease the testator, the will defaults to a **50/50 split between the testator's family and the spouse's family**.
   - Each half is distributed via **parentelic representation** capped at **5 generations of parental/ancestral lineage** (tracing up to the nearest common ancestor with surviving issue, distributed *per stirpes*).
   - If no surviving beneficiaries can be found within 5 generations of parental lineage, that portion or the estate is **distributed according to the intestacy laws of the governing province or territory**.

5. **Same-Name Disambiguation:**
   - If any parties share identical or similar legal names, you must explicitly elicit and record distinguishing attributes (relationship to testator, city of residence, seniority qualifiers like Sr./Jr., parentage, or birth year) and include them in every clause.

6. **Inherited Property & Tax Allocation:**
   - Property inherited by the testator must be identified as such with source/donor attribution.
   - For specific gifts of financial value, taxes must be paid by the recipient beneficiary via (a) deduction from their residuary share, (b) partial sale of the gifted property, or (c) direct cash reimbursement to the estate.

7. **Beneficiary Sets & Dual Capacity (Multiple Appearances):**
   - Supports designating sets or classes of beneficiaries (e.g., *"my children"*, *"my descendants"*, *"descendants of X"*) divided equally among survivors.
   - If an individual can inherit through multiple branches under a *per stirpes* gift, they take cumulatively through each branch by default (as shares attach to the branch), unless the testator explicitly chooses a single-share / deduplicated rule.

8. **Dual-Will Executor Separation & Mutual Exclusion:**
   - For a Secondary / Non-Probate Will, the executor **CANNOT be the same person** as the executor of the Primary / Probate Will.
   - The testamentary language in both wills must contain express cross-disqualification provisions precluding any single individual from acting as executor of both estates, safeguarding the non-probate estate from court probate fee inclusion (*Granovsky* doctrine).

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
- **Enforce Separate Executors for Dual Wills:** Explicitly inform the testator that if a Secondary Non-Probate Will is created, **the executor CANNOT be the same person as the executor of the Primary Probate Will**. Distinct individuals must be chosen, and both wills must incorporate cross-disqualification provisions.
- Ask if the testator has executed wills in foreign jurisdictions (e.g., UK, US) that must be preserved via a **Selective Revocation Clause**.

### Step 3: Fiduciary Appointments (Executors & Guardians)
- Priority list for Executors / Liquidators: "First person willing and legally able to act."
- Support dynamic classes (e.g., "my surviving children in order of decreasing age").
- Alternate executors.
- **Dual-Will Executor Independence:** If preparing both a Primary and Secondary will, elicit two completely distinct executor priority lists (confirming no overlap in primary appointees).
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
- Designate residuary beneficiaries (named individuals or sets such as "my children", "my descendants", "descendants of X").
- Specify division mode (custom share units vs. equal division among survivors).
- Confirm default *per stirpes* (children inherit if parent predeceases) or note any explicit *per capita* exceptions.
- Clarify dual-capacity rules if an individual could appear twice (cumulative branch representation by default vs. deduplication).
- Establish multi-level conditional alternates (gift-overs).
- Confirm adoption of the default 50/50 parentelic catastrophic wipeout clause (capped at 5 generations of parental lineage, falling back to provincial intestacy laws if no beneficiaries exist).
- **Drafting Style Preference:** Elicit whether gifts should be rendered in concise plain-language English prose, or using an **ultra-terse formal notation (tabular matrix or symbolic shorthand)** backed by the internal preamble definitions and appendix examples.

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
| **Dual-Will Executor Independence** | When primary and secondary wills exist, verify distinct executors are appointed and enforce inclusion of cross-disqualification provisions. |
| **Quebec Notarial Formalities** | Remind Quebec testators that a will before witnesses requires probate upon death, whereas a notarial will does not. |

---

## 4. Document Generation Suite

Produce the complete four-part deliverable package:

1. **Last Will and Testament (`.md` / `.txt`):**
   - Clean, formal legal instrument (zero software disclaimers or AI metadata).
   - Structured into:
     - *Preliminary Definitions Preamble:* Concise legal definitions governing construction and symbolic notations.
     - *Concise Dispositive Clauses:* Crisp, direct beneficiary designations and appointments (rendered as concise English prose, or an ultra-terse tabular/symbolic formal notation).
     - *Incorporated Testamentary Appendix (Schedule A):* Plain-language mathematical walkthroughs and illustrative examples of share contraction and distribution rules, **executed with initials on every page and witness signatures**.

2. **Provincial Affidavit of Execution / Attestation:**
   - Statutory court form for the specific province (e.g., Ontario Form 74D, BC WESA Supreme Court affidavit, Alberta Form NC 8).

3. **Provincial Signing and Witnessing Guide:**
   - Physical presence rules (two adult witnesses present at the same time).
   - Invalidation risks if beneficiaries sign as witnesses.
   - Initialing all pages in blue ink (including the Incorporated Testamentary Appendix), date, and signature block.

4. **Advisory Safeguards & Validation Report (External Companion Document):**
   - Software and informational disclaimers (recommending review by qualified legal counsel).
   - Summary of validation checks and provincial statutory considerations (e.g., dependant relief duties, witness eligibility).
   - Kept strictly separate from the executed will.
