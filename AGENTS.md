## Repo Identity

- Name: `mcp-python-sdk`
- Type: `repo`
- Absolute path: `/Users/oskar/repo/mcp-python-sdk`
- Role: Ennui-owned maintenance fork of the MCP Python SDK for pinned Streamable HTTP lifecycle fixes used by Google Workspace MCP
- Global reference: `/Users/oskar/.agents/AGENTS.md`

## Inheritance From Global AGENTS

- Global rules in `/Users/oskar/.agents/AGENTS.md` apply by default.
- This file adds only fork-specific maintenance and verification rules.
- If repo identity, role, path, or workspace mapping changes durably, update both this file and `/Users/oskar/.agents/.aimemory/repos.toml` in the same task.

## Repo-local Rules

- Keep `upstream` pointed at `modelcontextprotocol/python-sdk` and `origin` pointed at `ennuiweb/python-sdk`.
- Production fixes belong on a version-named maintenance branch and must remain narrowly scoped and pinned by commit from downstream deployments.
- Preserve upstream tests and add a regression test for every local transport change.
- Never add credentials, deployment secrets, or Oskar-specific runtime configuration to this SDK fork.
- `CLAUDE.md` is upstream's development guide and stays upstream-owned; follow it (uv only, never pip; `uv run --frozen pytest`, `uv run --frozen ruff check .`, `uv run --frozen pyright`). Some test modules need optional extras such as `websockets`.
- Check the current maintenance branch (`git branch --show-current`, e.g. `oskar/session-cleanup-v1.28.1`) before committing; never commit fork fixes to `main`.

## Local Context Map

- `src/mcp/server/streamable_http.py` — Streamable HTTP transport lifecycle
- `src/mcp/server/streamable_http_manager.py` — stateful session allocation and idle reaping
- `tests/server/` — transport and session-manager regression tests
- `.aimemory/memory.md` — fork purpose, pinning, and upstream status
- `CLAUDE.md` — upstream development guidelines (tooling, code quality, testing)
- Downstream consumer: `/Users/oskar/repo/google-workspace-mcp` pins this fork by commit

## Self-maintenance Rules

- Update `.aimemory/memory.md` when the pinned base version, local fix set, or upstream merge status changes.
- If this fork is retired after upstream releases equivalent fixes, remove its `repos.toml` entry in the same task.
- After changing this curated repo's `AGENTS.md`, run `oskar-agents-lint` through the Bridge project (`/Users/oskar/repo/oskar-memory-bridge`).
