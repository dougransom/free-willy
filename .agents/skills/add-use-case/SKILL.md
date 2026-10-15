---
name: add-use-case
description: Elicits, grills, refines, and catalogs new testamentary scenarios into docs/USE_CASES.md through structured interactive interviewing, probing for Canadian legal invariants, edge cases, tax traps, and practical allocation mechanics.
---

# Add Use Case Skill (`add-use-case`)

Use this skill whenever:
- The user provides an informal idea, scenario fragment, or prompt via `/add-use-case <text>`.
- The user describes a real-world estate planning situation, family structure, or asset distribution pattern that needs to be captured in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md).
- Exploring new edge cases, blended family dynamics, corporate shareholdings, or cross-border assets for Free-Willy.

---

## 1. Prime Directive: Interactive "Grill the User" Protocol

Raw scenario ideas are often vague or legally incomplete (e.g., *"I want to give my cottage to my kids but let my second wife use it"* or *"My executor should be my brother unless he's broke"*).

The agent **must NOT simply accept raw text at face value**. Instead, the agent conducts an interactive **grilling session** to uncover:
1. **Underlying Intent & Competing Interests:** Who benefits, who might feel excluded, and what tensions exist?
2. **Boundary Conditions & Failure Modes:** What happens if someone dies first, dies simultaneously, refuses to act, goes bankrupt, loses mental capacity, or has no children?
3. **Canadian Legal & Statutory Invariants:** How does this operate under common-law provincial statutes (Ontario *SLRA*, BC *WESA*, Alberta *WSA*) versus Quebec civil law (*CCQ*)?
4. **Income Tax & Fiscal Traps:** Does this risk triggering deemed disposition at death under ITA s. 70(5), forfeiture of the s. 70(6) spousal rollover, double taxation on CCPC shares, or debt forgiveness inclusions under ITA s. 80?
5. **Declarative Data Modeling:** How will this intention be parameterized cleanly in YAML/JSON?

---

## 2. Step-by-Step Execution Workflow

### Step 1: Ingest and Analyze Initial Input Text
Parse the user's initial input text from `/add-use-case <text>`. Determine the preliminary category:
- **Distribution & Residue (`UC-DIST`):** Shares, classes, relational subsets, survivorship, gifts-over.
- **Executors & Fiduciaries (`UC-EXEC`):** Priorities, co-executors, minority, compensation, removal.
- **Trusts & Protective Provisions (`UC-TRUST`):** Age tranches, *Saunders v. Vautier*, spendthrift, Henson trusts.
- **Real Property & Unique Assets (`UC-PROP`):** Cottages, life interests, purchase options, encumbrances/mortgages.
- **Corporate & Cross-Border (`UC-JUR` / `UC-CORP`):** Multiple wills, CCPC shares, foreign situs wills, US estate tax.
- **Personal Effects & Advances (`UC-ASSET` / `UC-LOAN`):** Memoranda of wishes, heirlooms, loans, hotchpot.
- **Administrative Directives (`UC-ADMIN`):** Funeral wishes, remains, anatomical gifts, digital accounts.

### Step 2: The Grilling Interview (Iterative Clarification)
Ask probing, targeted questions to unpack the scenario.
- **Use `ask_question`** whenever there are distinct, well-defined legal or architectural options to choose from (e.g., choosing between Model A rollover-preserving trust vs. Model B immediate gift-over; or choosing between per stirpes vs. per capita; or choosing between hotchpot vs. debt forgiveness).
- **Use clear conversational text** when prompting for personal family specifics, asset descriptions, or non-binary nuances.

#### The 5 Essential Grilling Vectors:
1. **Who takes if the primary appointee/beneficiary fails?**
   - Does it descend down to their children (*per stirpes*)?
   - Does it divide among surviving peers (*per capita*)?
   - Does it go to a backup alternate (conditional taker)?
