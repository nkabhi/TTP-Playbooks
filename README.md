# TTP Playbook

> A scalable, community-friendly cybersecurity knowledge base for documenting **Tactics, Techniques & Procedures (TTPs)**, detection engineering content, incident lessons learned, and hands-on labs — mapped to [MITRE ATT&CK](https://attack.mitre.org/).

![Markdown](https://img.shields.io/badge/docs-markdown-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-active-brightgreen)

---

## 🎯 Purpose

This repository is a living knowledge base for security practitioners to:

- Document adversary **TTPs** in a consistent, reusable format
- Map every technique to **MITRE ATT&CK**
- Capture **detection logic** (Sigma / KQL / SPL / YARA) alongside the attack it detects
- Record **lab builds** used to safely reproduce attacks
- Preserve **lessons learned** from incidents and exercises
- Serve as a reference library for blue teams, threat hunters, and content creators

---

## 🗂️ Repository Structure

```
ttp-playbook/
├── README.md                  # You are here
├── CONTRIBUTING.md            # How to add content
├── LICENSE
├── templates/                 # Reusable Markdown templates
│   ├── attack-detection-template.md
│   ├── mitre-mapping-template.md
│   ├── lab-setup-template.md
│   ├── lessons-learned-template.md
│   └── reference-template.md
├── diagrams/                  # Standalone Mermaid diagram library
│   └── mermaid-diagram-guide.md
├── docs/
│   └── mitre-attack-navigator.md
└── domains/
    ├── active-directory/
    ├── azure/
    ├── aws/
    ├── windows/
    ├── linux/
    ├── network/
    ├── kubernetes/
    ├── ai-security/
    ├── web-security/
    ├── detection/
    ├── dfir/
    └── threat-hunting/
```

Each **domain** folder follows the same internal layout so the repo scales cleanly as content grows:

```
domains/<domain>/
├── README.md         # Domain overview, sub-topics, ATT&CK matrix coverage
├── ttps/              # One file per technique (attack-detection-template)
├── labs/              # One file per lab build (lab-setup-template)
└── references/        # Cheatsheets, tool notes (reference-template)
```

---

## 📚 Domains Covered

| Domain | Focus |
|---|---|
| [Active Directory](domains/active-directory/README.md) | Kerberoasting, DCSync, ACL abuse, lateral movement |
| [Azure](domains/azure/README.md) | Entra ID, Conditional Access abuse, Az CLI persistence |
| [AWS](domains/aws/README.md) | IAM privilege escalation, S3 exposure, Lambda persistence |
| [Windows](domains/windows/README.md) | Living-off-the-land, process injection, persistence |
| [Linux](domains/linux/README.md) | Cron/systemd persistence, privilege escalation, rootkits |
| [Network](domains/network/README.md) | C2 traffic patterns, protocol abuse, pivoting |
| [Kubernetes](domains/kubernetes/README.md) | RBAC abuse, pod escape, secrets exfiltration |
| [AI Security](domains/ai-security/README.md) | Prompt injection, model exfiltration, RAG poisoning |
| [Web Security](domains/web-security/README.md) | OWASP Top 10, auth bypass, SSRF |
| [Detection](domains/detection/README.md) | Sigma/KQL rule libraries, detection engineering notes |
| [DFIR](domains/dfir/README.md) | Forensic artifacts, triage playbooks, IR process |
| [Threat Hunting](domains/threat-hunting/README.md) | Hypothesis-driven hunts, hunt packages |

---

## 🧩 How to Use the Templates

1. Copy the relevant template from `templates/` into the correct domain subfolder.
2. Rename it to match the technique/lab/incident (e.g. `kerberoasting.md`).
3. Fill in every section — incomplete entries should be marked `TODO`.
4. Add a link to it from the domain's `README.md` index table.
5. Open a PR (see [CONTRIBUTING.md](CONTRIBUTING.md)).

---

## 🖼️ Diagrams

All diagrams use [Mermaid](https://mermaid.js.org/), which renders natively in GitHub Markdown. See [`diagrams/mermaid-diagram-guide.md`](diagrams/mermaid-diagram-guide.md) for copy-paste starter diagrams (attack chains, detection pipelines, kill chains, incident timelines).

---

## 🗺️ MITRE ATT&CK Mapping

Every TTP entry must include a completed [`mitre-mapping-template.md`](templates/mitre-mapping-template.md) block. See [`docs/mitre-attack-navigator.md`](docs/mitre-attack-navigator.md) for how to export your coverage into the official ATT&CK Navigator layer format.

---

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). All content should be defensive-purpose, clearly labeled for lab/simulated environments, and free of real production secrets, IPs, or customer data.

## 📄 License

[MIT](LICENSE) — content is provided for educational and defensive security purposes.
