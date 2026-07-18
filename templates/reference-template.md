<!--
TEMPLATE: Quick Reference / Cheatsheet
Copy into domains/<domain>/references/<topic-name>.md
For command references, tool cheatsheets, and quick-lookup material.
-->

# Reference: <Topic Name>

**Domain:** e.g. Active Directory
**Last Updated:** YYYY-MM-DD

## Overview

One paragraph on what this reference covers and when to reach for it.

## Quick Commands

| Purpose | Command | Notes |
|---|---|---|
| Enumerate X | `command --flag` | Requires Y access |
| Detect X | `query-language-here` | Run in SIEM |

```bash
# Example command block
tool-name --option value
```

## Key Ports / Protocols

| Port | Protocol | Purpose |
|---|---|---|
| 88/tcp | Kerberos | Authentication |

## Common Log Locations

| OS/Platform | Log | Path |
|---|---|---|
| Windows | Security | `%SystemRoot%\System32\winevt\Logs\Security.evtx` |
| Linux | Auth log | `/var/log/auth.log` |

## Related Techniques

- [Technique 1](../ttps/example-technique.md)
- [Technique 2](../ttps/example-technique-2.md)

## External Resources

- [Official docs](https://example.com)
- [Relevant tool repo](https://github.com/example/tool)
