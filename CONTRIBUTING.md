# Contributing to TTP Playbook

Thanks for helping grow this knowledge base. A few ground rules keep it useful and safe.

## Content Rules

- ✅ Defensive/educational intent only — every TTP entry must include detection guidance.
- ✅ Lab environments only. Never include real production hostnames, IPs, credentials, customer data, or screenshots containing sensitive info.
- ✅ Map every technique to a MITRE ATT&CK ID.
- ✅ Use the provided templates — consistency is what makes this repo scalable.
- ❌ No fully weaponized exploit code. Reference public tools/PoCs by name and link instead of pasting working exploit payloads.

## Adding a New TTP

1. `cp templates/attack-detection-template.md domains/<domain>/ttps/<technique-name>.md`
2. Fill in every section.
3. Add the entry to the ATT&CK coverage table in `domains/<domain>/README.md`.
4. Add a Mermaid diagram if the attack has a multi-step flow (see `diagrams/mermaid-diagram-guide.md`).

## Adding a New Lab

1. `cp templates/lab-setup-template.md domains/<domain>/labs/<lab-name>.md`
2. Include a Mermaid architecture diagram.
3. List teardown steps — labs must be fully reversible.

## Adding Lessons Learned

1. `cp templates/lessons-learned-template.md domains/dfir/<incident-name>.md`
2. Redact all sensitive identifiers before committing.

## Style

- One technique/lab/incident per file.
- File names: `kebab-case.md`.
- Headings: sentence case.
- Prefer tables over long prose for structured data (data sources, detections, IOCs).
- Diagrams: Mermaid only, so they render natively on GitHub — no external image dependencies for diagrams.

## Pull Requests

- PR title format: `[domain] Add: <short description>`
- Link the ATT&CK technique ID in the PR description.
- One logical unit of content per PR.
