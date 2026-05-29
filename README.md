# NGMEP Project

Mining engineering platform split into **frontend** and **backend** (like CAD + database server).

## Repositories / folders

| Folder | Role |
|--------|------|
| [`ngmep-platform/`](ngmep-platform/) | Web UI — visualization, modules, AI copilot |
| [`ngmep-backend/`](ngmep-backend/) | **API server** — ingest & retrieve org/project/dataset data |

Planning docs: `upgrade.md`, `implementation plan.md`, `next_gen_mining_system_architecture.md`

## Run both

**Terminal 1 — Backend (data in/out)**

```bash
cd ngmep-backend
npm install
npm run seed
npm run dev
```

→ http://localhost:8787

**Terminal 2 — Frontend**

```bash
cd ngmep-platform
npx --yes serve .
```

→ http://localhost:3000 (or port shown)

**Connect frontend to backend** (browser console or inject before load):

```javascript
localStorage.setItem("ngmep_api_url", "http://localhost:8787");
location.reload();
```

Top bar **API** badge turns green when linked.

## Data flow

```
User / field tools / scripts
        ↓ POST (ingest)     ↑ GET (retrieve)
              ngmep-backend API
        ↓ sync              ↑ save workspace
              ngmep-platform (browser)
```

See [`ngmep-backend/README.md`](ngmep-backend/README.md) for full API reference.
