# mcp-python-sdk memory

- Purpose: narrow Ennui-owned maintenance fork used to pin Streamable HTTP session cleanup fixes required by the hosted Google Workspace MCP deployment.
- Base: MCP Python SDK `v1.28.1`; production work lives on `oskar/session-cleanup-v1.28.1`.
- Local fix set: reject invalid pre-session methods before allocation, clean request/SSE streams when a response ends early, and retain explicit idle reaping in downstream FastMCP construction.
- Upstream tracking: retire local patches only after equivalent upstream fixes are released and the Workspace soak suite passes against that release.
