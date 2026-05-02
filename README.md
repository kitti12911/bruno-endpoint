# bruno-endpoint

Bruno endpoint collection for homelab API checks and manual request testing.

This repository is intended to hold Bruno collections for homelab services. Keep request definitions, environments, and examples here so API checks can be shared without depending on local-only client state.

## usage

Open this repository with [Bruno](https://www.usebruno.com/) and add or import collections for the services you want to test.

Recommended collection layout:

```text
<service-name>/
  bruno.json
  collection.bru
  environments/
    local.bru
    dev.bru
```

## environments

Use Bruno environments for service-specific values instead of hardcoding them in requests. Common variables should stay consistent across collections:

| variable  | description                                          |
| --------- | ---------------------------------------------------- |
| `baseUrl` | base URL for the target service                      |
| `token`   | bearer token for authenticated requests, when needed |

Do not commit real secrets, long-lived tokens, or machine-specific values. Use local Bruno secrets for sensitive values.

## maintenance notes

- Keep collection folders grouped by service or API domain.
- Prefer reusable environment variables for hosts, tokens, IDs, and common request inputs.
- Keep request names short and action-oriented, for example `get health`, `create item`, or `search users`.
- Commit only shared examples and safe defaults.
