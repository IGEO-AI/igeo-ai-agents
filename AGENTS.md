# Contributor and agent guidance

This bundle helps agents research public igeo.ai information. Keep its scope limited to public documentation, configuration examples, and the `igeo-public-docs` skill.

- Use **igeo.ai** in prose and metadata. Preserve fixed technical identifiers such as the skill directory name.
- Treat linked documentation as first-party source material. Preserve product limitations, dates, and the difference between public documentation and authenticated workspace access.
- Match tool names and input fields to the deployed server's `tools/list` response. Keep the portable Agent Plugins configuration separate from client-native examples.
- Keep examples credential-free. Do not include account IDs, private source code, environment files, session data, customer information, or logs from authenticated requests.
- Do not install clients, alter a user's existing configuration, register accounts, or publish this bundle merely to research a public question.
- If MCP is unavailable, use the public documentation or report the connection error; do not invent a successful tool result.

For changes, validate the skill's frontmatter and instructions, parse each JSON file, and validate root `plugin.json` and `mcp.json` against their declared Agent Plugins v1 schemas. Verify links and run an anonymous initialization, tool discovery, and representative read against the deployed endpoint before describing a release as tested.

Review the exact release files before publication. Confirm the publisher's licensing and distribution choices separately; no license grant is declared by this bundle.
