# Free-Willy: System Requirements Specification

**Project Name:** Free-Willy  
**Repository Location:** `~/code/free-willy`  
**License:** Super Permissive (MIT / 0BSD) with strict "Use at Your Own Risk" disclaimer  
**Target Jurisdictions:** All 10 Canadian Provinces & 3 Territories (Common Law & Quebec Civil Law)  
**Primary Output Documents:** Last Will and Testament, Provincial Affidavit of Execution, Provincial Signing and Witnessing Guide  

---

## 1. Executive Summary & Purpose

**Free-Willy** is an open-source, extensible legal template and document generation system designed to produce legally robust, English-language testamentary documents for residents across all Canadian provinces and territories.

Rather than offering one-size-fits-all static forms, Free-Willy provides parameterized legal templates paired with province-specific statutory boilerplate, formal execution affidavits, and detailed signing guides. The system specifically accommodates complex real-world estate planning needs such as:
- Prioritized appointment hierarchies (e.g., dynamic selection such as descendants by decreasing age).
- Multiple wills / secondary wills to minimize probate taxes on Canadian-Controlled Private Corporation (CCPC) shares and private assets.
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
- **Quebec Notarial Will Compatibility:** English clauses, terminology (e.g., *Liquidator* instead of *Executor*, *Tutor* instead of *Guardian*, *Legacy* instead of *Bequest*), and structural provisions suitable for formalization before a Quebec notary.
- **Probate vs. Non-Probate Distinction in Quebec:** Clear guidance reflecting that notarial wills do not require probate, whereas wills before witnesses require probate before the Superior Court or a notary.

---

## 3. Document Deliverables (System Output)

For each generation run, Free-Willy produces three core documents plus an advisory preamble:

| Document | Purpose | Placement / Rules |
| :--- | :--- | :--- |
| **Last Will and Testament** | The formal testamentary instrument. | **Strictly clean.** No software warnings, metadata disclaimers, or watermarks on the face of the instrument that could jeopardize probate or court acceptance. |
| **Affidavit of Execution / Attestation** | Sworn statement by one of the subscribing witnesses before a Commissioner of Oaths or Notary Public. | Province-specific format (e.g., Ontario Form 74D / Rule 74, BC WESA Supreme Court Civil Rules affidavits, Alberta Form NC 8). Required or strongly recommended for probate in all common law provinces. |
| **Signing and Witnessing Guide** | Detailed plain-language execution protocol. | Specifies local rules: physical presence requirement, minimum age of witnesses, disqualification of beneficiaries and spouses of beneficiaries, blue ink signing, initialing every page, and notary/commissioner formalities. |
| **Advisory Preamble & Safeguard Summary** | Separate companion sheet providing legal notices, statutory maintenance warnings, share calculation rules, and input validation results. | Packaged strictly **outside** the will itself (as a preceding cover sheet or separate document) to preserve legal sanctity. |

---

## 4. Functional Requirements & Estate Features

### 4.1 Prioritized Appointment Lists (Executors & Guardians)
1. **Dynamic Priority List Evaluation:**
   - The user specifies an ordered candidate list for Executors (Liquidators in QC) and Guardians (Tutors in QC).
   - The appointee clause must designate the **first individual in the list who is willing and legally competent/able to act**.
   - Must support named individuals (e.g., `[John Doe, Jane Doe]`) as well as dynamic class expressions (e.g., `my descendants in order of decreasing age`).
2. **Co-Executors & Alternates:**
   - Ability to specify sole executor with alternates, or joint co-executors with survivorship powers.
3. **Compensation & Expense Reimbursement:**
   - Standard trustee compensation clauses or explicit waiver of executor fees beyond reasonable out-of-pocket expenses.

### 4.2 Scope of Will & Asset Segregation
Free-Willy must support two distinct scoping options for the generated will:
1. **General Will (Primary):**
   - Applies to the worldwide estate or general assets within the province/country of residence.
