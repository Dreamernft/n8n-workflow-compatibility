# n8n Workflow Compatibility — free examples by SwitchGraph

Spot sample-based API payload compatibility risks before deploying an n8n workflow change. This independent project provides synthetic fixtures, a practical checklist, and links to free browser tools. No sign-up required to use the free tools.

## Start here (free)

1. Open the [workflow dependency analyzer](https://switchgraph-evolution.bilge-topal.workers.dev/).
2. Select **Try example**, or download `examples/workflow.json` and load it into the analyzer.
3. Select source **Orders** and compare `examples/before.json` with `examples/after.json`.
4. Expect 4 references, 3 sample risks, 2 affected consumers. See the [example report](examples/expected-report.json).
5. Use the [free manifest builder](https://switchgraph-evolution.bilge-topal.workers.dev/manifest) to prepare multiple test cases.

| Consumer | Field | Example result |
| --- | --- | --- |
| Invoice | `/customer/name` | Missing in candidate sample |
| Invoice | `/total` | Number changed to string |
| Alert | `/total` | Number changed to string |
| Warehouse | `/id` | Unchanged in samples |

## Learn and integrate

- [API change checklist](https://switchgraph-evolution.bilge-topal.workers.dev/launch.html)
- [Analyzer guide](https://switchgraph-evolution.bilge-topal.workers.dev/guide.html)
- [Private CI integration example](CI_GUIDE.md)

## Need batch checks in CI?

[DriftGuard Batch](https://switchgraph-evolution.bilge-topal.workers.dev/batch) is a separate paid local CLI for up to 30 sample comparison cases per run, with structured JSON reports and CI exit codes. One-time price: $49. The paid CLI is not included in this repository. Node.js 20+ required for the CLI.

## Limitations and privacy

Static sample comparison is not a runtime safety guarantee. Dynamic expressions, code nodes, item linking and branches may be unresolved. Use synthetic or sanitized data. Never publish real workflow credentials, API keys or customer payloads. The browser analyzer processes workflow and sample contents locally. See its [privacy notice](https://switchgraph-evolution.bilge-topal.workers.dev/privacy.html).

SwitchGraph is independent and not affiliated with n8n. This repository is a public example collection, not the paid product or a community node. No open-source license has been granted; separate example usage terms are pending owner approval.