2. **What are the triggering and terminating events?**
   - For rights of residence or trusts: what ends the right (death, remarriage, moving to long-term care, vacancy for >180 days)?
   - For conditional appointments: what disqualifies the fiduciary (minority, bankruptcy, relocation out of Canada)?
3. **Who pays the carrying costs and terminal taxes?**
   - For real estate: who pays municipal taxes, utilities, insurance, vs. structural capital repairs?
   - For mortgages: does the beneficiary assume the debt, or does the residue pay it off?
   - For appreciated capital property: are taxes paid by residue or indemnified by the beneficiary?
4. **How are disputes resolved?**
   - If multiple children want the same heirloom or cottage, who decides (executor discretion, lottery, sale)?
   - If a business interest is involved, how is valuation established (independent CBV appraisal)?
5. **What is the default statutory rule, and is the user overriding it?**
   - e.g., in Ontario/BC, mortgages are assumed by the devisee by default; is an override intended?

### Step 3: Assign Unique Use Case Identifier & Metadata
Determine the next available sequence number within the chosen category in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md):
- Search existing identifiers (e.g., `UC-DIST-01`, `UC-DIST-02` -> next is `UC-DIST-03`).
- Set metadata tags:
  ```markdown
  * **Status:** Pending Processing
  * **Mapped Requirements:** Pending Processing
  * **Last Reviewed:** [YYYY-MM-DD]
  ```

### Step 4: Format the Complete Use Case Entry
Structure the scenario using the standardized Free-Willy template:

```markdown
### UC-<CAT>-<NN>: <Descriptive Scenario Title>
* **Status:** Pending Processing
* **Mapped Requirements:** Pending Processing
* **Scenario:** <Clear narrative describing the testator persona, family context, and practical objective.>
* **Intent & Practical Allocation:**
  * <Detailed bullet points outlining how the mechanism works.>
  * <Division of responsibilities, timing, and conditions.>
* **Legal Invariants & Boundary Rules:**
  * <Provincial statutory constraints, common-law rules, and tax considerations (e.g., ITA s. 70(6), Saunders v. Vautier).>
  * <Failure modes, default rules, and exculpatory provisions.>
* **Example Declarative Configuration:**
  ```yaml
  <Clean YAML snippet illustrating how this scenario will be configured in user input.>
  ```
```

### Step 5: Append to [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md)
- Read the relevant section of [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md) using `view_file`.
- Insert the new use case into the appropriate section using `replace_file_content`.
- **Never use bash heredocs (`cat << 'EOF'`).**

### Step 6: Recommend Next Action
Upon successfully adding the use case, inform the user:
- Summarize the new use case ID and title.
- Point them to the updated section in [`docs/USE_CASES.md`](file:///home/doug/code/free-willy/docs/USE_CASES.md).
- Recommend running `/update-requirements-from-use-cases` to derive the normative specifications into [`docs/REQUIREMENTS.md`](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md).

---

## 3. Grilling Heuristic Reference

| Topic | Questions to Grill the User On |
| :--- | :--- |
| **New Beneficiary Category** | Biological vs adopted? Are stepchildren included or excluded? How does class close (at death vs later)? |
| **Fiduciary / Executor** | What if they are a minor at execution? What if they live outside Canada (non-resident tax withholding)? Are they compensated or serving gratuitously? |
| **Life Estates / Residence** | Rollover-preserving spousal trust (income for life upon sale) or immediate gift-over to children on remarriage/care home (forfeiting s. 70(6) rollover)? Who pays taxes and maintenance? |
| **Specific Gifts / Assets** | Is the property mortgaged? Is it appreciated capital property? Does the gift include contents? What if the asset is sold before death (ademption)? |
| **Family Loans** | Is it intended as debt forgiveness (testamentary bequest avoiding ITA s. 80) or hotchpot (equalizing deduction from residue)? Does it accrue interest? |
| **Business / Shares** | Is it a CCPC? Does the testator have a secondary will in Ontario? Are there shareholder agreements (buy-sell / shotgun clauses)? |
