# reporting-source-ct-native

A commercetools Connect data-source connector for the reporting framework.

Split out of the reporting framework monorepo with `scripts/split-connector.mjs`.
The framework contracts under `*/src/shared` are vendored: re-run the split to update
them rather than editing them here, or they will drift from the framework.

## Deploy

```bash
git init && git add -A && git commit -m "initial" && git tag v0.1.0
# then, with the Connect CLI:
commercetools connect connectorstaged create --repo <url> --tag v0.1.0
commercetools connect connectorstaged publish
commercetools connect deployment create --connector <key> --region <region>
```

After deploying, its `postDeploy` publishes a capability descriptor to Custom Object
`reporting.datasources/<SOURCE_ID>`, and the reporting gateway picks it up within a
minute. No framework redeploy is needed.
