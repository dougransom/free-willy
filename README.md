# Free-Willy 🐋📜

**Free-Willy** is an open-source, parameterized legal template and testamentary document generator for residents of all Canadian provinces and territories.

## Key Capabilities

- **All Canadian Jurisdictions:** Covers common law provinces and territories, as well as English-language wills under the *Civil Code of Québec* (wills before witnesses & notarial compatibility).
- **Comprehensive Document Suite:** Generates:
  1. *Last Will and Testament* (kept pristine for probate; no software disclaimers on the document itself).
  2. *Provincial Affidavit of Execution / Attestation* (province-specific statutory court forms).
  3. *Signing and Witnessing Guide* (strict compliance rules for physical execution).
  4. *Advisory Preamble & Safeguards Report* (separate advisory sheet).
- **Dynamic Priority Appointments:** Prioritized lists for executors and guardians ("first person willing and legally able to act", including dynamic class expressions like descendants by decreasing age).
- **Multiple Wills / Secondary Wills:** Supports dual will strategies (non-probate wills for private corporation / CCPC shares, shareholder loans, and out-of-province assets to minimize probate fees).
- **Foreign Will Protection:** Selective revocation clauses that explicitly preserve validly executed wills in other jurisdictions.
- **Strict Separation of Legal Disclaimers:** Safeguards and statutory warnings are kept on a separate companion sheet, never printed on the will itself.
- **Dedicated AI Agent Skill:** Includes an interactive agent skill (`.agents/skills/will-preparation/SKILL.md`) guiding AI assistants through conversational intake, provincial validation, and document assembly.
- **French Templates for Bilingual & Civil Jurisdictions:** Source-of-truth French templates for jurisdictions accepting French wills without translation (Quebec, New Brunswick, Ontario, Manitoba, and territories), with a dedicated translation skill (`.agents/skills/translate-canonical-template-to-french/SKILL.md`).

## Project Documentation

Detailed system requirements and legal specifications are documented in [docs/REQUIREMENTS.md](docs/REQUIREMENTS.md).

## License

Super permissive (MIT License with strict "AS IS" disclaimer). Use entirely at your own risk.
