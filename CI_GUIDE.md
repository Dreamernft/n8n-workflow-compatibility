# Sample-based compatibility checks in private CI

Use the free analyzer and the synthetic files in `examples/` to understand the test case. For existing licensed DriftGuard Batch users, place the purchased CLI, its analyzer module and sanitized examples in a **private** repository. The following workflow is a reference snippet, not a runnable workflow in this public repository.

```yaml
name: Workflow sample compatibility
on: [pull_request]
permissions:
  contents: read
jobs:
  sample-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '22'
      - run: node driftguard.mjs examples/manifest.json
```

Exit 0: no observed sample risk or flagged limitation (not proof of runtime safety). Exit 1: invalid input or I/O. Exit 2: observed risk. Exit 3: inconclusive. The provided synthetic example intentionally exits 2 with the purchased CLI. Investigate every nonzero result. Do not commit or redistribute the licensed CLI in a public repository. CI hosting quotas may apply.

For your own workflows, collect authorized representative samples, change one source at a time, review coverage limitations and separately test the real workflow in a controlled environment.
