# Zineps for Cursor

Connect Cursor to the hosted [Zineps MCP server](https://mcp.zineps.com/docs/login) for shipments, labels, orders, invoices, and partner operations. You need a Zineps account with organisation access.

## Install

[Add Zineps to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=zineps&config=eyJ1cmwiOiJodHRwczovL21jcC56aW5lcHMuY29tL21jcCJ9)

Open the link on a computer with Cursor installed, review the endpoint, and confirm installation. The link contains only the public endpoint configuration.

Alternatively, merge this configuration into `~/.cursor/mcp.json` for your user, or `.cursor/mcp.json` for one project. Preserve any existing servers:

```json
{
  "mcpServers": {
    "zineps": {
      "url": "https://mcp.zineps.com/mcp"
    }
  }
}
```

## Authorize and verify

1. Open Cursor Settings and find Zineps under Tools & Integrations / MCP, or Customize in newer versions.
2. Select the sign-in/connect action. Confirm the authorization page is on `mcp.zineps.com`.
3. Sign in to Zineps, choose the session duration and permitted tools, then approve. Start with read-only access and only the tools you need.
4. Ask Cursor to call `GetMyInfo` to verify your authenticated scope, then `GetToolGuide` for supported workflows. Do not publish the returned account details.

Available tools depend on your role, organisation, access mode, and granted permissions. Creating or remaking labels can incur carrier charges. Review each proposed action before allowing it.

## Disconnect

Disable or remove Zineps from Cursor's MCP settings. This stops Cursor using the connection; do not assume removing local configuration revokes an already issued token. Use a short authorization session when testing.

## Troubleshooting

- Opening `/mcp` in a normal browser returns HTTP 401 without a token. This is expected; connect through Cursor and authorize.
- Use the complete URL `https://mcp.zineps.com/mcp` and a Cursor version supporting Streamable HTTP and OAuth.
- If sign-in fails or expires, reconnect and authorize again. An organisation policy may restrict custom MCP servers or plugins.
- An unavailable tool may be excluded by your role or consent. Do not broaden permissions just to make a test pass.

## Data handling

Zineps processes tool inputs and results needed for your request. The connector does not require your full conversation or question recording for product improvement. Relevant operational logs and investigation records may be retained. Your selected AI provider also processes inputs and results under its own policies. See the [Zineps connector privacy policy](https://mcp.zineps.com/privacy) for data uses, recipients, retention and privacy controls. Never put passwords or tokens in chat or configuration committed to Git.

## Package contents and validation

This repository contains the Cursor manifest, public MCP configuration, and Zineps branding. It does not contain the server implementation or credentials. The hosted service retains its own access requirements.

Configuration and deeplink can be checked statically. Actual Cursor installation, OAuth authorization, and a `GetMyInfo` call must be verified separately before claiming end-to-end compatibility.

Maintained by [Zineps](https://www.zineps.com). Contact: bhanu@zineps.com.