2. **Secondary / Non-Probate Will (Dual Will Strategy):**
   - Essential for jurisdictions with high probate fees (e.g., Ontario Estate Administration Tax).
   - Governs assets that do not require probate to transfer, specifically:
     - Shares in private corporations (e.g., CCPCs - Canadian-Controlled Private Corporations).
     - Shareholder loans and promissory notes.
     - Tangible personal property (art, jewelry, collections).
     - Private partnership interests or real estate held under beneficial trust arrangements in other provinces.
   - Distinct definitions ensuring no overlap with the Primary Will to prevent accidental total revocation.

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
3. **Dynamic Share Allocation Model (Variable Denominator):**
   - **No Fixed Share Total:** When dividing an estate or fund into shares, the total pool of shares is **strictly determined by the sum of shares gifted**, rather than being constrained to an arbitrary constant like 100 or 100% (e.g., Alice: 3 shares, Bob: 2 shares, Charlie: 1 share = 6 total shares; Alice receives 3/6, Bob 2/6, Charlie 1/6).
   - **Extinguishment of Unallocatable Shares (Non-Existent Shares):** If any share cannot be legally allocated to a designated recipient (e.g., the beneficiary has predeceased the testator with no surviving issue under *per stirpes*, or has predeceased under a *per capita* gift, or is legally disqualified from taking), **those unallocatable shares cease to exist**.
   - **Automatic Denominator Contraction (Preventing Partial Intestacy):** The total number of shares automatically contracts to the sum of the remaining legally valid shares (e.g., if Charlie above is deceased without substitute beneficiaries, Charlie's 1 share ceases to exist; the total contracts to 5 shares, with Alice receiving 3/5 and Bob 2/5). This completely eliminates undisposed fractional residues and prevents partial intestacy.
4. **Distribution Models:**
   - **Spousal Rollover with Gift-Over:** 100% to spouse/partner if surviving the survival period; gift-over to children or named beneficiaries (*per stirpes* by default).
   - **Custom Share Allocations:** Custom named beneficiaries assigned relative share units, governed by the dynamic denominator and non-existent share rules.
5. **Survivorship Condition & 90-Day Default Period:**
   - **Default Survival Period (90 Days):** Unless overridden in configuration, every beneficiary must survive the testator by a minimum of **90 days** to take any gift, share, or bequest.
   - **Unified Survival Rule (Pre- vs. Post-Execution Death Neutrality):** The same legal rules apply regardless of whether a beneficiary passed away *before* or *after* the will was made. The test is strictly binary: **a beneficiary either survives the testator by the full 90-day survival period, or they do not**.
   - **Consequence of Non-Survival:** Any beneficiary who does not survive the 90-day period is legally treated as having predeceased the testator (triggering *per stirpes* descent to children, or share extinguishment under *per capita* / lack of issue).
6. **Arbitrary Multi-Level Conditional Beneficiaries (Gift-Overs):**
   - Any bequest or residuary allocation may specify an ordered sequence of conditional beneficiaries to **any arbitrary level of nesting or conditions** (e.g., Primary Recipient -> Conditional Alternate 1 -> Conditional Alternate 2 -> ... -> Alternate N).
   - **Per Stirpes Precedence Over Conditional Beneficiaries:**
     - For any gift that operates under *per stirpes* (the system default for all residuary gifts, or explicitly designated), **conditional beneficiaries only take effect if the primary beneficiary leaves NO surviving descendants (issue)**.
     - If the primary beneficiary does not survive the 90-day period but leaves living descendants, the gift automatically descends to those descendants *per stirpes*.
     - The first-tier conditional beneficiary is reached only if the primary beneficiary leaves no surviving descendants. If that conditional beneficiary also fails to survive, their descendants take *per stirpes* (if the gift retains *per stirpes* status), and only if they also leave no descendants does the gift progress to subsequent conditional tiers.
   - For gifts explicitly designated *per capita*, conditional beneficiaries take immediately upon the primary beneficiary's failure to survive, without descending to the primary's children.
7. **Default Catastrophic / Family Wipeout Fallback Clause (Parentelic Representation):**
   - The system must provide a default fallback clause for the entire will to prevent partial or complete intestacy if all primary, substitute, and conditional gifts fail (i.e., complete disaster / family wipeout).
   - **50/50 Spousal and Testator Family Division:** The remaining estate is divided into two equal halves:
     - 50% to the testator's family.
     - 50% to the spouse's family (if married or in a common-law relationship; if unmarried or if one side has no qualifying living descendants, 100% passes to the surviving side).
   - **Parentelic Representation Algorithm (Nearest Ancestor with Surviving Descendants):**
     - For each family half, the system traces back along lineal ancestry to find the **nearest related ancestor(s) from whom the testator (or spouse) descends who have surviving descendants** (e.g., parents, and if no surviving descendants of parents, grandparents, and so forth).
     - That half is then distributed among those surviving descendants **per stirpes** (lineal representation).
     - This guarantees the estate never fails for lack of heirs and prevents accidental escheat to the provincial Crown.

### 4.5 Minor Testamentary Trusts & Guardian Appointments
1. **Staged Age of Distribution:**
   - Configurable distribution milestone ages (e.g., age 18/19, 21, 25, or fractional releases such as 50% at 21, balance at 25).
2. **Trustee Discretionary Powers:**
   - Discretionary powers to encroach on income and capital for maintenance, education, advancement, and medical care of minor beneficiaries.
3. **Guardian / Tutor Nomination:**
   - Parental appointment of testamentary guardian/custodian for minor children, subject to provincial court ratification.

### 4.6 Specific Bequests, Inherited Property, Pets, and Digital Assets
1. **Pecuniary & Specific Legacies:**
   - Specific sums of money or identified personal property items bequeathed to named individuals or registered charities.
   - **Multi-Level Conditional Alternates:** Any specific bequest can designate conditional beneficiaries to any depth of nesting. If the gift is governed by *per stirpes*, alternate conditional beneficiaries only take if the primary legatee dies leaving no surviving descendants.
2. **Identification of Inherited Property:**
   - **Explicit Inherited Property Designation:** Any testamentary gift consisting of property that was inherited by the testator must be expressly identified as inherited property in the clause.
   - **Source Attribution:** The clause must explicitly state the source(s) of the property (e.g., inherited from a named benefactor, predecessor estate, family lineage, or specific trust).
3. **Tax Liability & Allocation for Specific Gifts of Financial Value (Beneficiary Responsibility):**
   - **Beneficiary Obligation:** For any specific gifts possessing financial value (e.g., pecuniary legacies, securities, corporate shares, investment accounts, or appreciated property generating capital gains or deemed disposition taxes upon death), any taxes attributable to or arising from the gift must be borne and paid by the beneficiary receiving the gift, rather than depleting the general residue of the estate.
   - **Payment Satisfaction Mechanisms:** The recipient beneficiary must satisfy their apportioned tax liability through one of the following three permitted methods:
     1. **Residuary Offset:** Deducted from the beneficiary's share of any residuary estate (where the recipient is also entitled to a residuary share).
     2. **Partial Sale of Gifted Property:** Liquidating or selling a sufficient portion of the gifted property or asset to remit the required taxes to the estate.
     3. **Direct Remittance to Estate:** Remitting funds directly to the estate executors/liquidators in the required amount to satisfy the tax liability prior to the release or transfer of the property.
   - **Executor Lien / Retention Power:** Executors and trustees are granted the administrative power to hold back delivery or transfer of the specific gift until the beneficiary's tax obligation has been satisfied via one of the three permitted methods.
4. **Digital Assets Provision:**
   - Express executor powers to access, control, modify, archive, or delete digital accounts, email, cryptocurrencies, cloud storage, and domain names in compliance with modern service terms.
5. **Pet Care Provisions:**
   - Bequest of pets to designated caregivers, optionally accompanied by an honorary trust or cash fund for veterinary care and maintenance.

### 4.7 Person Identity & Disambiguation of Identical Names
1. **Machine-Generated Clarity Guarantee:**
   - If two or more distinct individuals identified in the will share the exact same legal name (e.g., senior and junior, parent and child, cousins, or unrelated individuals), the machine-generated will must make each person's identity unmistakably distinct in every clause where they are referenced.
2. **Mandatory Disambiguating Attributes:**
   - When identical names occur across any role (executors, trustees, guardians, specific legatees, residuary beneficiaries, or substitute takers), the template rendering engine must mandate and incorporate one or more disambiguating attributes into the generated legal text:
     - **Relationship to Testator:** (e.g., *"my brother John Smith"*, *"my nephew John Smith"*).
     - **Current Residential Locality / Domicile:** (e.g., *"of the City of Calgary, Alberta"*, *"currently residing in Halifax, Nova Scotia"*).
     - **Generational / Seniority Qualifiers:** (e.g., *"John Smith, Senior"*, *"John Smith, Junior"*).
     - **Parentage / Lineage Details:** (e.g., *"the son of my sister Mary Doe"*).
     - **Date / Year of Birth:** (e.g., *"born July 14, 1980"*), where relationship and address alone are insufficient to distinguish peers.
3. **Data Model Representation (Entity Separation):**
   - In declarative configurations, every person must have an independent, distinct entity representation or unique identifier (`id`), ensuring they are never conflated by compilers or AI drafting agents, even when string values for `legal_name` or `full_name` are identical.

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
   - Collects personal profile, domicile, marital status, children, and dependants.
   - Evaluates scoping needs: single will vs. dual wills (general probate will vs. secondary corporate will for private CCPC shares to minimize provincial probate tax), as well as foreign will preservation.
2. **Identification of Inherited Property & Provenance Tracking:**
   - Prompts the user to identify any gifts originating from inheritance and records the donor/source estate.
3. **Tax Apportionment on Financial Gifts:**
   - Explains and structures beneficiary tax responsibility on specific gifts possessing financial value, selecting between residuary offset, partial property liquidation, or direct estate reimbursement.
4. **Disambiguation of Same-Named Persons:**
   - Detects duplicate names across all parties (executors, guardians, beneficiaries) and enforces distinguishing attributes (relationship, address, seniority qualifier, parentage, or birth year).
5. **Intelligent Distribution & Arithmetic Modeling:**
   - Guides the user through share allocations using variable denominator arithmetic (sum of gifted shares; non-existent shares upon failure).
   - Enforces *per stirpes* by default, with optional explicit *per capita* overrides.
   - Configures arbitrary multi-level conditional beneficiaries (gift-overs), ensuring the agent understands that under *per stirpes*, alternates only take if the primary beneficiary leaves no surviving issue.
   - Configures the 50/50 parentelic catastrophic wipeout fallback clause (splitting between testator and spouse lineages via nearest common ancestors with living descendants).
6. **Statutory Validation & Safeguards Check:**
   - Audits the resulting estate model against provincial requirements: witness eligibility (flagging beneficiaries/spouses), age of majority, family relief / dependant support duties, and Quebec notarial vs. witnessed will formalities.
7. **Clean Document Assembly & Separation:**
   - Instructs the agent on compiling the four deliverables, strictly preserving the pristine Last Will and Testament free of software metadata, while compiling all validation reports, educational math walkthroughs, and legal notices into the companion Advisory Preamble.

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
legal_notes: "Implements default per stirpes rule. Pre-death and post-execution deaths treated identically under 90-day survival condition."
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

survivorship_days: 90 # System default: 90 days

appointments:
  executors:
    priority_order:
      - person: "spouse"
      - person: "Jane Doe"
        relationship: "sister"
        address: "Ottawa, ON"
      - class: "descendants_by_decreasing_age"
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
      tax_allocation:
        borne_by: "beneficiary" # "beneficiary" (default for financial gifts) | "estate_residue"
        payment_method: "residue_offset" # "residue_offset" | "partial_sale" | "remit_funds"
    - recipient: "Jane Doe"
      type: "tangible_property"
      description: "My grandfather's gold pocket watch"
      is_inherited: true
      source_of_property: "Inherited from grandfather (Arthur Doe, Estate of Arthur Doe)"
      tax_allocation:
        borne_by: "beneficiary"
        payment_method: "remit_funds"
      conditional_beneficiaries:
        - recipient: "Richard Roe"
  # Default catastrophic wipeout clause for the entire will:
  ultimate_fallback:
    rule: "parentelic_50_50_spousal_split" # 50% testator family, 50% spouse family via nearest ancestor with surviving issue per stirpes
    enabled: true

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
1. **Witness Eligibility:**
   - Warns if any designated executor, beneficiary, or spouse of a beneficiary is listed in execution instructions.
2. **Age of Majority Checks:**
   - Validates testator minimum age requirements (18 in AB, SK, MB, ON, PEI, QC; 19 in BC, NB, NL, NS, YT, NT, NU), flagging exceptions (e.g., military service or married minors where permitted by statute).
3. **Dependant Support Obligations (Family Relief):**
   - Issues warnings where provincial statutes impose mandatory claims for spouses or dependent children (e.g., Ontario SLRA Part V, BC WESA Part 4) if the distribution omits a dependent.
4. **Quebec Formalities Notice:**
   - Notes that a will before witnesses will require probate upon death, whereas a notarial will does not.
5. **Same-Name Disambiguation Enforcement:**
   - Detects when two or more distinct individuals (executors, trustees, guardians, specific legatees, residuary beneficiaries, or substitute takers) share identical legal names.
   - Mandates that differentiating attributes (relationship, locality/residence, seniority qualifier, parentage, or birth year) are provided in the configuration and rendered in all relevant clauses, preventing court confusion and probate delays.

### 11.2 Strict Preamble Separation Principle
- **Absolute Rule:** Any advisory note, validation warning, software metadata, or legal disclaimer generated by Free-Willy **MUST NEVER** be embedded into the body of the Last Will and Testament.
- All cautionary guidance and validation reports must output to a distinct **Advisory Preamble / Summary** or separate companion file.

### 11.3 Plain-Language Educational Guidance in Preamble: Distribution Mechanics & Share Arithmetic
The Advisory Preamble **must clearly explain both the share division mathematics, the 90-day survivorship condition, and the *per stirpes* vs. *per capita* rules** in plain, accessible language:

1. **Dynamic Share Arithmetic & Non-Existent Shares:**
   - The preamble must explicitly document how shares work:
     > *"How Your Estate Shares Are Calculated:*  
     > *Your estate is divided into shares rather than rigid percentages (like 100%). The total number of shares is simply the sum of all shares given out.*  
     > *If a beneficiary cannot receive their share (for example, if they have died and have no children to inherit under per stirpes), their shares simply **do not exist**. The total share count shrinks automatically, and the remaining beneficiaries divide the estate in proportion to their own shares without leaving any undisposed leftover money."*
   - Illustrate with a concrete example (e.g., 3 shares to Alice, 2 to Bob, 1 to Charlie = 6 shares. If Charlie is ineligible, total becomes 5 shares: 3/5 to Alice, 2/5 to Bob).

2. **The 90-Day Survivorship Rule:**
   - The preamble must clearly explain why and how the 90-day survival rule operates:
     > *"Survivorship Requirement (90 Days):*  
     > *To inherit under this will, a beneficiary must survive you by at least 90 days. It does not matter whether a person passed away before or after you wrote this will—if they do not live at least 90 days after your death, they are treated as having predeceased you.*  
     > *This prevents your estate from passing into a deceased beneficiary's estate, avoiding double probate fees and unwanted delays."*

3. **Per Stirpes vs. Per Capita Distinctions:**
   - The Advisory Preamble **must clearly explain the legal distinction and real-world implications** between *per stirpes* and *per capita* distribution:
     - **Educational Walkthrough:** Illustrate with an intuitive example:
       > *"Per Stirpes (Default): If your estate is divided equally between two children, and one child dies before you leaving two grandchildren, that deceased child's 50% share passes down to those two grandchildren (25% each).*  
       > *Per Capita (Optional Override): Under per capita, the deceased child's share does not go to the grandchildren; instead, the entire estate goes to your surviving child."*
     - **Explicit Confirmation of Defaults:** The preamble must state clearly that all residuary gifts in the attached will operate under *per stirpes* unless an explicit *per capita* tag was designated.

4. **Tax Obligations on Specific Financial Gifts & Inherited Property Disclosures:**
   - The Advisory Preamble must clearly educate the testator and beneficiaries regarding tax responsibilities on specific bequests:
     > *"Taxes on Specific Gifts of Financial Value:*  
     > *If you leave a specific gift of financial value (such as a cash legacy, securities, or appreciated property), any taxes triggered by that gift are paid by the beneficiary receiving it—not deducted from the residue meant for others.*  
     > *The beneficiary can satisfy these taxes by having them deducted from their share of the residue (if they are a residuary beneficiary), by selling a portion of the property, or by remitting funds directly to your estate.*  
     > *Inherited property is explicitly identified along with its original source(s) to maintain transparent provenance and family records."*

5. **Conditional Beneficiary Mechanics & Catastrophic Family Wipeout Protection:**
   - The Advisory Preamble must clearly explain how multi-level conditional alternates interact with *per stirpes* and how the catastrophic fallback functions:
     > *"Backup / Conditional Beneficiaries:*  
     > *You may name backup beneficiaries to any number of levels for any gift. However, if a gift is given 'per stirpes' (the default rule), your backup beneficiary will ONLY receive the gift if the primary beneficiary dies leaving NO living children or grandchildren. If the primary beneficiary leaves children, the gift passes directly down to those children instead.*  
     > *Ultimate Family Disaster / Wipeout Clause:*  
     > *If everyone you named in your entire will passes away without surviving descendants, your estate will not be lost to the government. Instead, your estate is split 50/50 between your family and your spouse's family. For each side, the law traces up to the closest ancestors who have living descendants and distributes that half to them per stirpes."*

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
  │       └── review-will-skill/
  │           └── SKILL.md
  ├── docs/
  │   ├── REQUIREMENTS.md
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
