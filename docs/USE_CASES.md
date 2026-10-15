# Free-Willy: Testamentary Use Cases & Scenario Catalog

**Status:** Living Document / Non-Exhaustive Scenario Catalog  
**Purpose:** Captures practical, real-world testamentary scenarios, relational configurations, and user distribution intents to be processed into formal system requirements, data models, and parameterized legal clauses.

---

## 1. Distribution & Beneficiary Allocation Scenarios

### UC-DIST-01: Proportional Share Allocation Across Heterogeneous Sets and Individuals
* **Status:** Processed
* **Mapped Requirements:** [§4.4.3 Dynamic Share Allocation Model (Variable Denominator & Heterogeneous Sets)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#44-residuary-estate-distribution)
* **Scenario:** The testator does not want simple percentage splits across a flat list of individuals. Instead, the testator conceives of their residue or estate as divided into a total pool of **shares**, where specific quantities of shares are allocated to named individuals or dynamically defined groups of people.
* **Example:**
  * 3 shares allocated to "my children with [Person A]";
  * 2 shares allocated to "my children with my current spouse [Person B]";
  * 1 share allocated to "my sibling [Person C]" (per capita).
* **Division Mechanics:**
  * For groups receiving a block of shares: ability to specify whether intra-group division is **per stirpes** (descendants take deceased parent's share) or **per capita** (only surviving group members divide the block equally, or divide among all members equally).
  * Automatic normalization of arbitrary integer or fractional share ratios into precise legal fractions and percentages without rounding ambiguity.

### UC-DIST-02: Rich Relational Beneficiary Set Definitions
* **Status:** Processed
* **Mapped Requirements:** [§4.4.8 Beneficiary Sets, Relational Subsets & Class Gifts](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#44-residuary-estate-distribution)
* **Scenario:** The system must recognize and accurately resolve standard testamentary relational sets, particularly for modern blended, extended, and multi-generational families, distinguishing between full blood, half blood, step-relations, and specific relationship origins:
  * `all_my_children`: All legal children of the testator.
  * `children_with_spouse`: Children born to or adopted with the current spouse/partner.
  * `children_with_person_x`: Children born to or adopted with a specific named former partner/individual.
  * `children_from_prior_relationships`: Explicit enumerated list or class definition `[Child 1, Child 2, Child 3]`.
  * `my_parents`: Testator's surviving parents.
  * `my_grandparents`: Testator's surviving grandparents.
  * `my_cousins`: First cousins (with clear legal boundary: maternal, paternal, or both; strictly first cousins vs. cousins once removed).
  * `my_descendants`: Lineal descendants down through subsequent generations.
* **Legal Invariants:** Clear definitions of class closing dates (e.g., as of the testator's death), inclusion/exclusion of formally adopted children, and exclusion of unadopted stepchildren unless specifically named.

### UC-DIST-03: Flexible Charitable Bequests (Cash vs. In-Kind Public Securities Optimization & Cy-Près Replacement)
* **Status:** Processed
* **Mapped Requirements:** [§4.6.5 Flexible Charitable Bequests (In-Kind Securities vs. Cash & Cy-Près Replacement)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#46-registered-plans-insurance-inherited-property-and-digital-assets), [§8 Declarative Data Input Specification](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#8-declarative-data-input-specification), [§11.1.17](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#111-built-in-validation-engine), [§11.3.9](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#113-will-architecture-internal-definitions-preamble--incorporated-testamentary-appendix)
* **Last Reviewed:** 2026-10-15
* **Scenario:** The testator wishes to make one or more charitable bequests (fixed pecuniary dollar amounts, percentage shares of residue, entire non-registered accounts, or the ultimate catastrophic wipeout fallback). Rather than rigidly restricting the gift to cash, the testator grants the executor full discretionary authority to satisfy the charitable gift either in cash or by transferring publicly traded securities (stocks, bonds, mutual funds, ETFs) directly in kind. This allows the estate to take advantage of the 0% capital gains inclusion rate under paragraph 38(a.1) of the *Income Tax Act*, completely eliminating capital gains tax on accrued appreciation while generating a 100% fair market value charitable tax receipt. Additionally, the testator provides an express *cy-près* replacement power to ensure gifts do not fail if a charity deregisters or merges prior to distribution.
* **Intent & Practical Allocation:**
  * **Supported Gift Modalities:** Operates across all testamentary charitable gift formats:
    1. *Fixed Pecuniary Sum:* e.g., "$25,000 to Charity X, payable in cash or equivalent publicly traded securities".
    2. *Residuary Share / Percentage:* e.g., "1 share (or 10%) of residue to Charity Y, satisfiable in cash or in kind".
    3. *Identified Portfolio / Account:* Specific devise of an entire non-registered investment portfolio or identified share certificates to a charity.
    4. *Catastrophic Wipeout Fallback:* Ultimate family wipeout gift to a designated charity (e.g., Cancer Research Society) satisfiable in cash or securities.
  * **Absolute Executor Discretion:** The executor is granted sole discretion to assess the estate's tax position upon death, identify securities in the testator's portfolio with the highest accrued capital gains, and decide whether to satisfy the charitable gift in cash, entirely in kind with securities, or in a combination of both.
  * **Valuation Benchmark:** Securities transferred in kind are valued at their **Fair Market Value on the date of transfer / distribution** (closing market price on a recognized stock exchange), ensuring the charity receives exact economic value equivalent to the dollar gift amount.
  * **Express Cy-Près Replacement Power:** If a named charity ceases to exist, amalgamates, or is no longer a registered charity under the *Income Tax Act* at the time of distribution, the gift does not lapse. The executor is granted express authority to redirect the gift to another registered Canadian charity having similar objects or purposes (or to the default Cancer Research Society).
* **Legal Invariants & Boundary Rules:**
  * **Zero Inclusion Rate (ITA s. 38(a.1)):** Under paragraph 38(a.1) of the *Income Tax Act*, the deemed capital gain on publicly traded securities donated directly in kind to a registered charity is reduced to 0%. Selling the shares first and donating the cash results in 50% (or up to 66.67%) capital gains taxation.
  * **Graduated Rate Estate (GRE) Receipt Allocation:** Under ITA s. 118.1(1), charitable donation credits generated by will can offset up to 100% of net income on the terminal return and prior year's return, or be utilized by the GRE across 5 estate tax years.
  * **CRA Qualified Donee Requirement:** The recipient organization must be a registered charity in good standing with the Canada Revenue Agency (holding a valid Business Number ending in RR0001).
  * **No Direct Transfer of Illiquid Private Shares:** Applies specifically to publicly traded securities listed on designated stock exchanges; private CCPC shares remain governed by corporate reorganization powers (§4.5.3).
* **Example Declarative Configuration:**
  ```yaml
  charitable_bequests:
    flexible_satisfaction_mode: "executor_discretion" # "executor_discretion" | "mandatory_in_kind_if_available" | "cash_only"
    valuation_timing: "date_of_distribution" # "date_of_distribution" (closing exchange price) | "date_of_death"
    cy_pres_replacement:
      enabled: true
      fallback_charity: "Cancer Research Society"
    gifts:
      - recipient_name: "Cancer Research Society"
        registration_number: "11915 3229 RR0001"
        type: "pecuniary"
        amount: 25000.00
        currency: "CAD"
        satisfaction_options: ["cash", "in_kind_public_securities"]
      - recipient_name: "Nature Conservancy of Canada"
        registration_number: "11924 6544 RR0001"
        type: "residue_share"
        shares: 1
        satisfaction_options: ["cash", "in_kind_public_securities"]
  ```

### UC-DIST-04: Residuary In-Specie Distribution Protocol (In-Kind Securities Preference vs. Real Estate Liquidation Default)
* **Status:** Processed
* **Mapped Requirements:** [§4.4.12 Residuary In-Specie Distribution Protocol](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#44-residuary-estate-distribution), [§8 Declarative Data Input Specification](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#8-declarative-data-input-specification), [§11.1.18](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#111-built-in-validation-engine), [§11.3.10](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#113-will-architecture-internal-definitions-preamble--incorporated-testamentary-appendix)
* **Last Reviewed:** 2026-10-15
* **Scenario:** The testator holds a mixed residuary estate comprising cash, a non-registered investment portfolio of publicly traded securities (stocks, ETFs, mutual funds), and real estate (e.g., residential or secondary real property not specifically devised to an individual). Rather than applying a blunt "liquidate everything" mandate or an unworkable "distribute everything in kind" requirement, the testator establishes an asset-differentiated distribution protocol:
  1. **Securities:** Preferred distribution **in kind (in specie)** directly to residuary beneficiaries to avoid forced market liquidation, preserve ongoing investment exposure, and transfer stepped-up cost base securities without friction, subject to pragmatic frustration exceptions.
  2. **Real Estate:** Default **liquidation (sale to cash)** by the executor on the open market, avoiding the notorious family disputes and litigation caused by forced co-ownership (tenancy-in-common) under provincial *Partition Acts*, unless all beneficiaries unanimously request title in kind or an heir exercises a buyout option.
* **Intent & Practical Allocation:**
  * **Securities In-Kind Preference & Proportionality:**
    * Publicly traded securities are transferred directly to the investment accounts of residuary beneficiaries *in kind*.
    * *Proportional Slicing:* Each residuary beneficiary receives their exact pro-rata entitlement of *each* individual security holding (e.g., if Alice and Bob are equal 50/50 residuary heirs and the estate holds 100 shares of Company X and 200 units of an index ETF, Alice receives 50 shares of X + 100 units of ETF, and Bob receives 50 shares of X + 100 units of ETF), eliminating disputes over "cherry-picking" higher-yielding or volatile stocks.
  * **Exceptions to In-Kind Securities Distribution (The 5 Frustration Off-Ramps):**
    The executor is empowered to liquidate securities for cash if:
    1. *Estate Debts & Tax Liabilities:* Liquid estate cash is insufficient to satisfy debts, funeral costs, probate taxes (e.g., Ontario Estate Administration Tax, BC probate fees), and terminal income taxes (deemed capital gains at death under ITA s. 70(5)). The executor exercises discretion to liquidate cash-equivalents or securities with capital losses / minimal gains first to preserve preferred assets.
    2. *Beneficiary Express Cash Request:* A beneficiary provides written instructions requesting their share in cash rather than securities.
    3. *Financial Institution / Custodial Impracticability:* A receiving broker, custodian, or platform refuses or is unable to accept the in-kind transfer.
    4. *Odd Lots & Fractional Shares:* Fractional units or odd lots that cannot be cleanly divided among beneficiaries are sold, with the resulting cash distributed to equalize shares.
    5. *Cross-Border / Non-Resident Beneficiary Compliance:* A beneficiary resides outside Canada (e.g., in the US or UK), where Canadian mutual funds or securities cannot be lawfully transferred or would trigger punitive foreign compliance rules or Part XIII non-resident withholding taxes.
  * **Real Estate in Residue (Presumption of Sale to Cash):**
    * Any real property forming part of the general residue is presumed to be sold by the executor on the open market at fair market value, with net sale proceeds distributed in cash.
    * *Off-Ramp 1 (Option to Purchase / Buyout):* Any beneficiary may exercise an exclusive option to purchase or buyout the property in accordance with [§4.5.3 of REQUIREMENTS.md](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#45-minor-testamentary-trusts--comprehensive-administrative-powers) at independent appraised FMV.
    * *Off-Ramp 2 (Unanimous In-Kind Written Election):* If all residuary beneficiaries unanimously sign a written direction requesting an in-kind transfer of title as tenants-in-common (e.g., for a shared rental property), the executor transfers title in kind.
* **Legal Invariants & Boundary Rules:**
  * **Stepped-Up Basis & Rollout (ITA s. 70(5) & s. 107(2)):** At death, the deceased is deemed to dispose of capital property at FMV, and the estate acquires it at an Adjusted Cost Base (ACB) equal to that FMV. When capital property is distributed in satisfaction of capital interests in residue, it generally rolls out at the estate's ACB under ITA s. 107(2) without triggering secondary capital gains for the estate.
  * **Provincial Partition Acts (Avoiding Deadlock):** Transferring undivided fractional title to real estate without unanimous agreement inevitably triggers disputes over occupancy, maintenance, and expenses, forcing an expensive court-ordered sale under provincial statutes (e.g., Ontario *Partition Act*, BC *Partition of Property Act*). The sale presumption protects the estate from litigation.
  * **Prudent Investor Standard:** The executor maintains fiduciary discretion to safeguard estate value and rebalance or liquidate volatile holdings if administration is delayed.
* **Example Declarative Configuration:**
  ```yaml
  residuary_distribution_policy:
    securities:
      default_treatment: "in_kind_proportional" # "in_kind_proportional" | "liquidate_all_to_cash"
      proportional_division: true # Split each holding pro-rata across beneficiaries
      odd_fractional_shares: "liquidate_to_cash"
      frustration_off_ramps:
        pay_debts_and_taxes: true
        beneficiary_cash_election: true
        custodial_unavailability: true
        non_resident_beneficiaries: true
      debt_tax_liquidation_priority: "minimal_capital_gain_first" # "minimal_capital_gain_first" | "pro_rata"
    real_estate:
      default_treatment: "liquidate_to_cash" # "liquidate_to_cash" (standard) | "in_kind_joint"
      allow_unanimous_in_kind_request: true
      recognize_family_buyout_option: true
  ```

---

## 2. Executor & Fiduciary Appointment Scenarios

### UC-EXEC-01: Dynamic & Generational Executor Cascades
* **Status:** Processed
* **Mapped Requirements:** [§4.1.1 Dynamic Priority List Evaluation & Generational Sequences](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#41-prioritized-appointment-lists-executors--guardians)
* **Scenario:** The testator establishes an ordered priority list of primary and alternate executors that combines specific named individuals and dynamic relational sequences.
* **Example Priority Sequence:**
  1. Primary: `Person X`
  2. Alternate 1: `Person Y`
  3. Alternate 2+: `my descendants in order of birth` (oldest surviving child, then second oldest, etc.)
  4. Alternate 3+: `my parents' descendants in order of birth` (testator's siblings/half-siblings in descending chronological order)

### UC-EXEC-02: Anticipatory / Deferred Legal Capacity (Temporal Feasibility)
* **Status:** Processed
* **Mapped Requirements:** [§4.1.5 Anticipatory / Deferred Executor Capacity & Devolution (Temporal Logic)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#41-prioritized-appointment-lists-executors--guardians)
* **Scenario:** An executor named in the cascade (e.g., an eldest child or teenage sibling) is currently a minor (under the provincial age of majority—18 in ON, AB, SK, MB, QC, PE; 19 in BC, NB, NS, NL, YT, NT, NU) at the time the will is executed.
* **Intent & Context:** The testator is of sound mind and anticipates surviving long enough that the designated executor will reach the age of majority before the will takes effect.
* **Legal Fallback & Temporal Logic:**
  * The will maker must be explicitly protected from claims of incapacity or confusion by clear recital that the designation is intentional and contingent upon attaining the legal age of majority.
  * **Dynamic Status Evaluation:** If the testator dies while the named executor is still a minor, the condition evaluates as legally disabled/ineligible at the operative time (date of death/probate application).
  * The appointment must cleanly and automatically devolve to the next eligible alternate executor in the sequence, with express provision whether the minor may assume or join the role upon reaching majority (e.g., grant of administration with will annexed during minority vs. permanent pass-over to the alternate).

### UC-EXEC-03: Differentiated & Indexed Executor Compensation (Fee Schedules & Exclusions)
* **Status:** Processed
* **Mapped Requirements:** [§4.1.3 Compensation, Selective Exclusions & Indexed Fee Schedules](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#41-prioritized-appointment-lists-executors--guardians)
* **Scenario:** The testator establishes distinct compensation rules for executors depending on their identity:
  1. **Excluded Individuals:** Specific individuals (e.g., `Person X`, `Person Y`—frequently a spouse, adult child, or primary beneficiary) serve without compensation or commission, receiving reimbursement solely for reasonable out-of-pocket expenses incurred in the administration of the estate.
  2. **Compensated Individuals:** Any other individual or alternate who acts as executor is entitled to compensation in one of the following structured forms:
     * **Flat Fee:** A fixed dollar sum payable from the estate upon substantial completion/passing of accounts.
     * **Percentage:** A fixed percentage of the gross value of the estate (or capital/revenue receipts).
     * **Hourly Rate:** A defined hourly rate for actual time reasonably expended on estate administration.
  3. **Annual Compound Escalation / Indexation:**
     * To protect against inflation over extended periods between will execution and probate, the compensation rate/fee is escalated annually at an agreed rate of $x\%$ per annum.
     * **Commencement Date:** Indexation begins on **January 1st of the calendar year immediately following the date of execution** of the will, and compounds annually every January 1st thereafter.
     * **Mathematical Formulation:** $\text{Effective Rate} = \text{Base Rate} \times (1 + x)^N$, where $N$ is the number of completed calendar years elapsed between the initial January 1st benchmark date and the date of the testator's death (or date of billing/settlement).
* **Legal Invariants & Certainty:**
  * To avoid court requisition or challenge during a passing of accounts before a provincial court registrar or judge, the operative text must translate the mathematical compounding into unambiguous legal prose while retaining mathematical precision.
  * Explicit confirmation that this contractual testamentary compensation clause overrides default statutory tariffs under provincial *Trustee Acts* (e.g., Ontario *Trustee Act* s. 61, BC *Trustee Act* s. 88).

---

## 3. Multi-Jurisdictional, Corporate & Cross-Border Scenarios

### UC-JUR-01: Differential Probate Jurisdiction & Private Corporation Planning
* **Status:** Processed
* **Mapped Requirements:** [§4.1.4, §4.2.2 Secondary / Non-Probate Will (Dual Will Strategy)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#42-scope-of-will--asset-segregation)
* **Scenario:** The testator resides in a jurisdiction with high probate fees (e.g., Ontario Estate Administration Tax at ~1.5% above $50k, or British Columbia at ~1.4%), but holds:
  1. Shares in one or more closely held, privately held Canadian corporations (CCPCs); and/or
  2. Tangible personal property or real estate in jurisdictions with low, capped, or zero probate fees (e.g., Quebec with nominal flat court fees, Alberta with capped fees at $525, or US/foreign situs).
* **Requirements Coverage:**
  * **Provincial Nomenclature Standards:** Uses **"Primary Will"** and **"Secondary Will"** in Ontario; uses **"Probate Will"** and **"Non-Probate Will"** in British Columbia.
  * **British Columbia Distinct Executor Guardrail (*Berkner Estate*, 2017 BCSC 619):** Under BC Supreme Court Civil Rule 25-3(2) and WESA s. 122, an applicant for probate must disclose all assets passing to that applicant. If the same executor is named in both wills, non-probate assets become subject to BC probate fees (~1.4%). Therefore, in BC, the executors and alternates of the Probate Will and Non-Probate Will **must be completely different individuals or entities** (enforced via system guardrail `BC_DUAL_WILL_SHARED_EXECUTOR_PROHIBITED`).
  * **Ontario Common Executor Permissibility (*Granovsky* / *Milne*):** Under Ontario *Estates Act* s. 32(1), a limited grant of probate is issued; the same executor may act under both the Primary and Secondary Wills.
  * **Asset Segregation & Real Estate Caution:** Isolates CCPC shares, shareholder loans, and nominee/first-dealing real estate from probate, while ensuring ordinary Land Titles Absolute real estate remains in the Primary/Probate Will to prevent probate contamination.
  * Clear situs allocation clauses designating specific assets to specific testamentary instruments without cross-contamination.

### UC-JUR-02: Co-existence and Harmonization with Foreign Wills
* **Status:** Processed
* **Mapped Requirements:** [§4.2.3, §4.3.2 Selective / Non-Revocation Option](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#43-selective-revocation--preservation-of-foreign-wills)
* **Scenario:** The testator holds assets outside Canada (e.g., vacation property in Florida/Arizona, ancestral property in Europe, bank accounts in the UK/Hong Kong) and either already has an executed foreign will or anticipates executing a separate situs will in that foreign jurisdiction.
* **Requirements Coverage:**
  * **Selective / Carve-Out Revocation Clause:** The standard revocation clause ("I hereby revoke all prior wills and testamentary dispositions...") must *not* inadvertently revoke the foreign will.
  * Precise territorial demarcation (e.g., "revoking all prior wills only insofar as they relate to property situated in Canada").
  * Reciprocal non-conflict confirmation and coordination of debt/tax apportionment clauses so that Canadian executors do not exhaust Canadian assets paying foreign estate/inheritance duties unless intended.

### UC-JUR-03: Non-Resident Beneficiary Remittances & Cross-Border Traps (Part XIII Withholding, CRA Clearance & Anti-Bank-Draft Safeguards)
* **Status:** Processed
* **Mapped Requirements:** [§3 Document Deliverables (Estate Executor Guide)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#3-document-deliverables-system-output), [§4.11 Non-Resident Beneficiaries & Cross-Border Remittance Safeguards](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#411-non-resident-beneficiaries--cross-border-remittance-safeguards), [§8 Declarative Data Input Specification](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#8-declarative-data-input-specification), [§11.1.16](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#111-built-in-validation-engine)
* **Last Reviewed:** 2026-10-15
* **Scenario:** The testator designates a beneficiary who is not a resident of Canada for income tax purposes—most frequently a resident or citizen of the United States (e.g., an adult child living in the US), or living in the UK, Europe, or Australia. Distributing estate funds to non-residents exposes lay executors to severe personal tax liability and practical pitfalls, particularly when retail bank tellers casually advise executors to mail a paper bank draft (cashier's check) across the border:
  1. *Personal Liability of the Executor (ITA s. 159):* Under subsection 159(2) and (3) of the *Income Tax Act*, an executor who distributes estate property to a beneficiary prior to obtaining a **CRA Clearance Certificate (Form TX19)** is **personally liable** for all unpaid taxes, penalties, and interest of the deceased and the estate, up to the value of the distributed property. Once funds leave Canada, the CRA cannot easily attach foreign assets and will hold the executor personally responsible.
  2. *Mandatory Part XIII Non-Resident Withholding (ITA s. 212):* Distributing estate income or taxable capital gains to a non-resident requires the executor to withhold Canadian non-resident tax (standard 25%, typically reduced to 15% under tax treaties like the Canada-US Tax Convention) and file an annual NR4 information return. Mailing a full gross distribution without withholding makes the executor personally liable for the unremitted tax plus substantial failure-to-withhold penalties.
  3. *The Bank Draft Hazard:* Physical bank drafts mailed internationally are frequently lost, intercepted, delayed in customs, or subjected to lengthy fraud verification holds by foreign banks. If a paper bank draft is lost, Canadian banks typically require the executor to purchase an expensive personal indemnity bond (often 100%–150% of the draft amount) before reissuing. Furthermore, retail bank branches charge steep 2.5%–3.5% foreign exchange margins on draft conversions.
  4. *US IRS Form 3520 Reporting Trap:* A US-resident beneficiary receiving a distribution from a foreign estate or foreign trust exceeding $100,000 USD must report it to the IRS on **Form 3520**. If the estate does not furnish proper documentation (such as a Foreign Non-Grantor Trust Beneficiary Statement), the IRS can impose draconian failure-to-file penalties starting at 25% to 35% of the gross bequest.
* **Intent & Practical Allocation:**
  * **Companion Unexecuted Executor Guide (Practical Roadblocks & Guidance):**
    * The system produces a companion, unexecuted **Estate Executor Guide** delivered alongside each will (kept strictly distinct from the formal signed will and signing guide).
    * Formally alerts the executor never to follow retail bank teller advice to send paper bank drafts internationally.
    * Mandates using secure electronic wire transfers (SWIFT / Fedwire) with institutional FX services rather than physical paper drafts.
    * Explains the critical necessity of obtaining a CRA Clearance Certificate (TX19) and retaining a sufficient tax holdback reserve before releasing final distributions.
    * Guides the executor on US IRS Form 3520 compliance and providing a Foreign Non-Grantor Trust Beneficiary Statement for US recipients.
  * **Testamentary Administrative Powers (Within the Will):**
    * The will confers express administrative authority empowering the executor to:
      1. *Withhold Part XIII Taxes:* Withhold and remit any applicable Canadian non-resident withholding taxes from estate distributions;
      2. *Establish a Clearance Reserve:* Hold back a reasonable cash tax reserve and postpone final foreign distributions until the Canada Revenue Agency issues a final Certificate of Clearance under s. 159(2) of the *Income Tax Act*;
      3. *Require Tax Information & Documentation:* Demand that non-resident beneficiaries provide foreign tax identification numbers (e.g., US Social Security Number / ITIN), Form W-8BEN, and written confirmation of their tax residency status as a prerequisite to receiving distributions.
* **Legal Invariants & Boundary Rules:**
  * **Section 159(2) & 159(3) *Income Tax Act*:** Absolute statutory personal liability for the legal representative who distributes before obtaining clearance.
  * **Part XIII *Income Tax Act* & Treaty Reductions:** Standard 25% statutory rate reduced by bilateral treaties (e.g., Article XXII of the Canada-US Tax Convention).
  * **Separation of Guidance from Instrument:** Educational bank warnings and tax commentary are placed in the unexecuted companion Executor Guide and Advisory Safeguards Report, preserving the clean solemnity of the formal Last Will.
* **Example Declarative Configuration:**
  ```yaml
  beneficiaries:
    residue:
      shares:
        - recipient: "Sarah Miller"
          relationship: "daughter"
          residence_country: "US" # Non-resident of Canada
          us_tax_person: true # US Citizen / Green Card holder / Resident
          shares: 1

  non_resident_safeguards:
    executor_tax_holdback_authorized: true
    require_cra_clearance_before_final_distribution: true
    mandatory_electronic_remittance_advice: true # Recommends SWIFT wire over physical bank drafts
    generate_executor_guide: true
  ```

---

## 4. Trust & Protective Provisions

### UC-TRUST-01: Age-Graduated Testamentary Trusts (Delayed Vesting Beyond Age of Majority)
* **Status:** Processed
* **Mapped Requirements:** [§4.5.1 Age-Graduated Testamentary Trusts (Delayed Vesting Beyond Age of Majority)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#45-minor-testamentary-trusts--comprehensive-administrative-powers)
* **Scenario:** The testator wants gifts or residue allocated to any beneficiary under age $X$ (e.g., under 18 or 21) to be held in trust by the executor until that beneficiary reaches age $Y$ (e.g., age 25, 30, or phased tranches such as 1/3 at 21, 1/3 at 25, balance at 30).
* **Requirements to Derive:**
  * Comprehensive testamentary trust terms avoiding the rule in *Saunders v. Vautier* (ensuring gifts do not prematurely collapse and vest absolutely upon the beneficiary reaching provincial age of majority).
  * Discretionary interim encroachment powers for health, education, maintenance, and advancement (*HEMA*).
  * Contingent gift-over provisions in the event the beneficiary dies before attaining age $Y$.

### UC-TRUST-02: Spendthrift & Creditor Protective Trusts (Insolvent / At-Risk Beneficiaries)
* **Status:** Processed
* **Mapped Requirements:** [§4.5.4 Spendthrift & Creditor Protective Trusts (Insolvent / At-Risk Beneficiaries)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#45-minor-testamentary-trusts--comprehensive-administrative-powers)
* **Scenario:** A designated beneficiary (e.g., an adult child) is in active bankruptcy, has substantial judgment creditors, operates a high-liability business, or is undergoing contentious matrimonial litigation at the time of distribution.
* **Intent & Legal Invariants:**
  * An outright bequest or fixed trust interest would be seized by a bankruptcy trustee or judgment creditors under provincial execution statutes.
  * The will must establish a **protective determinable trust**: if the beneficiary undergoes bankruptcy, attempts to alienate, assign, or mortgage their interest, or if creditors attempt seizure, their fixed interest immediately terminates.
  * The trust automatically converts into a fully discretionary trust where the trustee may, in absolute discretion, apply income or capital for the maintenance and living expenses of the beneficiary and their dependents, without the beneficiary possessing an enforceable property right that creditors can attach.

---

## 5. Real Property & Family Asset Scenarios

### UC-PROP-01: Life Interest / Exclusive Right of Residence (Blended Families & Qualifying Spousal Trust)
* **Status:** Processed
* **Mapped Requirements:** [§4.8 Life Interests & Residential Rights of Occupancy (Blended Family Housing Trusts)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#48-life-interests--residential-rights-of-occupancy-blended-family-housing-trusts)
* **Scenario:** The testator owns residential real estate (solely or as tenant-in-common) and has children from a previous relationship, alongside a surviving spouse or partner.
* **Intent & Practical Allocation:**
  * The surviving spouse is granted the exclusive right to occupy, use, and enjoy the family home for the duration of the spouse's life (or until an earlier terminating event, such as remarriage, entry into a common-law partnership, permanent vacancy for >$N$ consecutive months, or permanent admission into a specialized long-term care facility).
  * **Allocation of Carrying Costs:** Clear division of financial obligations:
    * *Spouse's Responsibility:* Property taxes, homeowner's insurance, utilities, routine maintenance, and minor repairs.
    * *Estate / Capital Responsibility:* Major structural repairs, replacement of roof/furnace, and mortgage principal (if applicable).
  * **Power to Sell & Downsize:** Trustee power, with the spouse's consent, to sell the home and use the net proceeds to purchase a smaller replacement residence subject to the same terms, or invest the surplus proceeds with income paid to the spouse.
  * **Remainder to Children:** Upon the spouse's death or cessation of residence, the property (or proceeds) vests absolutely in the testator's children in equal shares per stirpes.
  * **Tax Invariants:** Must be drafted to satisfy the strict criteria of a **Qualifying Spousal Trust under s. 70(6) of the *Income Tax Act*** to preserve the tax-deferred spousal capital gains rollover at death.

### UC-PROP-02: Option to Purchase / Right of First Refusal for Family Assets (Cottages & Private Business Shares)
* **Status:** Processed
* **Mapped Requirements:** [§4.5.3 Comprehensive Executor & Trustee Administrative Powers (Option to Purchase)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#45-minor-testamentary-trusts--comprehensive-administrative-powers)
* **Scenario:** The estate includes a unique asset that cannot be practically subdivided—such as a family recreational cottage, rural real estate, or shares in a closely held family business (CCPC).
* **Intent & Practical Allocation:**
  * One child or group of beneficiaries has a deep personal or operational connection to the asset, while other beneficiaries prefer cash/liquidity.
  * The will grants the designated beneficiary an exclusive option to purchase the property or shares from the estate within a defined window (e.g., within 90 days following the issuance of the grant of probate).
  * **Valuation Mechanism:** The purchase price is determined by an independent accredited appraisal (AACI for real estate; CBV for business shares), optionally with a defined deduction reflecting saved real estate commission (e.g., 3–5%).
  * **Equalization:** The purchase proceeds are paid into the general residue of the estate and distributed among all beneficiaries under the residuary distribution formula, preventing family disputes and forced partition sales under provincial partition legislation.

### UC-PROP-03: Specific Real Estate Gifts Subject to Encumbrance (Mortgage Exoneration vs. Assumption)
* **Status:** Processed
* **Mapped Requirements:** [§4.6.2 Specific Bequests, Inherited Property, Encumbered Real Estate & Capital Gains](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#46-registered-plans-insurance-inherited-property-and-digital-assets)
* **Scenario:** The testator devises a specific real property (e.g., a recreational property or rental condominium) to a specific named beneficiary, but the property is encumbered by an outstanding mortgage, collateral loan, or line of credit.
* **Intent & Practical Allocation:**
  * Under Canadian common law and provincial statutes (e.g., Ontario *Succession Law Reform Act* s. 32; BC *Wills, Estates and Succession Act* s. 47), the statutory default presumption is that **encumbered property bears its own debt**—the specific devisee takes the property subject to the mortgage without exoneration from the residue.
  * The system must allow the testator to make an explicit, informed election:
    1. **Mortgage Assumption (Default):** Devisee takes the property subject to the mortgage and indemnifies the estate against mortgage debt.
    2. **Mortgage Exoneration (Residuary Satisfaction):** Directs the executor to pay off and discharge the mortgage balance in full out of the general estate residue, so the devisee receives unencumbered title.

---

## 6. Personal Effects & Lifetime Advancements

### UC-ASSET-01: Tangible Personal Property & Informal Memorandum of Wishes
* **Status:** Processed
* **Mapped Requirements:** [§4.9 Tangible Personal Property & Precision Allocation (Personal Effects)](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#49-tangible-personal-property--precision-allocation-personal-effects)
* **Scenario:** The testator owns a variety of personal effects, jewelry, heirlooms, furniture, art, vehicles, and tools. They desire to allocate specific items to specific family members, but wish to update their choices periodically without executing a formal will or codicil.
* **Intent & Practical Allocation:**
  * The will bequeaths all tangible personal property to the executor, with a direction to distribute individual items in accordance with any signed, dated, informal **Memorandum of Personal Wishes** left with the will.
  * **Legal Invariants & Probate Protection:** The clause must be expressly framed as **precatory / advisory** to prevent probate registries from requiring the informal memorandum to be submitted for formal probate as an incorporated document (which would freeze probate until the memorandum is found, or trigger requisitions if undated/unwitnessed).
  * **Dispute Fallback Mechanism:** If an item is not mentioned in the memorandum, or if beneficiaries dispute an item, the executor has final binding authority to distribute by agreement, round-robin selection lottery, or sale with proceeds passing into residue.

### UC-LOAN-01: Family Loans, Advances & Hotchpot (Equalization vs. Debt Forgiveness)
* **Status:** Processed
* **Mapped Requirements:** [§4.4.11 Lifetime Advances, Family Loans & Hotchpot Clauses](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#44-residuary-estate-distribution)
* **Scenario:** During their lifetime, the testator advanced significant funds to one child (e.g., $150,000 for a home purchase or business startup), documented by a promissory note, loan agreement, or family records.
* **Two Mutually Exclusive Intentions:**
  1. **Debt Forgiveness:** The testator intends for the outstanding debt to be completely canceled and forgiven upon death, releasing the child and their estate from all liability (with clear tax structuring regarding commercial debt forgiveness under **s. 80 of the *Income Tax Act***).
  2. **Hotchpot / Loan Equalization:** The testator intends for all children to receive equal net economic value from the total estate. The outstanding principal balance of the lifetime loan is brought into "hotchpot"—it is conceptually added back to the estate residue, and deducted from that specific child's residuary distribution, so other siblings receive proportionate cash equalization.

---

## 7. Administrative & Personal Directives

### UC-ADMIN-01: Precatory Funeral, Cremation, and Anatomical Gift Directions
* **Status:** Processed
* **Mapped Requirements:** [§4.10 Personal Directives: Funeral Wishes, Remains & Anatomical Gifts](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#410-personal-directives-funeral-wishes-remains--anatomical-gifts)
* **Scenario:** The testator holds strong personal, philosophical, or religious wishes regarding the disposition of their earthly remains (e.g., immediate cremation and scattering of ashes in a specific location; traditional burial in a family plot; or anatomical donation of body/organs for medical research and transplant).
* **Legal Invariants & Provincial Nuance:**
  * Under Canadian common law, the estate executor has the exclusive legal right and duty of custody and disposal of the deceased's body, and **testamentary directions regarding burial or cremation are legally precatory (advisory)** rather than strictly binding.
  * However, clear testamentary recitals provide decisive moral and evidential authority to prevent intra-family deadlock or disputes between surviving spouses and biological children under provincial burial statutes (e.g., Ontario *Funeral, Burial and Cremation Services Act*; BC *Cremation, Interment and Funeral Services Act*).
