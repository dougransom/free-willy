---
name: review-requirements
description: Audits and reviews docs/REQUIREMENTS.md and proposed testamentary specifications to ensure they produce legally valid, enforceable Canadian wills without unnecessary risk of probate delay, court challenge, or tax pitfalls.
---

# Review Requirements Skill (`review-requirements`)

Use this skill whenever:
- Reviewing, auditing, or proposing modifications to [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md).
- Adding or modifying testamentary mechanisms, statutory clauses, or default rules.
- Ensuring the specification produces wills that are **legally valid**, **enforceable**, and **insulated against challenge or probate delay** across all Canadian jurisdictions.

---

## 1. Prime Directive

The core goal of Free-Willy is not merely to generate text that sounds legal, but to produce testamentary documents that:
1. **Pass Probate Court Inspection Without Requisition or Court Intervention:** Every operative clause must be formulated in traditional, clear legal English prose acceptable to conservative court registrars across all provinces and territories.
2. **Withstand Rigorous Litigation Scrutiny:** Minimize any attack surface for disgruntled heirs, omitted dependants, or creditors under common-law and civil-law challenges.
3. **Avoid Devastating Fiscal Traps:** Safeguard tax rollovers, avoid accidental revocation of registered assets, and prevent double taxation on private corporate shares.

---

## 2. The 7 Pillars of Challenge-Resistant Testamentary Design

When reviewing requirements, evaluate every clause and architectural specification against these 7 foundational pillars:

### Pillar 1: Testamentary Capacity & Knowledge/Approval (*Banks v. Goodfellow*)
* **The Legal Test:** The testator must understand the nature of the act, the extent of their property, and the claims of those who might naturally expect to benefit.
* **Challenge Risk:** Challengers frequently allege lack of capacity or lack of knowledge and approval when a will contains bizarre provisions, factual impossibilities, or internal confusion.
* **Requirements Audit Checklist:**
  - [ ] **No Gifting to the Deceased:** The requirements must **never** permit naming beneficiaries known to be dead at the time of drafting under a fictional "survivorship" rule. If a relative is deceased, the will must directly name their issue or frame the clause unambiguously (e.g., *"To the surviving issue of my deceased brother, John"*).
  - [ ] **Clean Legal Instrument:** Software disclaimers, AI metadata, execution audit logs, and educational math walkthroughs must remain **strictly outside** the formal Last Will and Testament to preserve solemnity and avoid confusing the court.
  - [ ] **Clear Language of Intent:** Dispositive clauses must unambiguously express testamentary intent without precatory (wishful) ambiguity.

### Pillar 2: Probate Certainty & Operative Legal Prose
* **The Legal Standard:** Probate registries verify documents on their face. Any ambiguity or non-standard notation triggers a formal requisition or requires an expensive court application for directions.
* **Requirements Audit Checklist:**
  - [ ] **Standard Legal English Prose:** Operative clauses in the will must strictly use traditional, tested legal English phrasing.
  - [ ] **Prohibition of Shorthand / Code Notation:** Experimental notation, algebraic formulas (e.g., `Residue := 3: Alice [PS]...`), or tabular dispositive matrixes must **never** be used as the operative dispositive text in the body of the will.
  - [ ] **Optional Appendices Kept Auxiliary:** Worked arithmetic scenarios belong strictly in an optional illustrative appendix (Schedule A) or the external advisory report, purely to demonstrate intent without displacing operative prose.

### Pillar 3: Undue Influence & Free Agency (*Vout v. Hay*)
* **The Legal Standard:** A will is invalid if coercion overpowered the testator's volition, or if drafted under suspicious circumstances that the propounder fails to dispel.
* **Requirements Audit Checklist:**
  - [ ] **Execution Witness Disqualification:** Absolute prohibition against any beneficiary, spouse of a beneficiary, or non-adult acting as an attesting witness.
  - [ ] **Independent Evidence of Wishes:** For AI-assisted interviews, verify that questions screen for whether the testator is answering freely and not being prompted by a beneficiary.

