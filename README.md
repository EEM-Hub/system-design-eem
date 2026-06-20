---
schema_version: "1.0"
type: eem
project_name: "system-design-eem"
domain: ["System Design"]
license: cc-by-sa-4.0
base_network: null
source_repos: []
beliefs_total: 1296
beliefs_in: 1213
beliefs_out: 83
premises: 1000
derived: 296
nogoods: 0
generator: ftl-reasons/0.48.0
---

# System Design EEM

## Stats

| Metric | Value |
|--------|-------|
| Total beliefs | 1296 |
| Status | 1213 IN / 83 OUT |
| Premises (observations) | 1000 |
| Derived (justified conclusions) | 296 |
| Nogoods (contradictions) | 0 |
| Retraction rate | 6% |
| Max derivation depth | 14 |

## How to Use

### Import into a reasons database

```bash
reasons init
reasons import-json network.json
```

### Query beliefs

```bash
reasons search "your query"
reasons explain <node-id>
reasons show <node-id>
```

## Files

| File | Description |
|------|-------------|
| `network.json` | Full belief network (machine-readable, portable) |
| `reasons.db` | SQLite database (gitignored, regenerate with `reasons import-json network.json`) |
| `README.md` | This EEM card |

## Quality

- 1213 beliefs IN, 83 OUT
- 1000 premises grounded in direct observations
- 296 derived beliefs justified via SL justifications
- 0 nogoods detected

## Limitations

- Auto-generated card — review and customize for your use case

## License

Sources and entries are derived from Wikipedia articles and licensed under
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
See [LICENSE](LICENSE) and [ATTRIBUTION.md](ATTRIBUTION.md) for details.
