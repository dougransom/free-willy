# Free-Willy: Testamentary Use Cases & Scenario Catalog

**Status:** Living Document / Non-Exhaustive Scenario Catalog  
**Purpose:** Captures practical, real-world testamentary scenarios, relational configurations, and user distribution intents to be processed into formal system requirements, data models, and parameterized legal clauses.

---

## 1. Distribution & Beneficiary Allocation Scenarios

### UC-DIST-01: Proportional Share Allocation Across Heterogeneous Sets and Individuals
* **Status:** Pending Processing
* **Mapped Requirements:** §4.4.3 (Dynamic Share Allocation Model) — *needs extension for heterogeneous sets*
* **Scenario:** The testator does not want simple percentage splits across a flat list of individuals. Instead, the testator conceives of their residue or estate as divided into a total pool of **shares**, where specific quantities of shares are allocated to named individuals or dynamically defined groups of people.
* **Example:**
  * 3 shares allocated to "my children with [Person A]";
  * 2 shares allocated to "my children with my current spouse [Person B]";
  * 1 share allocated to "my sibling [Person C]" (per capita).
* **Division Mechanics:**
  * For groups receiving a block of shares: ability to specify whether intra-group division is **per stirpes** (descendants take deceased parent's share) or **per capita** (only surviving group members divide the block equally, or divide among all members equally).
  * Automatic normalization of arbitrary integer or fractional share ratios into precise legal fractions and percentages without rounding ambiguity.

### UC-DIST-02: Rich Relational Beneficiary Set Definitions
* **Status:** Pending Processing
* **Mapped Requirements:** §4.4.8 (Beneficiary Sets & Class Gifts) — *needs extension for blended relational subsets*
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
* **Status:** Pending Processing
* **Mapped Requirements:** §4.1.1 (Dynamic Priority List Evaluation) — *needs explicit relational generation ordering*
* **Scenario:** The testator establishes an ordered priority list of primary and alternate executors that combines specific named individuals and dynamic relational sequences.
* **Example Priority Sequence:**
  1. Primary: `Person X`
  2. Alternate 1: `Person Y`
  3. Alternate 2+: `my descendants in order of birth` (oldest surviving child, then second oldest, etc.)
  4. Alternate 3+: `my parents' descendants in order of birth` (testator's siblings/half-siblings in descending chronological order)

### UC-EXEC-02: Anticipatory / Deferred Legal Capacity (Temporal Feasibility)
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires new §4.1.5: Temporal Capacity & Minor Executor Devolution)
* **Scenario:** An executor named in the cascade (e.g., an eldest child or teenage sibling) is currently a minor (under the provincial age of majority—18 in ON, AB, SK, MB, QC, PE; 19 in BC, NB, NS, NL, YT, NT, NU) at the time the will is executed.
* **Intent & Context:** The testator is of sound mind and anticipates surviving long enough that the designated executor will reach the age of majority before the will takes effect.
* **Legal Fallback & Temporal Logic:**
  * The will maker must be explicitly protected from claims of incapacity or confusion by clear recital that the designation is intentional and contingent upon attaining the legal age of majority.
  * **Dynamic Status Evaluation:** If the testator dies while the named executor is still a minor, the condition evaluates as legally disabled/ineligible at the operative time (date of death/probate application).
  * The appointment must cleanly and automatically devolve to the next eligible alternate executor in the sequence, with express provision whether the minor may assume or join the role upon reaching majority (e.g., grant of administration with will annexed during minority vs. permanent pass-over to the alternate).

---

## 3. Multi-Jurisdictional, Corporate & Cross-Border Scenarios

### UC-JUR-01: Differential Probate Jurisdiction & Private Corporation Planning
* **Status:** Processed
* **Mapped Requirements:** §4.1.4, §4.2.2 (Secondary / Non-Probate Will - Dual Will Strategy)
* **Scenario:** The testator resides in a jurisdiction with high probate fees (e.g., Ontario Estate Administration Tax at ~1.5% above $50k, or British Columbia at ~1.4%), but holds:
  1. Shares in one or more closely held, privately held Canadian corporations (CCPCs); and/or
  2. Tangible personal property or real estate in jurisdictions with low, capped, or zero probate fees (e.g., Quebec with nominal flat court fees, Alberta with capped fees at $525, or US/foreign situs).
* **Requirements Coverage:**
  * Support for **Primary and Secondary (Multiple) Wills** (e.g., Ontario *Granovsky* doctrine; BC *Berkner* regime) to isolate non-probate corporate shares and shareholder loans from public probate tax.
  * Clear situs allocation clauses designating specific assets to specific testamentary instruments without cross-contamination.

### UC-JUR-02: Co-existence and Harmonization with Foreign Wills
* **Status:** Processed
* **Mapped Requirements:** §4.2.3, §4.3.2 (Selective / Non-Revocation Option)
* **Scenario:** The testator holds assets outside Canada (e.g., vacation property in Florida/Arizona, ancestral property in Europe, bank accounts in the UK/Hong Kong) and either already has an executed foreign will or anticipates executing a separate situs will in that foreign jurisdiction.
* **Requirements Coverage:**
  * **Selective / Carve-Out Revocation Clause:** The standard revocation clause ("I hereby revoke all prior wills and testamentary dispositions...") must *not* inadvertently revoke the foreign will.
  * Precise territorial demarcation (e.g., "revoking all prior wills only insofar as they relate to property situated in Canada").
  * Reciprocal non-conflict confirmation and coordination of debt/tax apportionment clauses so that Canadian executors do not exhaust Canadian assets paying foreign estate/inheritance duties unless intended.

---

## 4. Trust & Protective Provisions

### UC-TRUST-01: Age-Graduated Testamentary Trusts (Delayed Vesting Beyond Age of Majority)
* **Status:** Pending Processing
* **Mapped Requirements:** Unmapped (Requires new §4.8: Testamentary Trusts & Delayed Vesting)
* **Scenario:** The testator wants gifts or residue allocated to any beneficiary under age $X$ (e.g., under 18 or 21) to be held in trust by the executor until that beneficiary reaches age $Y$ (e.g., age 25, 30, or phased tranches such as 1/3 at 21, 1/3 at 25, balance at 30).
* **Requirements to Derive:**
  * Comprehensive testamentary trust terms avoiding the rule in *Saunders v. Vautier* (ensuring gifts do not prematurely collapse and vest absolutely upon the beneficiary reaching provincial age of majority).
  * Discretionary interim encroachment powers for health, education, maintenance, and advancement (*HEMA*).
  * Contingent gift-over provisions in the event the beneficiary dies before attaining age $Y$.