### Pillar 4: Statutory Formalities & Provincial Execution Rules
* **The Legal Standard:** Failure to adhere to strict statutory formalities invalidates the entire instrument (or forces reliance on costly provincial curative provisions like BC *WESA* s. 58 or Ontario *SLRA* s. 21.1).
* **Requirements Audit Checklist:**
  - [ ] **Physical Presence by Default:** Default signing protocol mandates two adult witnesses physically present simultaneously with the testator and signing in blue ink.
  - [ ] **Provincial Virtual Witnessing Precision:** Where remote audio-visual witnessing is authorized, the requirements must enforce exact statutory conditions:
    - In **Ontario** (*SLRA* s. 4(3)): At least one witness must be a licensed Law Society of Ontario (LSO) lawyer or paralegal.
    - In **British Columbia** (*WESA* s. 35.2): Electronic/counterpart execution must satisfy explicit statutory audio-visual and counterpart rules.
  - [ ] **Quebec Civil Law Alignment:** Distinct treatment for Wills Before Witnesses (*CCQ* Arts. 712–715, requiring probate) vs. Notarial Wills (*CCQ* Art. 717, authentic act bypassing probate). Warn Quebec domiciliaries against multiple wills.

### Pillar 5: Dependant Support Obligations & Moral Claims
* **The Legal Standard:** Statutory family relief allows spouses, children, or dependants to seek court orders overriding the will if adequate provision was not made.
* **Requirements Audit Checklist:**
  - [ ] **Financial Need Jurisdictions (ON, AB, SK, MB, Atlantic):** Audits for omitted spouses, minor children, or adult children who were financially supported at death under provincial statutes (e.g., Ontario *SLRA* Part V, Alberta *WSA*).
  - [ ] **British Columbia Moral Claims (*WESA* s. 60):** In BC, courts have broad discretion under *Tataryn v. Tataryn Estate* to vary a will for adult, independent children based on **moral claims**. The requirements must issue high-priority warnings for BC testators disinheriting adult children.
  - [ ] **Statement of Reasons for Disinheritance:** Where a child or spouse is excluded or treated unequally, provide an optional, separate testamentary memorandum/affidavit of reasons (admissible under *WESA* s. 62) setting forth rational, substantiated reasons, kept confidentially with the executor outside the will.

### Pillar 6: Matrimonial Property Harmonization & Spousal Elections
* **The Legal Standard:** In provinces like Ontario (*Family Law Act* s. 5 & 6), a surviving spouse must choose within 6 months between an equalization of net family property or taking under the will.
* **Requirements Audit Checklist:**
  - [ ] **Express Election Clause:** The will must specify whether gifts to a surviving spouse are **in addition to**, or in satisfaction of, statutory equalization claims, community property rights, or family allowances.
  - [ ] **Common-Law vs. Married Distinction:** Requirements must recognize that common-law partners have no statutory equalization rights in Ontario, but possess broad spousal rights in BC (*WESA* 2-year marriage-like relationship) and Alberta (*Adult Interdependent Relationships Act*).

### Pillar 7: Fiscal Integrity & Income Tax Traps
* **The Legal Standard:** Estates are taxpayers subject to deemed disposition at death under the federal *Income Tax Act* (ITA).
* **Requirements Audit Checklist:**
  - [ ] **30-Day Survivorship Rule:** Survivorship conditions must default to **30 days** (never 90 days) to safeguard the spousal rollover under **s. 70(6) of the *Income Tax Act*** and prevent frozen estate administrations.
  - [ ] **Confirmation of Registered Plans (RRSP/RRIF/TFSA/FHSA) & Insurance:** Explicit non-revocation and confirmation of existing designations made outside the will; specify that terminal income taxes on registered plans are borne by the estate residue.
  - [ ] **Post-Mortem Corporate Reorganization Powers:** For Secondary Wills governing CCPC shares, the executor must have express authority to execute post-mortem reorganizations (ITA s. 164(6) loss carrybacks and pipeline planning) to prevent 70%+ double taxation.
  - [ ] **No Tax Allocation on Cash Bequests:** Canada has no inheritance tax. General pecuniary bequests must not be subjected to "tax allocation" rules.

