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
  * Support for **Primary and Secondary (Multiple) Wills** (e.g., Ontario *Granovsky* doctrine; BC *Berkner* regime) to isolate non-probate corporate shares and shareholder loans from public probate tax.
  * Clear situs allocation clauses designating specific assets to specific testamentary instruments without cross-contamination.

### UC-JUR-02: Co-existence and Harmonization with Foreign Wills
* **Status:** Processed
* **Mapped Requirements:** [§4.2.3, §4.3.2 Selective / Non-Revocation Option](file:///home/doug/code/free-willy/docs/REQUIREMENTS.md#43-selective-revocation--preservation-of-foreign-wills)
* **Scenario:** The testator holds assets outside Canada (e.g., vacation property in Florida/Arizona, ancestral property in Europe, bank accounts in the UK/Hong Kong) and either already has an executed foreign will or anticipates executing a separate situs will in that foreign jurisdiction.
* **Requirements Coverage:**
  * **Selective / Carve-Out Revocation Clause:** The standard revocation clause ("I hereby revoke all prior wills and testamentary dispositions...") must *not* inadvertently revoke the foreign will.
  * Precise territorial demarcation (e.g., "revoking all prior wills only insofar as they relate to property situated in Canada").
  * Reciprocal non-conflict confirmation and coordination of debt/tax apportionment clauses so that Canadian executors do not exhaust Canadian assets paying foreign estate/inheritance duties unless intended.

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
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires extension to §4.5: Protective & Discretionary Trusts)
* **Scenario:** A designated beneficiary (e.g., an adult child) is in active bankruptcy, has substantial judgment creditors, operates a high-liability business, or is undergoing contentious matrimonial litigation at the time of distribution.
* **Intent & Legal Invariants:**
  * An outright bequest or fixed trust interest would be seized by a bankruptcy trustee or judgment creditors under provincial execution statutes.
  * The will must establish a **protective determinable trust**: if the beneficiary undergoes bankruptcy, attempts to alienate, assign, or mortgage their interest, or if creditors attempt seizure, their fixed interest immediately terminates.
  * The trust automatically converts into a fully discretionary trust where the trustee may, in absolute discretion, apply income or capital for the maintenance and living expenses of the beneficiary and their dependents, without the beneficiary possessing an enforceable property right that creditors can attach.

---

## 5. Real Property & Family Asset Scenarios

### UC-PROP-01: Life Interest / Exclusive Right of Residence (Blended Families & Qualifying Spousal Trust)
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires new §4.8: Life Interests & Residential Rights of Occupancy)
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
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires extension to §4.5.3: Administrative Powers & Asset Realization)
* **Scenario:** The estate includes a unique asset that cannot be practically subdivided—such as a family recreational cottage, rural real estate, or shares in a closely held family business (CCPC).
* **Intent & Practical Allocation:**
  * One child or group of beneficiaries has a deep personal or operational connection to the asset, while other beneficiaries prefer cash/liquidity.
  * The will grants the designated beneficiary an exclusive option to purchase the property or shares from the estate within a defined window (e.g., within 90 days following the issuance of the grant of probate).
  * **Valuation Mechanism:** The purchase price is determined by an independent accredited appraisal (AACI for real estate; CBV for business shares), optionally with a defined deduction reflecting saved real estate commission (e.g., 3–5%).
  * **Equalization:** The purchase proceeds are paid into the general residue of the estate and distributed among all beneficiaries under the residuary distribution formula, preventing family disputes and forced partition sales under provincial partition legislation.

