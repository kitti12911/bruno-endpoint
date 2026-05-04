# bruno-endpoint

Bruno endpoint collection for homelab API checks and manual request testing.

This repository is intended to hold Bruno collections for homelab services.
Keep request definitions, environments, and examples here so API checks can be
shared without depending on local-only client state.

## usage

Open this repository with [Bruno](https://www.usebruno.com/) and add or import
collections for the services you want to test.

## requirements

- [Bruno](https://www.usebruno.com/) for opening and running the collections

Optional:

- [prettier](https://prettier.io/) for Markdown, YAML, JSON, and JSONC formatting

Current collection:

```bash
SandBox API/
├── environments/
│   └── UserServiceEnv.yml
├── User Service gRPC/
│   ├── Health Check.yml
│   ├── Get User.yml
│   ├── List Users.yml
│   ├── Create User.yml
│   ├── Update User.yml
│   ├── Patch User.yml
│   └── Delete User.yml
└── opencollection.yml
```

Recommended collection layout for new services:

```bash
<service-name>/
├── bruno.json
├── collection.bru
└── environments/
    ├── local.bru
    └── dev.bru
```

## environments

Use Bruno environments for service-specific values instead of hardcoding them in
requests. Common variables should stay consistent across collections:

| variable  | description                                          |
| --------- | ---------------------------------------------------- |
| `baseUrl` | base URL or gRPC endpoint for the target service     |
| `token`   | bearer token for authenticated requests, when needed |

Do not commit real secrets, long-lived tokens, or machine-specific values. Use
local Bruno secrets for sensitive values.

## maintenance notes

- Keep collection folders grouped by service or API domain.
- Prefer reusable environment variables for hosts, tokens, IDs, and common request inputs.
- Keep request names short and action-oriented, for example `get health`, `create item`, or `search users`.
- Commit only shared examples and safe defaults.

The current gRPC requests target
[`grpc-sandbox`](https://github.com/kitti12911/grpc-sandbox).

## available commands

```bash
make fmt
make pretty
make format
```
