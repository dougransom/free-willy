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
- **Multiple / Dual Wills Architecture:** Supports multiple will strategies to minimize probate taxes on private CCPC shares, shareholder loans, and nominee assets, respecting provincial frameworks: **Primary / Secondary Wills** in Ontario (shared executors permitted under *Granovsky*) and **Probate / Non-Probate Wills** in British Columbia (with mandatory distinct executor guardrails under *Berkner Estate*).
- **Foreign Will Protection:** Selective revocation clauses that explicitly preserve validly executed wills in other jurisdictions.
- **Strict Separation of Legal Disclaimers:** Safeguards and statutory warnings are kept on a separate companion sheet, never printed on the will itself.
- **Dedicated AI Agent Skill:** Includes an interactive agent skill (`.agents/skills/will-preparation/SKILL.md`) guiding AI assistants through conversational intake, provincial validation, and document assembly.
- **French Templates for Bilingual & Civil Jurisdictions:** Source-of-truth French templates for jurisdictions accepting French wills without translation (Quebec, New Brunswick, Ontario, Manitoba, and territories), with a dedicated translation skill (`.agents/skills/translate-canonical-template-to-french/SKILL.md`).

## Project Documentation

- **System Requirements Specification:** Detailed system architecture, data models, and legal requirements are documented in [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md).
- **Testamentary Use Case Catalog:** Real-world scenarios, family structures, and asset allocation models are cataloged in [`docs/USE_CASES.md`](docs/USE_CASES.md).
- **Default Charitable Beneficiary Guide:** Bequest guidelines and registry information for the Cancer Research Society are documented in [`docs/DEFAULT_CHARITY_BENEFICIARY.md`](docs/DEFAULT_CHARITY_BENEFICIARY.md).

## Agent-Driven Specification Workflow

Requirements and use cases in Free-Willy are designed to be edited and evolved by an AI agent using the specialized skills in `.agents/skills/`:

1. **Add a Use Case (`/add-use-case <text>`):**
   - When you have a testamentary scenario, family dynamic, or asset structure you would like supported, invoke the **[`add-use-case`](.agents/skills/add-use-case/SKILL.md)** skill.
   - The agent will **grill you** through an interactive interview to probe for boundary conditions, takers on failure, carrying cost allocations, dispute mechanisms, and provincial tax/legal traps.
   - The elicited, challenge-resistant scenario is then cataloged directly into [`docs/USE_CASES.md`](docs/USE_CASES.md).

2. **Update Requirements from Use Cases (`/update-requirements-from-use-cases`):**
   - After use cases are added or refined, invoke the **[`update-requirements-from-use-cases`](.agents/skills/update-requirements-from-use-cases/SKILL.md)** skill.
   - The agent detects git deltas and unprocessed use cases, translates them into normative requirements, data schemas, and validation checks, and updates [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) with bidirectional traceability.

3. **Audit Requirements (`/review-requirements`):**
   - Verify that requirements remain legally watertight across all 10 provinces and 3 territories using the **[`review-requirements`](.agents/skills/review-requirements/SKILL.md)** skill, auditing against the 7 Pillars of Challenge-Resistant Testamentary Design.

## Contributing & Feature Requests

- **Requesting a Use Case or Feature:** If you have a testamentary use case, estate scenario, or feature to request, please submit an issue on GitHub with an explanation of the scenario and its intended practical outcome.
- **Submitting Pull Requests:** Contributions are welcome via Pull Request if you can follow the agent-driven workflow described above (using `/add-use-case`, `/update-requirements-from-use-cases`, and `/review-requirements`) to ensure all additions are legally vetted, battle-tested against provincial invariants, and bidirectionally traced across [`docs/USE_CASES.md`](docs/USE_CASES.md) and [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md).

## TODO / Roadmap

- [ ] **Updating Templates from Updated Requirements:** Synchronize the modular clause library (`templates/clauses/`), clause manifests (`templates/manifest.yaml`), and assembly engines with the latest normative specifications in [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) (e.g., residential life interests, personal property memoranda, hotchpot accounting, asset purchase options, encumbered real estate, and funeral directives).
- [ ] **French Template Synchronization:** Synchronize and translate newly added canonical clauses into French (`templates/clauses_fr/`) using the **[`translate-canonical-template-to-french`](.agents/skills/translate-canonical-template-to-french/SKILL.md)** skill.
- [ ] **Declarative Linter & Compiler:** Build automated validation tooling to verify testator YAML configurations against statutory rules and clause dependencies.

## License

Super permissive (MIT License with strict "AS IS" disclaimer). Use entirely at your own risk.
