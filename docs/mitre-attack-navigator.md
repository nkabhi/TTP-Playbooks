# Using MITRE ATT&CK Navigator with This Repo

The [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) is the standard tool for visualizing technique coverage as a heat-mapped matrix. This repo's [`mitre-mapping-template.md`](../templates/mitre-mapping-template.md) is designed to convert directly into a Navigator "layer" JSON file.

## Workflow

1. Fill out the coverage table in a domain's `mitre-mapping-template.md` copy.
2. Convert each row into a `techniques` entry:
   - `techniqueID`: the MITRE ID (e.g. `T1558.003`)
   - `score`: 0 (no coverage) – 100 (fully detected & tested) — used for the color gradient
   - `comment`: short note on current detection state
3. Paste the resulting JSON into [Navigator's "Open Existing Layer" → "Upload from local"](https://mitre-attack.github.io/attack-navigator/).
4. Export a screenshot or SVG from Navigator and drop it into the domain folder if you want a static visual alongside the live table.

## Minimal Layer Template

```json
{
  "name": "Domain Coverage Layer",
  "versions": { "attack": "15", "navigator": "4.9.1", "layer": "4.5" },
  "domain": "enterprise-attack",
  "description": "Auto-generated from ttp-playbook coverage table",
  "techniques": [],
  "gradient": {
    "colors": ["#ff6666", "#ffe766", "#8ccc66"],
    "minValue": 0,
    "maxValue": 100
  },
  "legendItems": [
    { "label": "No Coverage", "color": "#ff6666" },
    { "label": "Partial Coverage", "color": "#ffe766" },
    { "label": "Full Coverage", "color": "#8ccc66" }
  ]
}
```

## Automating the Conversion (Optional)

If the repo grows large, a small script can scan all `mitre-mapping-template.md`-derived files for their tables and emit a merged Navigator layer. This is intentionally left as a `TODO` for a future `scripts/` folder — keeping the base repo dependency-free for now.
