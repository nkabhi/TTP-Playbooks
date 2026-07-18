# Mermaid Diagram Guide

Copy-paste starter diagrams for TTP docs, labs, and incident reports. All of these render natively in GitHub Markdown — no plugins required.

## 1. Attack Chain (Flowchart)

```mermaid
flowchart LR
    A[Reconnaissance] --> B[Initial Access]
    B --> C[Execution]
    C --> D[Persistence]
    D --> E[Privilege Escalation]
    E --> F[Lateral Movement]
    F --> G[Collection]
    G --> H[Exfiltration]
    style H fill:#ff6666,color:#fff
```

## 2. Kill Chain with Detection Points

```mermaid
flowchart LR
    A[Initial Access] -->|Detection: Email Gateway| B[Execution]
    B -->|Detection: EDR| C[Persistence]
    C -->|Detection: Sysmon Event 13| D[C2 Communication]
    D -.->|🔴 No Detection| E[Data Exfiltration]
    classDef detected fill:#8ccc66,color:#000
    classDef gap fill:#ff6666,color:#fff
    class A,B,C,D detected
    class E gap
```

## 3. Sequence Diagram (Auth / Protocol Abuse)

```mermaid
sequenceDiagram
    participant Attacker
    participant DC as Domain Controller
    participant SIEM

    Attacker->>DC: TGS-REQ (Kerberoast target SPN)
    DC-->>Attacker: TGS with RC4 ticket
    Attacker->>Attacker: Offline crack (hashcat)
    DC->>SIEM: Event 4769 logged
    SIEM-->>SIEM: Sigma rule evaluates encryption type
    SIEM->>SIEM: Alert fired (if RC4 + high volume)
```

## 4. Network / Infrastructure Diagram

```mermaid
graph TD
    subgraph Internet
        A[Attacker C2]
    end
    subgraph Corp Network
        B[Perimeter Firewall]
        C[Compromised Workstation]
        D[Domain Controller]
        E[File Server]
    end
    subgraph Monitoring
        F[SIEM]
    end
    A -->|HTTPS Beacon| B
    B --> C
    C -->|445/SMB| E
    C -->|88/Kerberos| D
    C -->|Logs| F
    D -->|Logs| F
```

## 5. Cloud IAM Privilege Escalation Path (AWS/Azure)

```mermaid
flowchart TD
    A[Low-Priv IAM User] -->|iam:PassRole| B[Assume Higher-Priv Role]
    B -->|lambda:CreateFunction| C[Deploy Lambda with Admin Role]
    C -->|Invoke| D[Full Account Compromise]
    style D fill:#ff6666,color:#fff
```

## 6. Kubernetes Attack Path

```mermaid
flowchart LR
    A[Compromised Pod] -->|Mounted Service Account Token| B[K8s API Access]
    B -->|RBAC Misconfig| C[List Secrets]
    C -->|Extract Cloud Creds| D[Cloud Account Pivot]
    B -->|Privileged Pod| E[Container Escape]
    E --> F[Node Compromise]
```

## 7. Incident Timeline

```mermaid
timeline
    title Example Incident Timeline
    09:00 : Phishing email delivered
    09:12 : User clicks malicious link
    09:15 : Payload executes : Beacon established
    11:40 : Lateral movement detected by EDR
    11:55 : SOC begins triage
    12:30 : Host isolated
```

## 8. ATT&CK Coverage (Pie Chart)

```mermaid
pie title Detection Coverage by Tactic
    "Detected" : 40
    "Partial" : 25
    "No Coverage" : 35
```

## 9. Decision Tree (Threat Hunting Triage)

```mermaid
flowchart TD
    A[Suspicious Process Spawned] --> B{Parent Process = Office App?}
    B -->|Yes| C{Network Connection Made?}
    B -->|No| D[Lower Priority — Log & Baseline]
    C -->|Yes| E[🔴 Escalate: Possible Macro Payload]
    C -->|No| F[🟡 Monitor]
```

## 10. State Diagram (Incident Lifecycle)

```mermaid
stateDiagram-v2
    [*] --> Detected
    Detected --> Triaged
    Triaged --> Contained
    Contained --> Eradicated
    Eradicated --> Recovered
    Recovered --> ClosedLessonsLearned
    ClosedLessonsLearned --> [*]
```

---

### Tips

- Keep diagrams under ~15 nodes for readability on GitHub's mobile renderer.
- Use `style` / `classDef` sparingly — red for gaps/critical paths, green for validated detections.
- Prefer `flowchart LR` for attack chains (reads left-to-right like a timeline) and `flowchart TD` for hierarchical/privilege structures.
