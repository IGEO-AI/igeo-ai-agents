# igeo.ai public agent integration

Use this bundle to answer questions about public igeo.ai products, pricing, and integration documentation with links to the underlying sources. It combines a focused research skill with the anonymous public documentation MCP endpoint. It contains configuration and instructions; no local server or executable dependency is required.

## Connect

MCP endpoint: `https://www.igeo.ai/api/docs-mcp/`

Transport: Streamable HTTP with JSON responses. The server supports MCP `2025-11-25`; let your client negotiate the protocol version and generate protocol headers. No API key, account, workspace ID, or authorization header is needed for this public server.

Choose the installation path your client supports:

- **Agent Plugins v1:** load this directory as a plugin. Root `plugin.json` supplies metadata; `mcp.json` declares the remote server; `skills/` contains the skill. Support depends on the client.
- **Existing MCP client:** add the HTTPS endpoint as a remote HTTP server. [examples/claude-code.mcp.json](examples/claude-code.mcp.json) uses Claude Code's `.mcp.json` format; [examples/vscode.mcp.json](examples/vscode.mcp.json) uses VS Code's `.vscode/mcp.json` format. Merge the server entry into existing configuration instead of replacing other servers.
- **Skill only:** install `skills/igeo-public-docs/` using your client's Agent Skills workflow. The skill also supports reading the published website when MCP is unavailable.

The portable root `mcp.json` and native client examples have different schemas. Use the file matching your client. Review the configuration through your client's normal connection/trust flow; this bundle does not change its approval settings.

## Verify a useful request

After connecting, ask:

> Use the igeo.ai public documentation tools to explain the difference between the public documentation server and the authenticated workspace MCP server. Cite the documentation you read.

A successful connection includes a real tool call and a result, not merely a plausible answer. Discover the current tools through `tools/list`. The initial tool set is:

| Tool | Use |
| --- | --- |
| `get_site_info` | Public product capabilities, audiences, and metric definitions |
| `get_pricing` | Published plans, billing terms, and social add-ons |
| `get_integration_docs` | Integration links and authentication requirements |
| `read_documentation` | Full `overview`, `mcp`, `auth`, or `api` developer guide |
| `search_documentation` | Relevant excerpts from developer guides and public summaries |

Example follow-up requests:

- “Explain monthly versus annual billing using current published pricing.”
- “Find the documented response when a cached REST result is still being built.”
- “Read the authentication guide and identify what an integration needs before requesting workspace data.”

Tool output is first-party information from igeo.ai. Cite its source URLs and retain any relevant scope or date. A product description is not independent proof of performance, security, or future availability.

## Boundaries and connection errors

This public server does not read customer analytics, connect a workspace, publish content, change records, subscribe to a plan, or execute arbitrary URLs. Search covers public developer guides and product, service, FAQ, and resource summaries; it does not search the entire blog or the internet.

The separate workspace MCP endpoint is `https://api.igeo.ai/mcp`. It requires an authorized connection and the permissions documented in the [authentication guide](https://www.igeo.ai/developers/auth/). This bundle includes no workspace credentials or automatic sign-in.

The public documentation transport is stateless, with no SSE listener, sessions, or task execution. A GET to the MCP transport URL returns HTTP 405; a compatible client uses POST. The [Server Card](https://www.igeo.ai/api/docs-mcp/server-card/) is a separate GET resource. Honor HTTP 429 and `Retry-After`. Browser connections are subject to the endpoint's Origin policy; use the public website if your browser client is not supported.

## Sources and formats

- [Public developer guides](https://www.igeo.ai/developers/)
- [Reference index](https://www.igeo.ai/llms.txt)
- [Server Card](https://www.igeo.ai/api/docs-mcp/server-card/)
- [Published pricing](https://www.igeo.ai/pricing/)
- [Agent Plugins v1 specification](https://agent-plugins.org/specification)
- [Agent Skills specification](https://agentskills.io/specification)
- [MCP 2025-11-25 transport](https://modelcontextprotocol.io/specification/2025-11-25/basic/transports)
- [Claude Code MCP configuration](https://code.claude.com/docs/en/mcp)
- [VS Code MCP configuration](https://code.visualstudio.com/docs/agents/reference/mcp-configuration)

For contributors, see [AGENTS.md](AGENTS.md). The server owns the runtime tools and documentation; check its current discovery and source pages when maintaining this bundle.
