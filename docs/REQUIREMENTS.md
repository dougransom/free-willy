# Free-Willy: System Requirements Specification

**Project Name:** Free-Willy  
**Repository Location:** `~/code/free-willy`  
**License:** Super Permissive (MIT / 0BSD) with strict "Use at Your Own Risk" disclaimer  
**Target Jurisdictions:** All 10 Canadian Provinces & 3 Territories (Common Law & Quebec Civil Law)  
**Primary Output Documents:** Last Will and Testament, Provincial Affidavit of Execution, Provincial Signing and Witnessing Guide  

---

## 1. Executive Summary & Purpose

**Free-Willy** is an open-source, extensible legal template and document generation system designed to produce legally robust, English-language testamentary documents for residents across all Canadian provinces and territories.

Rather than offering one-size-fits-all static forms, Free-Willy provides parameterized legal templates paired with province-specific statutory boilerplate, formal execution affidavits, and detailed signing guides. The system is founded on two paramount legal principles:
1. **Absolute Testamentary Validity:** Strict compliance with statutory formalities (e.g., signature placement, witness qualifications, attestation language) across all 10 provinces and 3 territories.
2. **Probate Certainty without Court Intervention:** All operative clauses must be formulated in unambiguous, traditional legal English prose designed to pass provincial probate registries (e.g., Ontario Estates Court, BC Supreme Court Probate Registry) without requisition, procedural delay, or expensive applications for court directions.

The system specifically accommodates complex real-world estate planning needs such as:
- Prioritized appointment hierarchies (e.g., dynamic selection such as descendants by decreasing age).
- Multiple wills / secondary wills to minimize probate taxes on Canadian-Controlled Private Corporation (CCPC) shares and private assets (principally in Ontario and British Columbia).
- Confirmation of registered accounts (RRSP, RRIF, TFSA, FHSA) and life insurance designations.
- Comprehensive executor administrative powers eliminating the need for court orders.
- Selective revocation clauses that protect and preserve foreign or extra-provincial wills.
- Clean separation between the executed legal instrument and cautionary advisory/preamble notices.
- Multi-modal consumption: direct human editing, AI-agent collaborative drafting, and programmatic headless compilation.

---

## 2. Jurisdictional Scope & Legal Frameworks

The system must support the statutory formalities and succession laws across all Canadian jurisdictions:

### 2.1 Common Law Provinces and Territories
Templates and statutory clauses must adhere to local succession legislation, including but not limited to:
- **Ontario:** *Succession Law Reform Act* (SLRA), *Estates Administration Act*
- **British Columbia:** *Wills, Estates and Succession Act* (WESA)
- **Alberta:** *Wills and Succession Act* (WSA)
- **Saskatchewan:** *The Wills Act, 1996*
- **Manitoba:** *The Wills Act*
- **Nova Scotia, New Brunswick, Newfoundland and Labrador, Prince Edward Island**
- **Yukon, Northwest Territories, Nunavut**

### 2.2 Quebec (Civil Law)
Quebec succession is governed by the *Civil Code of Québec* (CCQ):
- **English-Language Will Made in the Presence of Witnesses (Art. 712–715 CCQ):** Full English template satisfying the formal requirements of two witnesses and attestation clause.
- **Quebec Notarial Will Compatibility:** English clauses, terminology (e.g., *Liquidator* instead of *Executor*, *Tutor* instead of *Guardian*, *Legacy* instead of *Bequest*), and structural provisions suitable for formalization before a Quebec notary (Art. 717 CCQ).
- **Probate vs. Non-Probate Distinction in Quebec:** Clear guidance reflecting that notarial wills do not require probate, whereas wills before witnesses require probate before the Superior Court or a notary.
- **Single Will Recommendation for Quebec Residents:** Quebec residents must be explicitly warned to create **only one will** (preferably a Notarial Will, or a single Will Before Witnesses). Because Quebec probate fees on non-notarial wills are nominal flat court filing fees (~$100–$200) rather than ad-valorem taxes, and notarial wills bypass probate entirely, dual/multiple wills offer zero probate tax savings in Quebec and only create administrative confusion.
- **Extra-Provincial Situs Wills for Quebec Property:** Non-Quebec residents who own immovable (real) property situated in Quebec frequently execute a separate Quebec will specifically governing their Quebec immovables to avoid cumbersome cross-border probate/homologation proceedings under the CCQ.

### 2.3 French-Language Testamentary Templates (Bilingual & Civil Jurisdictions)
For Canadian provinces and territories that accept French wills directly for probate without requiring translation into English, **French source-of-truth templates will be provided**:
- **Quebec:** French is the official language; French templates provided for Wills Before Witnesses (*testament devant témoins*, Arts. 712–715 CCQ) and Notarial Wills (*testament notarié*, Art. 717 CCQ).
- **New Brunswick:** Officially bilingual (Constitution Act, 1982 s. 16(2); *Official Languages Act*); French wills accepted directly in the Court of King's Bench (Probate Division).
- **Ontario:** Under the *Courts of Justice Act* (s. 125, 126) and *French Language Services Act*, French wills and probate applications are accepted directly.
- **Manitoba:** Under s. 23 of the *Manitoba Act, 1870*, French is an official language of the courts; French wills are probated directly without translation.
- **Territories:** Northwest Territories and Nunavut provide statutory court recognition for French testamentary filings.

---

## 3. Document Deliverables (System Output)

For each generation run, Free-Willy produces core legal documents plus companion advisory and evidence materials:

| Document | Purpose | Placement / Rules |
| :--- | :--- | :--- |
| **Last Will and Testament** | The formal testamentary instrument. | **Strictly clean of software/AI metadata.** Structured into two integrated parts: (1) Preliminary Definitions & Rules of Construction (Internal Preamble); and (2) Operative Dispositive and Administrative Clauses in traditional, unambiguous legal English prose. (An optional Schedule / Appendix of Illustrative Calculations may be attached for construction clarity, signed/initialed on execution). |
| **Affidavit of Execution / Attestation** | Sworn statement by one of the subscribing witnesses before a Commissioner of Oaths or Notary Public. | Province-specific format (e.g., Ontario Form 74D / Rule 74, BC WESA Supreme Court Civil Rules affidavits, Alberta Form NC 8). Required or strongly recommended for probate in all common law provinces. |
| **Signing and Witnessing Guide** | Detailed plain-language execution protocol. | Specifies local rules: physical presence requirement (primary default across Canada), minimum age of witnesses, disqualification of beneficiaries and spouses of beneficiaries, blue ink signing, initialing every page (including schedules/appendices), and notary/commissioner formalities. Also provides statutory remote audio-visual witnessing protocols where permanently authorized (Ontario LSO licensee requirement under SLRA s. 4(3); BC electronic/counterpart execution under WESA s. 35.2). |
| **Advisory Safeguards & Validation Report** | Separate companion sheet providing software legal notices, statutory maintenance warnings, execution checklist, and input validation audit results. | Packaged strictly **outside** the will itself (as a preceding cover sheet or separate document) to preserve legal sanctity. Alerts executors to inter-provincial land resealing, matrimonial property elections, and dependant relief / moral claim duties. |
| **Confidential Digital Asset Memorandum** | Private, unprobated personal memorandum for digital accounts, password manager vaults, and hardware security keys. | Maintained strictly **outside** the public probate process with the testator's personal records to preserve password secrecy, referenced by general authority in the will. |
| **Statement of Reasons for Disinheritance (Optional)** | Evidentiary memorandum / statutory declaration explaining the testator's rationale for excluding or providing unequally for a child or spouse. | Kept with the executor strictly **outside** the will to avoid probate publicity/defamation. Admissible under BC WESA s. 62 and common-law evidence rules to defend against moral claim variation or dependant relief claims. |

---

## 4. Functional Requirements & Estate Features