### UC-PROP-03: Specific Real Estate Gifts Subject to Encumbrance (Mortgage Exoneration vs. Assumption)
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires extension to §4.6.2: Specific Bequests & Real Estate Debt Apportionment)
* **Scenario:** The testator devises a specific real property (e.g., a recreational property or rental condominium) to a specific named beneficiary, but the property is encumbered by an outstanding mortgage, collateral loan, or line of credit.
* **Intent & Practical Allocation:**
  * Under Canadian common law and provincial statutes (e.g., Ontario *Succession Law Reform Act* s. 32; BC *Wills, Estates and Succession Act* s. 47), the statutory default presumption is that **encumbered property bears its own debt**—the specific devisee takes the property subject to the mortgage without exoneration from the residue.
  * The system must allow the testator to make an explicit, informed election:
    1. **Mortgage Assumption (Default):** Devisee takes the property subject to the mortgage and indemnifies the estate against mortgage debt.
    2. **Mortgage Exoneration (Residuary Satisfaction):** Directs the executor to pay off and discharge the mortgage balance in full out of the general estate residue, so the devisee receives unencumbered title.

---

## 6. Personal Effects & Lifetime Advancements

### UC-ASSET-01: Tangible Personal Property & Informal Memorandum of Wishes
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires new §4.9: Tangible Personal Property & Precision Allocation)
* **Scenario:** The testator owns a variety of personal effects, jewelry, heirlooms, furniture, art, vehicles, and tools. They desire to allocate specific items to specific family members, but wish to update their choices periodically without executing a formal will or codicil.
* **Intent & Practical Allocation:**
  * The will bequeaths all tangible personal property to the executor, with a direction to distribute individual items in accordance with any signed, dated, informal **Memorandum of Personal Wishes** left with the will.
  * **Legal Invariants & Probate Protection:** The clause must be expressly framed as **precatory / advisory** to prevent probate registries from requiring the informal memorandum to be submitted for formal probate as an incorporated document (which would freeze probate until the memorandum is found, or trigger requisitions if undated/unwitnessed).
  * **Dispute Fallback Mechanism:** If an item is not mentioned in the memorandum, or if beneficiaries dispute an item, the executor has final binding authority to distribute by agreement, round-robin selection lottery, or sale with proceeds passing into residue.

### UC-LOAN-01: Family Loans, Advances & Hotchpot (Equalization vs. Debt Forgiveness)
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires extension to §4.4: Lifetime Advances & Loan Adjustment)
* **Scenario:** During their lifetime, the testator advanced significant funds to one child (e.g., $150,000 for a home purchase or business startup), documented by a promissory note, loan agreement, or family records.
* **Two Mutually Exclusive Intentions:**
  1. **Debt Forgiveness:** The testator intends for the outstanding debt to be completely canceled and forgiven upon death, releasing the child and their estate from all liability (with clear tax structuring regarding commercial debt forgiveness under **s. 80 of the *Income Tax Act***).
  2. **Hotchpot / Loan Equalization:** The testator intends for all children to receive equal net economic value from the total estate. The outstanding principal balance of the lifetime loan is brought into "hotchpot"—it is conceptually added back to the estate residue, and deducted from that specific child's residuary distribution, so other siblings receive proportionate cash equalization.

---

## 7. Administrative & Personal Directives

### UC-ADMIN-01: Precatory Funeral, Cremation, and Anatomical Gift Directions
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires new §4.10: Funeral Wishes, Remains & Anatomical Gifts)
* **Scenario:** The testator holds strong personal, philosophical, or religious wishes regarding the disposition of their earthly remains (e.g., immediate cremation and scattering of ashes in a specific location; traditional burial in a family plot; or anatomical donation of body/organs for medical research and transplant).
* **Legal Invariants & Provincial Nuance:**
  * Under Canadian common law, the estate executor has the exclusive legal right and duty of custody and disposal of the deceased's body, and **testamentary directions regarding burial or cremation are legally precatory (advisory)** rather than strictly binding.
  * However, clear testamentary recitals provide decisive moral and evidential authority to prevent intra-family deadlock or disputes between surviving spouses and biological children under provincial burial statutes (e.g., Ontario *Funeral, Burial and Cremation Services Act*; BC *Cremation, Interment and Funeral Services Act*).
