---
name: translate-canonical-template-to-french
description: Translates canonical English Markdown/YAML templates and clauses into French for Canadian jurisdictions that accept French wills without translation (Quebec, New Brunswick, Ontario, Manitoba, and bilingual territories), ensuring Canadian legal French accuracy and structural parity.
---

# Translate Canonical Template to French (`translate-canonical-template-to-french`)

Use this skill when translating or synchronizing English canonical source-of-truth templates (`templates/clauses/`) into French (`templates/clauses_fr/`) for use in Canadian jurisdictions that accept French-language testamentary instruments directly for probate.

---

## 1. Target Jurisdictions & Legal Systems

This skill targets Canadian provinces and territories that accept French-language wills without requiring a certified English translation for probate:

1. **Quebec (Civil Law — *Code civil du Québec*, CCQ):**
   - French is the official language.
   - Applies to Wills Made in the Presence of Witnesses (*testament devant témoins*, Arts. 712–715 CCQ) and Notarial Wills (*testament notarié*, Art. 717 CCQ).
2. **New Brunswick (Bilingual Common Law):**
   - Canada's constitutionally bilingual province (Constitution Act, 1982 s. 16(2); *Loi sur les langues officielles*).
   - French wills are probated directly in the Court of King's Bench (Probate Division).
3. **Ontario (Common Law):**
   - Under the *Courts of Justice Act* (s. 125, 126) and *French Language Services Act*, French wills and probate applications (Form 74D) are filed directly without translation.
4. **Manitoba (Common Law):**
   - Under s. 23 of the *Manitoba Act, 1870*, English and French are official court languages. French wills are probated directly.
5. **Territories (Northwest Territories & Nunavut):**
   - Official languages legislation provides statutory court recognition for French filings.

---

## 2. Structural Parity & Technical Invariants

When translating any canonical template, you must preserve exact technical parity:

1. **YAML Frontmatter Integrity:**
   - Keep all schema keys intact (`id`, `category`, `jurisdictions`, `scope`, `required_inputs`, `conflicts_with`, `requires`).
   - Translate human-readable descriptive values (`title`, `purpose`, `legal_notes`) into precise Canadian legal French.
   - Example:
     ```yaml
     id: "residue_per_stirpes_dynamic_v1"
     title: "Distribution du reliquat de la succession en parts dynamiques (par souche)"
     purpose: "Divise le reliquat en parts dynamiques avec extinction automatique des parts non attribuables"
     category: "disposition"
     jurisdictions: ["ALL"]
     scope: ["general", "secondary_corporate"]
     ```

2. **Semantic Block Markers:**
   - Retain exact comment delimiters:
     `<!-- clause: id -->` ... `<!-- endclause -->`

3. **Template Variables & Interpolations:**
   - Do NOT translate variable keys (e.g., keep `{{ person }}`, `{{ recipient }}`, `{{ shares }}`, `{{ currency }}`).
   - Only translate the surrounding legal prose.

---

## 3. Canadian Juridical Terminology Guide (*Français Juridique Canadien*)

Canadian legal French strictly distinguishes between **Common Law French** and **Quebec Civil Law French**:

| English Legal Concept | Common Law French (ON, NB, MB, Terr.) | Quebec Civil Law (CCQ) |
| :--- | :--- | :--- |
| **Last Will and Testament** | *Dernier testament* / *Testament* | *Testament* |
| **Executor / Estate Trustee** | *Fiduciaire de la succession* / *Exécuteur testamentaire* | *Liquidateur* (ou *liquidatrice*) |
| **Guardian** | *Tuteur testamentaire* / *Gardien* | *Tuteur* / *Tutrice* |
| **Specific Bequest (Property)** | *Legs particulier de biens* | *Legs à titre particulier* |
| **Pecuniary Legacy (Money)** | *Legs d'une somme d'argent* | *Legs à titre particulier d'une somme d'argent* |
| **Residuary Estate / Residue** | *Reliquat de la succession* / *Résidu* | *Résidu* / *Legs universel* |
| **Residuary Beneficiary** | *Bénéficiaire du reliquat* | *Légataire universel(le)* |
| **Per Stirpes** | *Par souche* (par représentation) | *Par souche* (par représentation) |
| **Per Capita** | *Par tête* | *Par tête* |
| **Survivorship Period (90 Days)** | *Délai de survie (90 jours)* | *Condition de survie (90 jours)* |
| **Inherited Property** | *Biens reçus par voie de succession (hérités)* | *Biens reçus par succession (legs ou succession légale)* |
| **Tax on Financial Gift** | *Impôts payables par le bénéficiaire (par imputation sur le reliquat, vente partielle ou versement à la succession)* | *Dettes fiscales et impôts acquittés par le légataire à titre particulier* |
| **Affidavit of Execution** | *Affidavit de souscription* / *Affidavit d'exécution* | *(N/A pour testament notarié; déclaration sous serment d'un témoin instrumentaire pour testament devant témoins)* |

---

## 4. Translation Workflow (Step-by-Step)

### Step 1: Select Canonical Source Template
- Read the target English clause from `templates/clauses/<category>/<filename>.md` using `view_file`.

### Step 2: Establish Jurisdictional Context
- If the clause is universal (`jurisdictions: ["ALL"]`) or specific to common law (`ON`, `NB`, `MB`), apply Canadian Common Law French terminology.
- If the clause is specific to Quebec (`jurisdictions: ["QC"]`), apply strict *Code civil du Québec* terminology (e.g., *liquidateur*, *testament devant témoins*).

### Step 3: Translate Body & Frontmatter
- Translate all legal text maintaining formal Canadian statutory phrasing.
- Apply Canadian French typographic rules:
  - Non-breaking spaces (*espace insécable*) before high punctuation (`:`, `;`, `!`, `?`).
  - Canadian French date formats (e.g., *le 14 octobre 2026*).
  - Accurate accents (*é, è, ê, à, ç, î, ô, û, etc.*).

### Step 4: Write to Target Directory
- Save the translated file in `templates/clauses_fr/<category>/<filename>.md` using `write_to_file` or `replace_file_content`.
- **Never use `cat << 'EOF'` or bash heredocs.**

### Step 5: Verification
- Verify variable placeholders match the English source.
- Check that frontmatter IDs and semantic block tags match the manifest schema.
