# AGENTS.md

Guidance for AI agents working in this repository.

## Cursor Cloud specific instructions

This repo is a **skills library + npm CLI + React/Vite web catalog**, not a multi-service backend. There is no Docker, database, or docker-compose.

### Services

| Component | Purpose | How to run |
|-----------|---------|------------|
| **Web catalog** (`apps/web-app`) | Browse/search 1,329+ skills | `npm run app:dev` (port **5173**) |
| **CLI installer** (`tools/bin/install.js`) | Install skills to agent directories | `node tools/bin/install.js --help` |
| **Repo tooling** (Python + Node) | Validate skills, generate indexes | `npm run validate`, `npm test` |

Optional (not required locally): **Supabase** (skill star counts in the web UI), **GitHub API** (refresh-skills sync in dev).

### Standard commands

See root `package.json` and `CONTRIBUTING.md`. Common flows:

```bash
# Web catalog (copies skills assets, then starts Vite)
npm run app:dev

# Repo validation & tests (CI parity, no network by default)
npm run validate
npm run test:local

# Web app lint & unit tests
cd apps/web-app && npm run lint
cd apps/web-app && npm test -- --run

# Production-like web build
npm run app:build
```

### Gotchas

- **`npm run app:setup`** must run before dev/build; `app:dev` and `app:build` invoke it automatically. It copies `skills_index.json` and the `skills/` tree into `apps/web-app/public/`.
- Root **`npm test`** runs the repo test suite via `tools/scripts/tests/run-test-suite.js`. Web app tests are separate: `cd apps/web-app && npm test`.
- **`ENABLE_NETWORK_TESTS=1`** is required for network/GitHub integration tests; default local runs skip them.
- Python scripts expect **PyYAML** (`pip install -r tools/requirements.txt`); CI uses Python 3.10+.
- The Vite dev server exposes **`/api/refresh-skills`** (see `apps/web-app` refresh-skills plugin). Sync-from-upstream needs git/network; browsing the catalog does not.
- No root ESLint; lint lives under `apps/web-app` only.
