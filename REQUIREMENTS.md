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
| **Advisory Preamble & Safeguard Summary** | Separate companion sheet providing legal notices, statutory maintenance warnings, and input validation results. | Packaged strictly **outside** the will itself (as a preceding cover sheet or separate document) to preserve legal sanctity. |

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
   - **No Fixed Share Total:** When dividing an estate or fund into shares, the total pool of shares is **strictly determined by the sum of shares gifted**, rather than being constrained to an arbitrary constant like 100 or 100%. (e.g., Alice: 3 shares, Bob: 2 shares, Charlie: 1 share = 6 total shares; Alice receives 3/6, Bob 2/6, Charlie 1/6).
   - **Extinguishment of Unallocatable Shares (Non-Existent Shares):** If any share cannot be legally allocated to a designated recipient (e.g., the beneficiary has predeceased the testator with no surviving issue under *per stirpes*, or has predeceased under a *per capita* gift, or is legally disqualified from taking), **those unallocatable shares cease to exist**.
   - **Automatic Denominator Contraction (Preventing Partial Intestacy):** The total number of shares automatically contracts to the sum of the remaining legally valid shares. (e.g., if Charlie above is deceased without substitute beneficiaries, Charlie's 1 share ceases to exist; the total contracts to 5 shares, with Alice receiving 3/5 and Bob 2/5). This completely eliminates undisposed fractional residues and prevents partial intestacy.
4. **Distribution Models:**
   - **Spousal Rollover with Gift-Over:** 100% to spouse/partner if surviving the survival period; gift-over to children or named beneficiaries (*per stirpes* by default).
   - **Custom Share Allocations:** Custom named beneficiaries assigned relative share units, governed by the dynamic denominator and non-existent share rules.
5. **Survivorship Condition & 90-Day Default Period:**
   - **Default Survival Period (90 Days):** Unless overridden in configuration, every beneficiary must survive the testator by a minimum of **90 days** to take any gift, share, or bequest.
   - **Unified Survival Rule (Pre- vs. Post-Execution Death Neutrality):** The same legal rules apply regardless of whether a beneficiary passed away *before* or *after* the will was made. The test is strictly binary: **a beneficiary either survives the testator by the full 90-day survival period, or they do not**.
   - **Consequence of Non-Survival:** Any beneficiary who does not survive the 90-day period is legally treated as having predeceased the testator. This triggers:
     - Under *per stirpes* (default): descent of their share down to their living issue/children.
     - Under *per capita* (or if leaving no issue): their shares cease to exist, and the total share denominator contracts accordingly.

### 4.5 Minor Testamentary Trusts & Guardian Appointments
1. **Staged Age of Distribution:**
   - Configurable distribution milestone ages (e.g., age 18/19, 21, 25, or fractional releases such as 50% at 21, balance at 25).
2. **Trustee Discretionary Powers:**
   - Discretionary powers to encroach on income and capital for maintenance, education, advancement, and medical care of minor beneficiaries.
3. **Guardian / Tutor Nomination:**
   - Parental appointment of testamentary guardian/custodian for minor children, subject to provincial court ratification.

### 4.6 Specific Bequests, Pets, and Digital Assets
1. **Pecuniary & Specific Legacies:**
   - Specific sums of money or identified personal property items bequeathed to named individuals or registered charities.
2. **Digital Assets Provision:**
   - Express executor powers to access, control, modify, archive, or delete digital accounts, email, cryptocurrencies, cloud storage, and domain names in compliance with modern service terms.
3. **Pet Care Provisions:**
   - Bequest of pets to designated caregivers, optionally accompanied by an honorary trust or cash fund for veterinary care and maintenance.

---

## 5. Declarative Data Input Specification

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
  primary:
    type: "spouse_then_children"
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

digital_assets:
  authorize_executor_access: true

pets:
  caregiver: "Jane Doe"
  cash_allocation: 2000.00
```


---

## 6. Character Encoding & Typographic Standards

### 6.1 Mandatory UTF-8 Standard
All system components—input files (YAML/JSON), template files, internal strings, and emitted output documents (Markdown, Plain Text, etc.)—**MUST use UTF-8 encoding**. Pure ASCII restrictions are explicitly prohibited.

### 6.2 Unicode Normalization (NFC)
- All string comparisons, name indexing, and text processing must adhere to **Unicode Normalization Form C (NFC)**.
- Prevents mismatched identifiers when names containing accents (e.g., composed `é` vs. combining character `e + ́`) are processed across different operating systems.

### 6.3 Linguistic & Typographic Requirements
- **Canadian Names & Addresses:** Full support for accented characters common in Canadian French, English, and Indigenous names and places (e.g., *François, Bérubé, Montréal, Île-du-Prince-Édouard*).
- **Legal Typography:** Native support for professional typographical characters:
  - Em-dashes (`—`), en-dashes (`–`), ellipses (`…`).
  - Typographic curved quotes (“ ” and ‘ ’).
  - Legal section markers and formatting glyphs (`§`, `¶`, `•`).
  - Currency symbols (`$`, `€`, `£`).

---

## 7. Output Formats & Architecture

1. **Phase 1 Baseline:**
   - **Markdown (`.md`):** Clean, standard GitHub-flavored Markdown formatted for easy diffing, manual customization, and inspection.
   - **Plain Text (`.txt`):** Monospace, indented, cleanly formatted text.
2. **Phase 2 Extensibility:**
   - Clean separation between the data model, domain logic, and renderer, ensuring future plug-and-play support for:
     - Formatted PDF (via Typst, Weasyprint, or LaTeX).
     - Editable Microsoft Word (`.docx`).
     - Printable HTML with print stylesheets (`@media print`).

---

## 8. Legal Safeguards, Validation & Advisory Rules

### 7.1 Built-in Validation Engine
Before generating documents, Free-Willy validates the input data against provincial legal rules:
1. **Witness Eligibility:**
   - Warns if any designated executor, beneficiary, or spouse of a beneficiary is listed in execution instructions.
2. **Age of Majority Checks:**
   - Validates testator minimum age requirements (18 in AB, SK, MB, ON, PEI, QC; 19 in BC, NB, NL, NS, YT, NT, NU), flagging exceptions (e.g., military service or married minors where permitted by statute).
3. **Dependant Support Obligations (Family Relief):**
   - Issues warnings where provincial statutes impose mandatory claims for spouses or dependent children (e.g., Ontario SLRA Part V, BC WESA Part 4) if the distribution omits a dependent.
4. **Quebec Formalities Notice:**
   - Notes that a will before witnesses will require probate upon death, whereas a notarial will does not.

### 7.2 Strict Preamble Separation Principle
- **Absolute Rule:** Any advisory note, validation warning, software metadata, or legal disclaimer generated by Free-Willy **MUST NEVER** be embedded into the body of the Last Will and Testament.
- All cautionary guidance and validation reports must output to a distinct **Advisory Preamble / Summary** or separate companion file.

---

## 9. Technical Stack & Implementation Guidelines

- **Decoupled Architecture:** As decided during design grilling, the core engine logic (data schemas, clause logic, priority resolver, and validation rules) is abstracted from the final technology implementation.
- **Repository Organization:**
  ```text
  free-willy/
  ├── docs/
  │   └── REQUIREMENTS.md
  ├── README.md
  ├── LICENSE
  ├── schema/
  │   └── testator_input_schema.json
  ├── templates/
  │   ├── common/
  │   ├── provinces/
  │   │   ├── on/
  │   │   ├── bc/
  │   │   ├── ab/
  │   │   ├── qc/
  │   │   └── ...
  │   └── affidavits/
  └── examples/
      ├── ontario_general_will.yaml
      ├── ontario_secondary_corporate_will.yaml
      ├── bc_family_will.yaml
      └── quebec_witnessed_will.yaml
  ```

---

## 10. Licensing & Disclaimer

- **License:** Super permissive (MIT or 0BSD) to encourage unrestricted personal, commercial, or developer adaptation.
- **Liability Disclaimer:** Prominent "AS IS" disclaimer stating:
  > *Free-Willy provides automated self-help legal templates and document generation tools. It is NOT a law firm and does NOT provide legal advice. Estate laws differ by jurisdiction and individual circumstances vary significantly. Use entirely at your own risk. Consultation with a qualified estate planning lawyer or notary in your jurisdiction is strongly recommended.*
