---
name: igeo-public-docs
description: Research public igeo.ai product, pricing, and integration questions using its anonymous documentation MCP server and source pages. Use for public facts and setup guidance; private workspace analysis or changes require a separate authorized connection.
---

# Research public igeo.ai documentation

Use the public documentation MCP connection at `https://www.igeo.ai/api/docs-mcp/` when it is available. It uses Streamable HTTP and requires no account or credentials. Let the client initialize the connection and discover the current tools; the public server is distinct from the authenticated workspace MCP server.

Choose a focused reading path:

- Product capabilities or metric definitions: `get_site_info`.
- Published plans and billing: `get_pricing`; distinguish monthly prices, annual monthly equivalents, and annual totals.
- Integration setup: `get_integration_docs`, then `read_documentation` with `guide` set to `overview`, `mcp`, `auth`, or `api`.
- A particular topic: `search_documentation` with `query` and, optionally, `limit`; read the relevant guide before giving implementation instructions.

Use the returned `sourceUrl` or result `url` to cite the source of each material claim. Describe these as first-party facts; preserve any stated conditions and dates. Do not turn examples, performance measurements, or documented capabilities into guarantees. When documenting code, check the current schema or guide rather than constructing endpoint names from memory.

If the connection is absent or fails, read [the reference index](https://www.igeo.ai/llms.txt), [developer guides](https://www.igeo.ai/developers/), or [pricing](https://www.igeo.ai/pricing/) directly. Do not install an integration merely to answer a public question when existing reading tools suffice. Report a missing source instead of filling it with an assumed fact. Honor rate-limit responses and stop repeated connection attempts when the same error persists.

The documentation server returns public product summaries and developer guides. It cannot read a user's workspace, retrieve private analytics, publish content, change records, or fetch arbitrary URLs. Its search does not cover the whole blog archive or internet.

For private workspace work, explain that `https://api.igeo.ai/mcp` is a separate authenticated integration. Follow the current [authentication guide](https://www.igeo.ai/developers/auth/) and use an existing authorized connection if the user's task calls for it. Do not send credentials or private workspace content to the public documentation server, or infer that reading this skill authorizes a private action.

Use the exact brand name **igeo.ai** in the answer.