---

## 3. Step-by-Step Review Workflow

When reviewing [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) or evaluating a proposed change:

### Step 1: Read the Active Requirements
Read the latest version of [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) and identify the specific sections, data schemas, or validation rules being audited or changed.

### Step 2: Audit Against the 7 Pillars
Run through each of the 7 Pillars above:
1. Does this requirement invite a challenge to capacity or knowledge/approval?
2. Does this requirement risk a probate registry requisition or require court intervention?
3. Are execution formalities and witness rules watertight?
4. Are dependant support and BC moral claims addressed?
5. Are matrimonial property elections handled?
6. Are income tax rules (ITA s. 70(6) rollover, s. 164(6) corporate powers, registered plans) respected?
7. Are trustee administrative powers sufficiently comprehensive so the executor does not need court orders?

### Step 3: Check Provincial Nuances
Verify that provincial differences are not conflated:
- **Ontario:** Dual wills with the *same executor* are permitted under *Granovsky*; strict 6-month *FLA* equalization election.
- **British Columbia:** *WESA* s. 60 moral claims for adult independent children; strict audio-visual execution standards (*WESA* s. 35.2).
- **Alberta:** Probate fees capped at $525 (dual wills unnecessary); *WSA* family relief limited to actual financial dependants.
- **Quebec:** Civil law regime (*CCQ*); Notarial wills bypass probate; no ad-valorem probate tax; common-law concepts like *Saunders v. Vautier* or split legal/equitable title do not apply.

### Step 4: Propose Refinements Using Dedicated Tools
If gaps, risks, or inconsistencies are found:
- Edit [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md) using `replace_file_content` (or `write_to_file`).
- **Never use `cat << 'EOF'` or bash heredocs.**
- Preserve clean markdown structure, cross-references, and code block formatting.

---

## 4. Practitioner Red Flag Heuristics

| Red Flag Pattern | Why It Risks Court Challenge or Requisition | Correct Legal Requirement |
| :--- | :--- | :--- |
| **Naming a deceased beneficiary** | Litigators will argue testator lacked capacity or knowledge/approval (*Banks v. Goodfellow*). | Screen for deceased relatives; name their issue directly or state "To the surviving issue of my deceased brother X". |
| **90-day survivorship clause** | Destroys the ITA s. 70(6) spousal rollover if spouse dies between day 31 and 90; freezes estate for 3 months. | Use a standard **30-day survivorship** period. |
| **Symbolic / code math in operative gifts** | Court registrars will requisition the will; forces expensive court applications for directions. | Keep operative clauses in standard legal English prose; relegate calculations to an optional appendix. |
| **Mandatory separate executors in Ontario dual wills** | Unnecessary barrier; *Granovsky* expressly allows the same executor. Creates risk of failed executor appointments. | Allow the same executor under *Granovsky*; rely on asset segregation for the limited grant. |
| **Ignoring BC adult children** | BC courts routinely rewrite wills under *WESA* s. 60 for adult children left out without explanation. | Issue prominent warning; generate an optional *Statement of Reasons for Disinheritance* under *WESA* s. 62. |
| **Missing registered account confirmation** | Risk of litigation over whether general revocation clause revoked prior RRSP/TFSA/insurance designations. | Express clause confirming prior designations and non-revocation. |
| **Omitting post-mortem corporate tax powers** | Executors of CCPC shares face 70%+ double taxation without s. 164(6) loss carryback or pipeline planning powers. | Grant broad authority to conduct post-mortem corporate tax reorganizations. |
| **Applying common law trust rules to Quebec** | Quebec civil law does not recognize split legal/equitable title or *Saunders v. Vautier*. | Restrict common-law trust doctrines to common-law provinces; use CCQ patrimony by appropriation for Quebec. |