### 4.1 Prioritized Appointment Lists (Executors & Guardians)
1. **Dynamic Priority List Evaluation & Generational Sequences:**
   - The user specifies an ordered candidate list for Executors (Liquidators in QC) and Guardians (Tutors in QC).
   - The appointee clause must designate the **first individual in the list who is willing and legally competent/able to act**.
   - Must support named individuals (e.g., `[John Doe, Jane Doe]`) as well as dynamic class and generational expressions:
     - `my descendants in order of birth` (oldest surviving child, then second oldest, descending through living issue).
     - `my parents' descendants in order of birth` (testator's siblings/half-siblings in descending chronological order).
2. **Co-Executors & Alternates:**
   - Ability to specify sole executor with alternates, or joint co-executors with survivorship powers.
3. **Compensation, Selective Exclusions & Indexed Fee Schedules:**
   - **Selective Exclusions (Gratuitous Service):** Capability to designate specific named individuals (e.g., `[Person X, Person Y]`, typically a spouse, adult child, or primary beneficiary) who serve without compensation or commission, entitled solely to reimbursement for reasonable out-of-pocket expenses incurred in the administration of the estate.
   - **Structured Remuneration for Other/Alternate Executors:** Any other appointed executor is entitled to compensation in one of three standardized modalities:
     - **Flat Sum:** A fixed dollar compensation payable from the estate upon substantial completion/passing of accounts.
     - **Percentage Fee:** A fixed percentage of the gross value of the estate (or capital and revenue receipts).
     - **Hourly Rate:** A stipulated hourly fee for time reasonably and necessarily expended on estate administration, supported by contemporaneous time dockets.
   - **Annual Compound Escalation / Indexation ($(1+x)^N$):**
     - To protect against currency inflation between will execution and probate, the compensation rate or fee may compound annually at an agreed escalation rate of $x\%$ per annum.
     - **Commencement Date:** Escalation commences on **January 1st of the calendar year immediately following the date of execution** of the will, and compounds every January 1st thereafter.
     - **Formula:** $\text{Effective Rate} = \text{Base Rate} \times (1 + x)^N$, where $N$ represents the number of completed calendar years elapsed between the initial January 1st benchmark date and the date of the testator's death (or date of billing/settlement).
     - **Statutory Override:** The operative clause must explicitly declare that this testamentary fee agreement governs and supersedes default statutory remuneration tariffs under provincial *Trustee Acts* (e.g., Ontario *Trustee Act* s. 61, BC *Trustee Act* s. 88, Alberta *Trustee Act* s. 44).
4. **Dual/Multiple Wills Executor Rules (Probate vs. Non-Probate):**
   - **Ontario Common Executor Rule (*Granovsky*):** Under established Ontario jurisprudence (*Granovsky Estate v. Ontario*, 1998; *Milne Estate*, 2019), the executor of the Primary (Probate) Will and the Secondary (Non-Probate) Will **MAY BE THE EXACT SAME PERSON**. The division between the estates is established by the limited scope of the grant of probate issued by the court (limited to assets under the Primary Will), not by trustee identity. Testators are not forced to appoint different individuals.
   - **Provincial Jurisdictional Nuances:**
     - **Ontario:** Fully supported and widely utilized to minimize Estate Administration Tax (1.5% on estates over $50,000) on private CCPC shares, shareholder loans, and tangible personal property.
     - **British Columbia:** Probate registries scrutinize multiple wills closely under WESA; while secondary wills are used, practitioners may designate distinct trustees or rely on alter ego / joint partner trusts or bare trusts due to registry practices.
     - **Alberta:** Because Alberta caps its probate grant fees at a flat maximum of $525, dual wills to save probate fees are unnecessary and discouraged.
     - **Quebec:** Because non-notarial wills have nominal court filing fees and notarial wills bypass probate entirely, dual wills are unnecessary.
5. **Anticipatory / Deferred Executor Capacity & Devolution (Temporal Logic):**
   - **Anticipatory Appointment of Minors:** Where a named candidate (e.g., a child or sibling) is a minor under the governing provincial age of majority (18 in ON, AB, SK, MB, QC, PE; 19 in BC, NB, NS, NL, YT, NT, NU) at the time of execution ($t_{\text{exec}}$), the clause must include an explicit recital confirming the testator is of sound mind and anticipates that the appointee will attain the age of majority prior to the will taking effect. This recital affirmatively insulates the will against probate requisitions alleging lack of capacity or confusion (*Banks v. Goodfellow*).
   - **Dynamic Evaluation at Operative Date ($t_{\text{death}}$):** Legal capacity and eligibility to act as estate trustee speak from the date of the testator's death. If the named appointee has reached the age of majority at $t_{\text{death}}$, the grant of probate issues directly to them.
   - **Automatic Devolution / Pass-Over:** If the named candidate is still a minor at $t_{\text{death}}$, they are legally disqualified from acting, and the appointment cleanly and automatically devolves to the next alternate executor in the designated priority sequence.
   - **Grant During Minority vs. Permanent Pass-Over:** The system supports configuring whether:
     - (a) The alternate acts permanently to the exclusion of the minor; or
     - (b) The alternate acts under a limited grant during minority (*durante minore aetate*), reserving leave for the minor to apply for probate upon attaining full age.

### 4.2 Scope of Will & Asset Segregation
Free-Willy must support distinct scoping options for the generated will:
1. **General Will (Primary / Probate):**
   - Applies to the worldwide estate or general assets within the province/country of residence that require probate (e.g., real estate titled solely in testator's name, public bank/brokerage accounts).
2. **Secondary / Non-Probate Will (Dual Will Strategy - Chiefly Ontario):**
   - Essential for jurisdictions with high ad-valorem probate fees (Ontario Estate Administration Tax).
   - Governs assets that do not require court-certified probate to transfer, specifically:
     - Shares in private corporations (e.g., CCPCs - Canadian-Controlled Private Corporations).
     - Shareholder loans and promissory notes.
     - Tangible personal property (art, jewelry, collections).
     - Private partnership interests or beneficial interests held under bare nominee agreements.
   - Distinct definitions ensuring no overlap with the Primary Will to prevent accidental revocation or probate fee contamination.
3. **Inter-Provincial Real Estate, Resealing & Multi-Jurisdictional Scoping:**
   - **Single Canadian Will with Resealing (Default Approach):** A single General Canadian Will legally governs all real and personal property across Canadian provinces and territories. Where a testator owns real property in an additional province (e.g., an Ontario domiciliary owning recreational land in BC or rental real estate in Alberta), local land title registries require a local court confirmation. The estate transfers such land via **inter-provincial resealing** (where the probate grant issued in the home province is resealed under local provincial statutes, such as BC WESA / Supreme Court Civil Rules or Alberta Surrogate Rules) or an ancillary grant. The Safeguards Report alerts the executor to necessary resealing steps.
   - **Elective Separate Provincial Property Wills:** If a testator specifically elects to execute a separate will for real property located in another province (or for closely held private shares to minimize probate taxes), Free-Willy accommodates this dual/multiple will architecture with mutual revocation carve-outs (§4.3).
   - **Foreign Real Estate (Outside Canada):** For real estate situated outside Canada (e.g., US, Europe, Mexico), Free-Willy recommends executing separate local situs wills drafted under the governing law of the foreign jurisdiction, and preserves them via the Selective Revocation Clause (§4.3).

### 4.3 Selective Revocation & Preservation of Foreign Wills
1. **Default Revocation:**
   - Standard revocation of all prior testamentary dispositions.
2. **Selective / Non-Revocation Option:**
   - Capability to expressly exempt and preserve validly executed foreign wills or extra-provincial wills (e.g., *"I revoke all previous wills and testamentary dispositions made by me, EXCEPT for my Last Will and Testament dated [Date] governing my real and personal property situated in [Country/Province]"*).

### 4.4 Residuary Estate Distribution
1. **Mandatory Default Rule: *Per Stirpes***:
   - Unless explicitly specified otherwise in the configuration, **all residuary gifts default to *per stirpes*** (by representation / along lineal branches).
   - If a beneficiary predeceases the testator leaving issue (children), that beneficiary's share does not lapse or divide among surviving peers; instead, their share descends down to their surviving children in equal parts.
2. **Explicit *Per Capita* Designation Option:**
   - Any residuary share or bequest may be explicitly overridden and designated as ***per capita*** (by head / only among living members).
   - Under a *per capita* designation, if a beneficiary predeceases the testator, their share does not pass to their children; rather, it is divided among the surviving beneficiaries of that class or lapses into the remaining residue.
3. **Dynamic Share Allocation Model (Variable Denominator & Heterogeneous Sets):**
   - **No Fixed Share Total:** When dividing an estate or fund into shares, the total pool of shares is **strictly determined by the sum of shares gifted**, rather than being constrained to an arbitrary constant like 100 or 100% (e.g., Alice: 3 shares, Bob: 2 shares, Charlie: 1 share = 6 total shares; Alice receives 3/6, Bob 2/6, Charlie 1/6).
   - **Proportional Block Allocation to Heterogeneous Sets & Entities:** The system must support allocating integer or fractional blocks of shares to both individual persons and defined sets or classes of beneficiaries (e.g., 3 shares to "my children with [Person A]", 2 shares to "my children with my current spouse [Person B]", and 1 share to "my sibling [Person C]").
   - **Intra-Group Division Rules for Share Blocks:** For any block of shares assigned to a group or set, the configuration must specify how those shares are divided among the members of the set:
     - ***Per Stirpes* Intra-Group:** The block of shares is divided equally among the living members of the set, with the share of any deceased member descending to their living issue *per stirpes*.
     - ***Per Capita* Intra-Group:** The block of shares is divided equally strictly among the surviving members of the set at the expiration of the 30-day survivorship period; if a member predeceases, the block divides among the remaining living members of that set.
   - **Extinguishment of Unallocatable Shares (Non-Existent Shares):** If any share or entire share block cannot be legally allocated to a designated recipient (e.g., the individual has predeceased with no issue under *per stirpes*, or an entire beneficiary set has no surviving members or issue, or an entity has ceased to exist), **those unallocatable shares cease to exist**.
   - **Automatic Denominator Contraction (Preventing Partial Intestacy):** The total number of shares automatically contracts to the sum of the remaining legally valid shares (e.g., if Charlie's share or an entire group's block fails without alternate takers, those shares cease to exist; the total contracts to the active sum, eliminating undisposed fractional residues and completely preventing partial intestacy).
   - **Precise Normalization in Legal Prose:** The operative legal clause must express the shares both as proportional units and as exact irreducible fractions (e.g., "three-fifths (3/5) of my residuary estate") in standard legal English, accompanied by the dynamic contraction rule.
4. **Distribution Models:**
   - **Spousal Rollover with Gift-Over:** 100% to spouse/partner if surviving the survival period; gift-over to children or named beneficiaries (*per stirpes* by default).
   - **Custom Share Allocations:** Custom named beneficiaries assigned relative share units, governed by the dynamic denominator and non-existent share rules.
5. **Survivorship Condition & 30-Day Default Period:**
   - **Default Survival Period (30 Days):** Unless overridden in configuration, every beneficiary must survive the testator by a minimum of **30 days** to take any gift, share, or bequest. This 30-day standard aligns with Canadian estate practice, safeguards the spousal rollover under **s. 70(6) of the *Income Tax Act***, and prevents protracted administrative delays.
   - **Consequence of Non-Survival:** Any beneficiary who does not survive the 30-day period is legally treated as having predeceased the testator (triggering *per stirpes* descent to children, or share extinguishment under *per capita* / lack of issue).
   - **Handling Beneficiaries Known to be Deceased (Testamentary Capacity Protection):** The system interview must screen for any beneficiaries who have already passed away at the time the will is drafted. To protect against challenges to testamentary capacity (*Banks v. Goodfellow*) or lack of knowledge and approval, the will must **NEVER** name a person known to be deceased as a direct legatee under a fictional survivorship rule. Instead, the language of the will is directly formulated to name their surviving issue, or framed unambiguously (e.g., *"To the surviving issue of my deceased brother, John Smith, in equal shares per stirpes"*).
6. **Arbitrary Multi-Level Conditional Beneficiaries (Gift-Overs):**
   - Any bequest or residuary allocation may specify an ordered sequence of conditional beneficiaries to **any arbitrary level of nesting or conditions** (e.g., Primary Recipient -> Conditional Alternate 1 -> Conditional Alternate 2 -> ... -> Alternate N).
   - **Per Stirpes Precedence Over Conditional Beneficiaries:**
     - For any gift that operates under *per stirpes* (the system default for all residuary gifts, or explicitly designated), **conditional beneficiaries only take effect if the primary beneficiary leaves NO surviving descendants (issue)**.
     - If the primary beneficiary does not survive the 30-day period but leaves living descendants, the gift automatically descends to those descendants *per stirpes*.
     - The first-tier conditional beneficiary is reached only if the primary beneficiary leaves no surviving descendants. If that conditional beneficiary also fails to survive, their descendants take *per stirpes* (if the gift retains *per stirpes* status), and only if they also leave no descendants does the gift progress to subsequent conditional tiers.
   - For gifts explicitly designated *per capita*, conditional beneficiaries take immediately upon the primary beneficiary's failure to survive, without descending to the primary's children.
7. **Catastrophic / Family Wipeout Fallback Clause (Grandparent Lineage & Charity Fallback):**
   - The system must provide a default fallback clause for the entire will to prevent partial or complete intestacy if all primary, substitute, and conditional gifts fail (i.e., complete disaster / family wipeout).
   - **50/50 Spousal and Testator Family Division:** The remaining estate is divided into two equal halves:
     - 50% to the testator's family.
     - 50% to the spouse's family (if married or in a common-law relationship; if unmarried or if one side has no qualifying living descendants, 100% passes to the surviving side).
   - **Parentelic Search Capped at Grandparents' Descendants:**
     - For each family half, the system traces back along lineal ancestry to find the **nearest related ancestor(s) from whom the testator (or spouse) descends who have surviving descendants**, strictly capped at the descendants of **grandparents** (or great-grandparents if explicitly selected).
     - That half is then distributed among those surviving descendants **per stirpes**.
     - Capping the search at grandparents eliminates the multi-generational distant cousin / "heir-hunter" trap, avoiding massive genealogical costs and court *Benjamin Orders*.
   - **Ultimate Charitable Wipeout Gift:**
     - If no surviving descendants of grandparents are found on either or both sides, that portion or the entirety of the estate is **distributed to a named Canadian registered charity**.
     - **Default Registered Charity:** **Cancer Research Society** (*Société de recherche sur le cancer*), Charitable Registration Number: **`11915 3229 RR0001`**, utilizing the testamentary bequest specifications in [`docs/DEFAULT_CHARITY_BENEFICIARY.md`](file:///home/doug/code/free-willy/docs/DEFAULT_CHARITY_BENEFICIARY.md).
8. **Beneficiary Sets, Relational Subsets & Class Gifts:**
   - **Standard Relational Subsets:** The system must recognize and accurately resolve expressive relational class definitions, particularly for modern blended, extended, and multi-generational families:
     - `all_my_children`: All legal children of the testator.
     - `children_with_spouse`: Children born to or legally adopted with the testator's current spouse or partner.
     - `children_with_person_x`: Children born to or legally adopted with a specific named former spouse, co-parent, or individual.
     - `children_from_prior_relationships`: Explicit enumerated list or relational class `[Child 1, Child 2, ...]`.
     - `my_parents`: Testator's surviving parents.
     - `my_grandparents`: Testator's surviving grandparents.
     - `my_cousins`: First cousins (with strict boundary qualification: maternal, paternal, or both; strictly first cousins and excluding cousins once or twice removed).
     - `my_descendants`: Lineal issue down through subsequent generations.
     - Named ad-hoc sets of individuals (e.g., `["Alice Doe", "Bob Roe", "Charlie Smith"]`).
   - **Legal Invariants & Class Boundaries:**
     - **Class Closing Date:** Classes close strictly at the date of the testator's death ($t_{\text{death}}$). No child conceived and born after the testator's death (other than a child *en ventre sa mère* conceived prior to death and subsequently born alive) enters the class.
     - **Adoption Status:** Formally and legally adopted children are treated identically to biological children across all Canadian jurisdictions under provincial child status legislation (e.g., Ontario *Children's Law Reform Act*, BC *Adoption Act*).
     - **Stepchildren Exclusion/Inclusion:** Unadopted stepchildren are **excluded by default** from any class designating "children" or "descendants" unless specifically enumerated or explicitly defined in the class configuration.
   - **Equal Division Among Survivors:** The gifted property or share block is divided in equal shares among the members of the designated set who survive the 30-day survivorship period.
   - **Interaction with Distribution Rules:**
     - Under *per capita*, the pool divides strictly among living members of the set surviving 30 days; deceased members' potential shares drop out.
     - Under *per stirpes*, if any member of the set fails to survive the 30-day period leaving living issue, their equal share descends to their issue *per stirpes*.
9. **Dual Capacity & Multiple Appearance in a Per Stirpes Gift ("Double Dipping" Rules):**
   - When an individual qualifies for a gift through more than one branch of descent or capacity (e.g., descending from two deceased siblings through intermarriage, or qualifying under both an individual share and a class gift):
   - **Default Branch Representation Rule (Cumulative Entitlement):**
     - Under pure *per stirpes*, representation attaches to the **lineal branch of descent (the stirps)** rather than the individual person.
     - By default, an individual who descends through multiple qualifying branches **inherits through each branch independently in proportion to their entitlement in that branch**. Each branch's share is treated as a separate, cumulative testamentary right.
   - **Configurable Anti-Duplication / Single-Share Override:**
     - The configuration may explicitly specify a deduplication rule (`multiple_appearance: "deduplicated"`), providing that an individual may only receive a single share, with any redundant entitlement redistributed among other members of that branch or returning to the residue.
   - **Named + Class Concurrency Rule:**
     - If an individual is explicitly named for an individual share and also qualifies under a general class gift in the same disposition, they receive both entitlements cumulatively unless the will clause explicitly states: *"excluding any person otherwise provided for in this Will"*.
10. **Operative English Legal Prose & Optional Illustrative Appendix:**
    - **Operative Clauses in Standard Legal Prose:** To guarantee probate certainty without court intervention or probate registry requisitions, all dispositive clauses within the body of the will must be formulated in concise, unambiguous traditional legal English prose.
    - **Prohibition of Shorthand/Symbolic Notation in Operative Clauses:** Symbolic or algebraic expressions (such as `Residue := 3: Alice [PS]...`) are strictly prohibited in the operative clauses of the will, as they jeopardize probate grant issuance and invite litigation.
    - **Optional Appendix / Schedule of Illustrative Calculations:** Where beneficial for complex share models, an attached Schedule of Construction & Examples may be incorporated, providing worked arithmetic scenarios to demonstrate testator intent.

### 4.5 Minor Testamentary Trusts & Comprehensive Administrative Powers
1. **Age-Graduated Testamentary Trusts (Delayed Vesting Beyond Age of Majority):**
   - **Delayed Distribution Age Thresholds ($X$ to $Y$):** The system must support establishing testamentary trusts for any beneficiary who is under an entry age $X$ (e.g., under age 18, 21, or 25) at the testator's death, directing the trustee to hold and manage their share in trust until they reach target distribution age $Y$ (e.g., age 21, 25, 30):
     - **Single Distribution Milestones:** Full capital payout upon attaining age $Y$.
     - **Phased / Staged Tranche Distributions:** Fractional capital releases across multiple age milestones (e.g., one-third (1/3) of capital at age 21, one-half (1/2) of the remaining capital at age 25, and the entire remaining balance at age 30).
   - **Provincial Minimum Age of Majority Alignment:** Initial vesting or distribution milestones must be at or above the governing provincial age of majority (minimum **18** in AB, MB, ON, PE, SK, QC; minimum **19** in BC, NB, NL, NS, YT, NT, NU). The validation engine strictly rejects distribution ages below the provincial majority, preventing estate funds from falling into court administration or the provincial Public Guardian and Trustee.
   - **Protection Against Premature Termination (*Saunders v. Vautier* Rule):**
     - Under the common-law rule in *Saunders v. Vautier* (1841), an adult beneficiary with an indefeasibly vested interest can demand immediate distribution upon reaching the provincial age of majority (18 or 19), frustrating the testator's intent to postpone distribution to age 25 or 30.
     - **Mandatory Contingent Gift-Over:** To defeat the rule in *Saunders v. Vautier* and ensure the trust remains enforceable until age $Y$, every delayed vesting trust clause must include an explicit **contingent gift-over** operative in the event the beneficiary dies prior to attaining the designated milestone age (e.g., *"If such beneficiary shall die before attaining the age of twenty-five (25) years, the remaining balance of their share shall be distributed to their living issue per stirpes, or failing issue, shall be added equally to the shares of my other surviving children"*).
     - **Quebec Patrimony by Appropriation:** In Quebec civil law, testamentary trusts are governed under CCQ Arts. 1260–1298 as autonomous patrimonies by appropriation, where the terms of the trust act govern without application of the common-law rule.
   - **Discretionary Interim Encroachment Powers (*HEMA*):**
     - Prior to final distribution at age $Y$, the trustee must possess broad, absolute discretionary powers to encroach upon and pay or apply the whole or any portion of the annual income and capital of the trust fund for the **health, education, maintenance, and advancement in life (*HEMA*)** of the beneficiary.
     - Authority to make payments directly to third-party institutions (e.g., universities, medical providers) or to guardians on behalf of minor beneficiaries without requiring court sanction.
2. **Guardian / Tutor Nomination:**
   - Parental appointment of testamentary guardian/custodian for minor children, subject to provincial court ratification.
3. **Comprehensive Executor & Trustee Administrative Powers (Avoiding Court Orders):**
   The will must confer comprehensive administrative powers on executors and trustees so they can administer the estate smoothly and handle reasonable situations without seeking costly court approval:
   - **Power of Sale and Conversion:** Absolute discretion to sell, call in, and convert any real or personal property by public auction or private contract, on terms they consider best, or to postpone sale indefinitely without liability for loss.
   - **Power to Distribute in Specie (In-Kind Allocation):** Absolute power to make any division, allocation, or distribution of the estate in kind (in specie) or partly in cash and partly in kind, and to determine the fair market value of any asset for distribution purposes, which valuation shall be conclusive and binding on all beneficiaries.
   - **Post-Mortem Corporate Tax Reorganization Powers (Crucial for CCPC Secondary Wills):** Comprehensive authority to implement post-mortem corporate reorganizations (e.g., capital loss carrybacks under **s. 164(6) of the *Income Tax Act***, "pipeline" planning, or s. 85 rollovers) to eliminate double taxation on shares of private corporations.
   - **Power to Make Tax Elections:** Full discretion to make all elections, designations, and determinations under the *Income Tax Act* (federal and provincial), including spousal rollover elections under s. 70(6), capital gains exemption claims, and allocation of tax credits among beneficiaries.
   - **Power to Borrow, Mortgage, and Pledge:** Authority to borrow money from any lender (including an executor in their personal capacity) for estate administration, tax payments, or preservation of assets, and to mortgage or pledge estate property as security.
   - **Power to Compromise and Settle Claims:** Broad power to compromise, compound, arbitrate, or abandon any claims, debts, or liabilities owed to or by the estate without court approval.
   - **Real Estate Management Powers:** Power to manage, lease, repair, alter, develop, insure, or mortgage any real estate held by the estate.
   - **Trustee Investment Discretion (Prudent Investor Expansion):** Broad authority to invest in modern asset classes (mutual funds, index funds, ETFs, real estate, private business debt/equity, digital assets) without regard to statutory diversification ratios or income/capital balancing rules, accompanied by standard exculpatory protections for good-faith decisions.
   - **Discretionary Protective Trusts / Henson Trust Principles:** Discretion to hold funds in a fully discretionary trust for any beneficiary who is incapacitated or receiving provincial disability assistance (e.g., Ontario ODSP, Alberta AISH), ensuring estate distributions do not disqualify them from provincial social support benefits.

### 4.6 Registered Plans, Insurance, Inherited Property, and Digital Assets
1. **Confirmation of Registered Plans (RRSP, RRIF, TFSA, FHSA) & Insurance Designations:**
   - **Non-Revocation & Confirmation Clause:** The will contains an express declaration confirming all prior beneficiary designations for registered retirement savings plans (RRSPs), registered retirement income funds (RRIFs), tax-free savings accounts (TFSAs), first home savings accounts (FHSAs), and life insurance policies made outside the will.
   - **General Revocation Protection:** Explicitly provides that the general revocation clause in the will does **NOT** revoke any instrument designating beneficiaries for registered plans or insurance policies under provincial succession/insurance statutes.
   - **Tax Liability on Registered Accounts Borne by Residue:** Specifies that any terminal income taxes arising from the deemed collapse or disposition of registered plans on death (e.g., RRSP/RRIF deemed income inclusion under the *Income Tax Act*) shall be **borne and paid out of the general residue of the estate**, ensuring the designated beneficiary receives the proceeds without deduction unless a contrary intention is explicitly configured.
2. **Specific Bequests, Inherited Property & Capital Gains Allocation:**
   - Specific sums of money (pecuniary legacies) or identified personal/real property bequeathed to named individuals or registered charities.
   - **No Tax Allocation on Cash Bequests:** In Canada, general pecuniary (cash) bequests carry no inheritance or income tax; cash bequests are never subjected to tax apportionment.
   - **Elective Capital Gains Indemnity on Appreciated Property:** Under s. 70(5) of the *Income Tax Act*, capital property (e.g., real estate, CCPC shares) is deemed disposed of at fair market value at death. By default under Canadian estate law, this terminal tax liability is an estate debt payable out of residue. However, Free-Willy supports an **elective capital gains indemnity clause**: if the testator chooses, the specific beneficiary of appreciated property must indemnify the estate for the terminal capital gains tax attributable to that specific property (via deduction from their residuary share, partial liquidation, or direct payment) as a condition of receiving the bequest. If not elected, the standard legal default applies and taxes are borne by residue.
   - **Provenance Attribution:** Inherited property is explicitly identified along with its ancestral/family source to maintain transparent estate records.
3. **Digital Assets Provision & Password Manager Credential Management:**
   - Express executor authority to access, control, manage, modify, archive, or delete digital accounts, emails, financial portals, cryptocurrencies, cloud storage, and domain names in compliance with service provider terms of service.
   - Express testamentary authorization to utilize password managers (1Password, Bitwarden), encrypted vaults, and hardware security keys (YubiKeys).
   - **Strict Public Will Privacy:** All sensitive master keys, seed phrases, and passwords are kept strictly out of the public will and housed in the confidential **Digital Asset Memorandum**.
4. **Pet Care Provisions:**
   - Bequest of pets to designated caregivers, accompanied by an honorary cash fund or trust for veterinary care and maintenance.

### 4.7 Matrimonial Property Elections & Person Disambiguation
1. **Spousal Matrimonial Property Rights & Common-Law Distinction:**
   - The will includes a standard declaration stating whether gifts made to a surviving spouse are **in addition to**, and not in satisfaction of, any statutory equalization claim, division of matrimonial property, or family relief allowance under governing provincial family law statutes (e.g., Ontario *Family Law Act* s. 5 & 6, Alberta *Family Property Act*, BC *Family Law Act*).
   - **Common-Law vs. Married Harmonization:** The system strictly accounts for provincial differences:
     - In **Ontario**, common-law partners have no statutory property equalization rights under the *Family Law Act* (they only possess dependant support rights under *SLRA* Part V). Equalization election clauses apply exclusively to legally married spouses.
     - In **British Columbia**, partners living in a marriage-like relationship for at least 2 years are recognized as full spouses under *WESA* and the *Family Law Act*.
     - In **Alberta**, interdependent partners are governed by the *Adult Interdependent Relationships Act*.
2. **Machine-Generated Disambiguation of Identical Names:**
   - When identical names occur across any role (executors, trustees, guardians, specific legatees, residuary beneficiaries, or substitute takers), the template rendering engine mandates and incorporates distinguishing attributes (relationship, locality/domicile, seniority qualifier, parentage, or birth year) into the generated legal text, eliminating registry requisitions.
3. **Data Model Representation (Entity Separation):**
   - In declarative configurations, every person has an independent unique identifier (`id`), ensuring they are never conflated by compilers or AI drafting agents, even when string values for `legal_name` or `full_name` are identical.

---

## 5. Template Usage Scenarios & Operational Modes

Free-Willy templates are designed for three primary operational modes:

### 5.1 Direct Human Editing (DIY & Legal Professional Drafting)
- **Manual Clause Customization:** Legal practitioners, paralegals, or self-represented individuals can open templates directly, reading and editing clauses using standard text and Markdown tools.
- **Granular Control:** Direct addition, removal, or inline adjustment of specific administrative powers or distribution clauses without requiring code execution.

### 5.2 AI-Agent-Assisted Drafting & Dedicated Skill
Free-Willy must provide a dedicated, standardized **Agent Skill** (`skills/will-preparation/SKILL.md` / `.agents/skills/will-preparation/SKILL.md`) to guide AI assistants (Gemini, Antigravity, Copilot, Claude, etc.) through the entire end-to-end interactive interview and will preparation process:
1. **Interactive Estate Interviewing & Elicitation:**
   - The skill guides the agent to conduct a structured, empathetic, step-by-step interview with the testator.
   - **Free Agency & Undue Influence Screening (*Vout v. Hay*):** Verifies that the testator is responding freely and independently, without direction, pressure, or coercion from any prospective beneficiary.
   - Collects personal profile, domicile, marital status, children, and dependants.
   - Evaluates scoping needs: single will vs. dual wills (general probate will vs. secondary corporate will for private CCPC shares to minimize provincial probate tax), as well as foreign will preservation.
2. **Identification of Inherited Property & Provenance Tracking:**
   - Prompts the user to identify any gifts originating from inheritance and records the donor/source estate.
3. **Elective Capital Gains Tax Allocation on Appreciated Property:**
   - Explains that general cash bequests trigger zero tax in Canada. For gifts of appreciated capital property (real estate, CCPC shares), explains that deemed disposition taxes are paid by the residue by default, but allows the testator to elect an indemnity condition where the beneficiary reimburses the estate (via residuary offset, partial property liquidation, or direct payment).
4. **Disambiguation of Same-Named Persons:**
   - Detects duplicate names across all parties (executors, guardians, beneficiaries) and enforces distinguishing attributes (relationship, address, seniority qualifier, parentage, or birth year).
5. **Intelligent Distribution & Arithmetic Modeling:**
   - Guides the user through share allocations using variable denominator arithmetic (sum of gifted shares; non-existent shares upon failure).
   - Enforces *per stirpes* by default, with optional explicit *per capita* overrides.
   - Configures arbitrary multi-level conditional beneficiaries (gift-overs), ensuring the agent understands that under *per stirpes*, alternates only take if the primary beneficiary leaves no surviving issue.
   - Configures the 50/50 parentelic catastrophic wipeout fallback clause (splitting between testator and spouse lineages via nearest common ancestors with living descendants).
6. **Statutory Validation & Safeguards Check:**
   - Audits the resulting estate model against provincial requirements: witness eligibility (flagging beneficiaries/spouses), age of majority, family relief / dependant support duties, and Quebec notarial vs. witnessed will formalities.
7. **Clean Document Assembly & Strict Separation:**
   - Instructs the agent on compiling the complete suite of deliverables, strictly preserving the pristine Last Will and Testament free of software metadata, incorporating worked arithmetic walkthroughs into the formally executed Schedule A Appendix, and compiling all software notices, validation audit reports, and statutory warnings into the external companion Advisory Safeguards & Validation Report.

### 5.3 Programmatic & Headless Compilation
- **Batch / Microservice Integration:** Software applications, web portals, or CLI pipelines can ingest declarative data files (YAML/JSON) and programmatically parse, assemble, and render the complete document suite.
- **Dynamic Variable Substitution & Expansion:** Automated engines expand loops, resolve conditions, calculate dynamic share denominators, and inject province-specific statutory boilerplate.

---

## 6. Template Architecture & Canonical Source of Truth

To satisfy human readability, AI-agent processing, and programmatic parsing simultaneously, Free-Willy establishes a strict **Canonical Source of Truth**.

### 6.1 Canonical Format: Structured Markdown with Frontmatter & Semantic Block Tags
The primary source of truth for all templates is **Structured Markdown** paired with **YAML frontmatter** and standardized **semantic block delimiters**:
- **Human-Readable:** Natural Markdown syntax ensures clauses read like standard legal documents.
- **Machine-Parsable:** Frontmatter headers define all machine-interpretable metadata, variables, and constraints.
- **AI-Accessible:** Semantic block markers (`<!-- clause: id --> ... <!-- endclause -->`) make boundaries and dependencies obvious to LLMs.

### 6.2 Modular Clause Library
Rather than maintaining brittle, monolithic legal forms, the repository maintains a **Modular Clause Library** organized by function and jurisdiction:
```text
templates/clauses/
├── appointment/
│   ├── executor_priority_list.md
│   ├── executor_compensation.md
│   └── guardian_priority_list.md
├── revocation/
│   ├── revocation_general.md
│   └── revocation_selective_foreign.md
├── disposition/
│   ├── residue_per_stirpes.md
│   ├── residue_per_capita.md
│   ├── specific_bequest_pecuniary.md
│   └── specific_bequest_property.md
├── trusts/
│   ├── minor_staged_distribution.md
│   └── pet_trust.md
├── administration/
│   ├── digital_assets_powers.md
│   └── general_investments_powers.md
└── jurisdictions/
    ├── on/
    ├── bc/
    ├── ab/
    ├── qc/
    └── ...
```

### 6.3 Formal Clause Frontmatter Schema
Each clause in the modular library must include standardized YAML frontmatter conforming to the following schema:
```yaml
id: "residue_per_stirpes_dynamic_v1"
title: "Residuary Estate Distribution with Dynamic Shares (Per Stirpes)"
purpose: "Divides residue into dynamic shares with automatic contraction for deceased beneficiaries without issue"
category: "disposition" # appointment | revocation | disposition | trust | administration | execution
jurisdictions: ["ALL"] # "ALL" or list of province codes: ["ON", "BC", "AB"]
scope: ["general", "secondary_corporate"]
required_inputs:
  - "beneficiaries.residue"
  - "survivorship_days"
conflicts_with:
  - "residue_per_capita_v1"
requires:
  - "revocation_general"
legal_notes: "Implements default per stirpes rule. Governed by 30-day survival condition."
```

### 6.4 Machine-Readable Clause Manifest / Catalog
- The repository must maintain an indexed manifest (`manifest.yaml` / `clauses.json`) generated from the clause frontmatters.
- The catalog enables programmatic tools and AI agents to query available clauses, evaluate dependency graphs, verify provincial compatibility, and identify missing variables without parsing all raw text files.

### 6.5 AI Agent Prompting & Assembly Guide
- An agent operational skill / guideline (`docs/AI_ASSEMBLY_GUIDE.md`) defining exact prompting protocols, decision trees, and assembly rules.
- Instructs AI models on how to validate input data, resolve priority hierarchies, maintain strict separation between legal documents and advisory preambles, and assemble valid clause sequences.

### 6.6 Validation Linter & Compiler Tooling
- A validation linter and compiler tool to:
  - Verify syntax and schema compliance across all clause files.
  - Detect broken dependencies or conflicting clauses in assembled manifests.
  - Audit variable completeness against supplied user configurations.

### 6.7 French Canonical Templates & Agent Translation Skill
- **Bilingual Source-of-Truth Provision:** For Canadian jurisdictions that accept French wills directly for probate without translation (Quebec, New Brunswick, Ontario, Manitoba, and territories), French source-of-truth templates (`templates/clauses_fr/`) will be provided alongside the English library.
- **Agent Translation Workflow:**
  - The French source-of-truth templates are translated directly from the canonical English templates by the AI agent using a dedicated skill: **`translate-canonical-template-to-french`** (`.agents/skills/translate-canonical-template-to-french/SKILL.md`).
  - **Structural Parity:** Preserves identical YAML frontmatter keys, schema bindings, and semantic block markers (`<!-- clause: id --> ... <!-- endclause -->`).
  - **Jurisdictional Legal French (*Français Juridique*):** Enforces accurate Canadian legal French, distinguishing common law French (*fiduciaire de la succession*, *legs particulier*, *reliquat*) from Quebec civil law (*liquidateur*, *succession*, *légataire à titre particulier*, *legs universel*).

---

## 7. Derived Template Forms & Distribution Formats (To Be Completed Later)

*Note: This section defines the multi-representation architecture for Free-Willy. Specific formats, compilation targets, and generation workflows will be finalized in subsequent design iterations.*

The canonical Source of Truth (Modular Markdown Clause Library) will be compiled or projected into several derived distribution forms:
1. **Assembled / Flattened Monolithic Markdown Templates:** Complete, end-to-end documents per province with inline annotations, optimized for rapid holistic reading by humans and LLM contexts.
2. **Fill-in-the-Blank / Bracketed Draft Forms:** Standalone text documents with bracketed placeholders (`[TESTATOR NAME]`, `[DATE]`) for offline human manual drafting.
3. **Structured JSON / YAML AST Catalog:** Fully structured programmatic representation for headless backends and automated legal tech pipelines.
4. **Additional Formats:** Formats such as formatted PDF, editable DOCX, and printable HTML to be integrated as compilation backends.

---

## 8. Declarative Data Input Specification

User inputs and estate details must be supplied via a clean, declarative configuration file (**YAML / JSON**), structured logically into:

```yaml
testator:
  full_name: "Douglas Edward"
  aliases: ["Doug Edward"]
  domicile:
    street: "123 Maple Leaf Way"
    city: "Toronto"
    province: "ON" # Validated against CA ISO codes
    postal_code: "M5V 2T6"
    citizenship: "Canadian"
  marital_status: "married" # single, married, common_law, divorced, widowed

scope_of_will:
  type: "general" # "general" | "secondary_corporate"
  preserve_foreign_wills:
    enabled: true
    exceptions:
      - jurisdiction: "United Kingdom"
        date_of_will: "2021-04-15"
        description: "Real property situated in England and Wales"

drafting_options:
  gift_clause_style: "standard_legal_english" # Dispositive clauses rendered in unambiguous legal English prose for probate certainty
  include_illustrative_appendix: true # Optional Schedule A with worked calculations to assist executor construction

survivorship_days: 30 # System default: 30 days (protects ITA s. 70(6) spousal rollover and avoids freezes)

appointments:
  executors:
    priority_order:
      - person: "spouse"
      - person: "Jane Doe"
        relationship: "sister"
        address: "Ottawa, ON"
      - class: "descendants_by_decreasing_age"
  # In a Dual-Will plan (e.g. Ontario Primary Probate + Secondary Corporate), executors can be the same person under Granovsky:
  # secondary_will_executors:
  #   priority_order:
  #     - person: "spouse"
  #     - person: "Jane Doe"
  guardians:
    priority_order:
      - person: "Jane Doe"
      - person: "Richard Roe"

beneficiaries:
  residue:
    distribution_rule: "per_stirpes" # "per_stirpes" (default) | "per_capita"
    shares:
      - recipient: "Jane Doe"
        shares: 3
        # Multi-level conditional alternates; under per_stirpes (default),
        # conditionals only apply if Jane Doe leaves no surviving descendants:
        conditional_beneficiaries:
          - recipient: "Richard Roe"
            conditional_beneficiaries:
              - recipient: "Canadian Wildlife Federation"
      - recipient: "Richard Roe"
        shares: 2
      - recipient: "John Smith"
        relationship: "brother"
        address: "Calgary, AB"
        shares: 1
      - recipient: "John Smith"
        relationship: "nephew"
        parentage: "son of my brother John Smith"
        address: "Vancouver, BC"
        shares: 1
        rule_override: "per_capita" # Optional override for specific gift
      - recipient_set: "descendants_of:Richard Roe" # Kinship / lineal set (e.g. "my_children", "descendants_of:...")
        division_mode: "equal_division_among_survivors" # divide equally among living members/branches
        distribution_rule: "per_stirpes"
        shares: 2
        multiple_appearance_rule: "cumulative_by_branch" # "cumulative_by_branch" (default) | "deduplicated"
  minor_trust_age: 25
  fractional_payouts:
    - age: 21
      percentage: 50
    - age: 25
      percentage: 100
  specific_bequests:
    - recipient: "Canadian Red Cross"
      type: "pecuniary"
      amount: 5000.00
      currency: "CAD"
    - recipient: "Jane Doe"
      type: "tangible_property"
      description: "My grandfather's gold pocket watch"
      is_inherited: true
      source_of_property: "Inherited from grandfather (Arthur Doe, Estate of Arthur Doe)"
      conditional_beneficiaries:
        - recipient: "Richard Roe"
  # Default catastrophic wipeout clause for the entire will:
  ultimate_fallback:
    rule: "parentelic_50_50_spousal_split_grandparents" # 50% testator family, 50% spouse family via nearest ancestor with surviving issue per stirpes, capped at grandparents
    capped_lineage: "grandparents" # Tracing capped at grandparents' descendants
    default_charity:
      name: "Cancer Research Society"
      french_name: "Société de recherche sur le cancer"
      registration_number: "11915 3229 RR0001"
      bequest_guide_reference: "docs/DEFAULT_CHARITY_BENEFICIARY.md"
    enabled: true

registered_plans_and_insurance:
  confirm_existing_designations: true
  taxes_borne_by_residue: true

spousal_matrimonial_election:
  treatment: "in_addition_to_equalization" # "in_addition_to_equalization" (default) | "in_satisfaction_of_equalization"

digital_assets:
  authorize_executor_access: true

pets:
  caregiver: "Jane Doe"
  cash_allocation: 2000.00
```

---

## 9. Character Encoding & Typographic Standards

### 9.1 Mandatory UTF-8 Standard
All system components—input files (YAML/JSON), template files, internal strings, and emitted output documents (Markdown, Plain Text, etc.)—**MUST use UTF-8 encoding**. Pure ASCII restrictions are explicitly prohibited.

### 9.2 Unicode Normalization (NFC)
- All string comparisons, name indexing, and text processing must adhere to **Unicode Normalization Form C (NFC)**.
- Prevents mismatched identifiers when names containing accents (e.g., composed `é` vs. combining character `e + ́`) are processed across different operating systems.

### 9.3 Linguistic & Typographic Requirements
- **Canadian Names & Addresses:** Full support for accented characters common in Canadian French, English, and Indigenous names and places (e.g., *François, Bérubé, Montréal, Île-du-Prince-Édouard*).
- **Legal Typography:** Native support for professional typographical characters:
  - Em-dashes (`—`), en-dashes (`–`), ellipses (`…`).
  - Typographic curved quotes (“ ” and ‘ ’).
  - Legal section markers and formatting glyphs (`§`, `¶`, `•`).
  - Currency symbols (`$`, `€`, `£`).

---

## 10. Output Formats & Architecture

1. **Phase 1 Baseline:**
   - **Markdown (`.md`):** Clean, standard GitHub-flavored Markdown formatted for easy diffing, manual customization, and inspection.
   - **Plain Text (`.txt`):** Monospace, indented, cleanly formatted text.
2. **Phase 2 Extensibility:**
   - Clean separation between the data model, domain logic, and renderer, ensuring future plug-and-play support for:
     - Formatted PDF (via Typst, Weasyprint, or LaTeX).
     - Editable Microsoft Word (`.docx`).
     - Printable HTML with print stylesheets (`@media print`).

---

## 11. Legal Safeguards, Validation & Advisory Rules

### 11.1 Built-in Validation Engine
Before generating documents, Free-Willy validates the input data against provincial legal rules:
1. **Witness Eligibility & Undue Influence Safeguards (*Vout v. Hay*):**
   - Warns if any designated executor, beneficiary, or spouse of a beneficiary is listed in execution instructions.
   - Formally alerts the testator that beneficiaries and spouses of beneficiaries must NEVER act as attesting witnesses (rendering gifts void under provincial succession statutes) and should NOT be present in the room during will execution to eliminate any suspicion of coercion or presumption of undue influence.
2. **Age of Majority Checks & Minor Trust Validation:**
   - **Testator Age:** Validates testator minimum age requirements (18 in AB, SK, MB, ON, PEI, QC; 19 in BC, NB, NL, NS, YT, NT, NU), flagging exceptions (e.g., military service or married minors where permitted by statute).
   - **Minor Trust Distribution Milestone Validation:** Strictly rejects any trust distribution milestone set below the governing provincial age of majority (18 or 19), preventing court transfer of funds to the provincial Public Guardian and Trustee.
   - **Saunders v. Vautier Gift-Over Audit:** Validates that any trust with distribution milestones extending beyond the age of majority includes contingent gift-overs to prevent premature trust termination.
3. **Dependant Support Obligations & Moral Claims Audit:**
   - Evaluates whether any spouse, common-law partner, or child is omitted or provided for unequally:
     - **Financial Need Provinces (ON, AB, SK, MB, Atlantic):** Audits for omitted spouses, minor children, or adult children who were financially supported at the time of death, issuing statutory warnings under provincial family relief acts (e.g., Ontario *SLRA* Part V, Alberta *WSA*).
     - **British Columbia Moral Claims (*WESA* s. 60):** In BC, explicitly flags that courts possess statutory authority to vary a will if it fails to make "adequate, just and equitable provision" for adult, financially independent children based on **moral obligations** (*Tataryn v. Tataryn Estate*).
   - **Generation of Statement of Reasons for Disinheritance:**
     - Where a child or spouse is excluded or treated unequally, Free-Willy provides an optional companion **Statement / Memorandum of Reasons for Disinheritance** (maintained confidentially outside the public probate will).
     - Framed to satisfy statutory admissibility requirements (e.g., *WESA* s. 62) by setting out the testator's rational, objective, and substantiated reasons (e.g., lack of relationship, substantial lifetime gifts, greater financial need of other heirs) to assist executors in defending against court variation.
4. **Quebec Formalities Notice:**
   - Notes that a will before witnesses will require probate upon death, whereas a notarial will does not.
5. **Same-Name Disambiguation Enforcement:**
   - Detects when two or more distinct individuals (executors, trustees, guardians, specific legatees, residuary beneficiaries, or substitute takers) share identical legal names.
   - Mandates that differentiating attributes (relationship, locality/residence, seniority qualifier, parentage, or birth year) are provided in the configuration and rendered in all relevant clauses, preventing court confusion and probate delays.
6. **Dual-Will Asset Segregation & Provincial Suitability Audit:**
   - Verifies that when both a Primary (Probate) Will and a Secondary (Non-Probate) Will are generated, the asset definitions are mutually exclusive, preventing probate fee contamination or accidental total revocation.
   - Confirms that in Ontario, the same executor may act under both wills in compliance with *Granovsky* and *Milne*.
   - Alerts testators in Alberta and Quebec that dual wills are unnecessary due to Alberta's flat $525 fee cap and Quebec's nominal court fees.
7. **Digital Asset Privacy & Credential Hygiene Check:**
   - Validates that no plaintext passwords, master encryption keys, cryptocurrency private keys, recovery seed phrases, or sensitive vault credentials are contained in the Last Will and Testament or its attached schedules.
   - Ensures sensitive digital credentials are directed exclusively to the confidential, unprobated **Digital Asset Memorandum**.
8. **Inter-Provincial Real Estate & Resealing Advisory Audit:**
   - Scans asset schedules for real estate situated outside the testator's home province.
   - Generates advisory alerts in the Safeguards Report outlining inter-provincial court resealing or ancillary grant procedures required to transfer out-of-province land title, or validates separate provincial will segregation where chosen.
9. **Virtual Witnessing Statutory Compliance Audit:**
   - Audits signing instructions against provincial remote execution laws:
     - In **Ontario**, verifies inclusion of the statutory mandate requiring at least one witness to be a licensed Law Society of Ontario (LSO) lawyer or paralegal (SLRA s. 4(3)).
     - In **British Columbia**, verifies compliance with WESA s. 35.2 remote audio-visual presence and electronic/counterpart will execution standards.
     - In other common law provinces and territories, warns that physical in-person execution is legally required.
10. **Common-Law vs. Married Matrimonial Election Audit:**
    - Checks testator marital status and province of domicile.
    - Ensures that statutory equalization election clauses under the Ontario *Family Law Act* (s. 5 & 6) are generated only for legally married testators, warning that Ontario common-law partners have no statutory property equalization rights (relegating claims to *SLRA* Part V dependant support or constructive trust claims).
    - Confirms proper application of spousal rights in BC (*WESA* 2-year cohabitation) and Alberta (*Adult Interdependent Relationships Act*).

### 11.2 Separation of Software Metadata & External Advisory Safeguards Report
- **Absolute Rule on Software Disclaimers:** Any software notice, AI metadata, execution checklist, or statutory dependant support / family relief warning generated by Free-Willy **MUST NEVER** be embedded into the Last Will and Testament.
- All non-testamentary cautionary guidance and validation audit logs output strictly to a distinct **External Advisory Safeguards & Validation Report** companion document.

### 11.3 Will Architecture: Internal Definitions Preamble & Incorporated Testamentary Appendix
To ensure beneficiary designations within the operative body of the will remain as concise as possible, explanatory clarity is achieved through two formal testamentary components **within the will itself**:

1. **Internal Definitions Preamble (Within the Body of the Will):**
   - Preceding the dispositive clauses, the will contains a formal preliminary section establishing binding legal definitions for terms used throughout the will (*per stirpes*, *per capita*, *survivor / 30-day survivorship*, *descendants*, *share allocation / non-existent shares*, *dual-capacity representation*).
   - This keeps operative gift clauses crisp and uncluttered while eliminating legal ambiguity.

2. **Incorporated Testamentary Appendix of Illustrative Examples (Part of the Will):**
   - Concrete mathematical walkthroughs and calculation scenarios are placed in an attached **Schedule / Appendix of Construction & Illustrative Examples** (e.g., *Schedule "A"*).
   - **Formally Executed as Part of the Will:** This appendix is an integral, legally binding part of the testamentary instrument. It is executed concurrently with the will and **receives initials on every page and witness signatures**, providing definitive evidence of testator intent for probate registries, trustees, and the courts.
   - The Schedule A Appendix sets out the following illustrative examples in plain language:

1. **Dynamic Share Arithmetic & Non-Existent Shares:**
   - The Appendix documents how shares work with concrete examples:
     > *"How Your Estate Shares Are Calculated:*  
     > *Your estate is divided into shares rather than rigid percentages (like 100%). The total number of shares is simply the sum of all shares given out.*  
     > *If a beneficiary cannot receive their share (for example, if they have died and have no children to inherit under per stirpes), their shares simply **do not exist**. The total share count shrinks automatically, and the remaining beneficiaries divide the estate in proportion to their own shares without leaving any undisposed leftover money."*
   - Illustrate with a concrete example (e.g., 3 shares to Alice, 2 to Bob, 1 to Charlie = 6 shares. If Charlie is ineligible, total becomes 5 shares: 3/5 to Alice, 2/5 to Bob).

2. **The 30-Day Survivorship Rule:**
   - The Appendix demonstrates why and how the 30-day survival rule operates:
     > *"Survivorship Requirement (30 Days):*  
     > *To inherit under this will, a beneficiary must survive you by at least 30 days.*  
     > *This prevents your estate from passing into a deceased beneficiary's estate (avoiding double probate fees and unwanted delays) while fully preserving the spousal rollover under s. 70(6) of the Income Tax Act."*

3. **Per Stirpes vs. Per Capita Distinctions:**
   - The Appendix **demonstrates the legal distinction and practical implications** between *per stirpes* and *per capita* distribution:
     - **Educational Walkthrough:** Illustrate with an intuitive example:
       > *"Per Stirpes (Default): If your estate is divided equally between two children, and one child dies before you leaving two grandchildren, that deceased child's 50% share passes down to those two grandchildren (25% each).*  
       > *Per Capita (Optional Override): Under per capita, the deceased child's share does not go to the grandchildren; instead, the entire estate goes to your surviving child."*
     - **Explicit Confirmation of Defaults:** The text confirms that all residuary gifts operate under *per stirpes* unless an explicit *per capita* designation was chosen.

4. **Elective Capital Gains Indemnity & Inherited Property Disclosures:**
   - The Appendix illustrates how tax obligations on specific gifts of appreciated property operate:
     > *"Taxes on Specific Gifts of Appreciated Property:*  
     > *General cash gifts trigger no income or inheritance tax in Canada. By default, terminal taxes on capital property are paid out of your estate residue. However, where an elective capital gains indemnity clause is chosen, any income taxes triggered by deemed disposition of appreciated property (such as real estate or private shares) are reimbursed by the specific beneficiary receiving that property.*  
     > *The beneficiary can satisfy this indemnity by having it deducted from their share of the residue (if they are also a residuary beneficiary), by selling a portion of the property, or by remitting funds directly to your estate.*  
     > *Inherited property is explicitly identified along with its original donor source to maintain transparent provenance and family records."*

5. **Conditional Beneficiary Mechanics & Catastrophic Family Wipeout Protection:**
   - The Appendix illustrates how multi-level conditional alternates interact with *per stirpes* and how the catastrophic fallback functions:
     > *"Backup / Conditional Beneficiaries:*  
     > *You may name backup beneficiaries to any number of levels for any gift. However, if a gift is given 'per stirpes' (the default rule), your backup beneficiary will ONLY receive the gift if the primary beneficiary dies leaving NO living children or grandchildren. If the primary beneficiary leaves children, the gift passes directly down to those children instead.*  
     > *Ultimate Family Disaster / Wipeout Clause:*  
     > *If everyone you named in your entire will passes away without surviving descendants, your estate will not be lost to the government. Instead, your estate is split 50/50 between your family and your spouse's family, tracing to the closest ancestors who have living descendants up to grandparents (or great-grandparents). If no living descendants of grandparents can be found, the estate is gifted to our default registered Canadian charity, the **Cancer Research Society** (Société de recherche sur le cancer, Registration: 11915 3229 RR0001), in accordance with [`docs/DEFAULT_CHARITY_BENEFICIARY.md`](file:///home/doug/code/free-willy/docs/DEFAULT_CHARITY_BENEFICIARY.md)."*

6. **Beneficiary Sets & Dual-Capacity Representation Rules:**
   - The Appendix illustrates how class gifts and multiple appearances operate:
     > *"Gifts to Groups or Sets of Beneficiaries:*  
     > *You may leave gifts to a group or class (such as 'my children', 'my descendants', or 'the descendants of [Person]'). The property is divided in equal shares among the members of the group who survive you by at least 30 days (with children inheriting their parent's share under per stirpes).*  
     > *If an Individual Inherits Through Multiple Branches:*  
     > *Under a per-stirpes gift, shares attach to family branches rather than specific individuals. If family connections allow an individual to inherit through more than one branch (for example, if cousins married and an heir descends through two branches, or if an heir is given an individual share and also belongs to a class), they receive the share belonging to each branch by default, unless you choose to limit them to a single share."*

---

## 12. Technical Stack & Implementation Guidelines

- **Decoupled Architecture:** As decided during design grilling, the core engine logic (data schemas, clause logic, priority resolver, and validation rules) is abstracted from the final technology implementation.
- **Repository Organization:**
  ```text
  free-willy/
  ├── .agents/
  │   └── skills/
  │       ├── will-preparation/
  │       │   └── SKILL.md
  │       ├── review-will-skill/
  │       │   └── SKILL.md
  │       ├── review-requirements/
  │       │   └── SKILL.md
  │       ├── update-requirements-from-use-cases/
  │       │   └── SKILL.md
  │       └── translate-canonical-template-to-french/
  │           └── SKILL.md
  ├── docs/
  │   ├── REQUIREMENTS.md
  │   ├── USE_CASES.md
  │   ├── DEFAULT_CHARITY_BENEFICIARY.md
  │   └── AI_ASSEMBLY_GUIDE.md
  ├── README.md
  ├── LICENSE
  ├── schema/
  │   ├── testator_input_schema.json
  │   └── clause_frontmatter_schema.json
  ├── templates/
  │   ├── manifest.yaml
  │   ├── clauses/
  │   │   ├── appointment/
  │   │   ├── revocation/
  │   │   ├── disposition/
  │   │   ├── trusts/
  │   │   ├── administration/
  │   │   └── jurisdictions/
  │   ├── clauses_fr/
  │   └── affidavits/
  └── examples/
      ├── ontario_general_will.yaml
      ├── ontario_secondary_corporate_will.yaml
      ├── bc_family_will.yaml
      └── quebec_witnessed_will.yaml
  ```

---

## 13. Licensing & Disclaimer

- **License:** Super permissive (MIT or 0BSD) to encourage unrestricted personal, commercial, or developer adaptation.
- **Liability Disclaimer:** Prominent "AS IS" disclaimer stating:
  > *Free-Willy provides automated self-help legal templates and document generation tools. It is NOT a law firm and does NOT provide legal advice. Estate laws differ by jurisdiction and individual circumstances vary significantly. Use entirely at your own risk. Consultation with a qualified estate planning lawyer or notary in your jurisdiction is strongly recommended.*
