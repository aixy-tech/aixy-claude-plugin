# Aixy

Connect Claude Code to the external tools your organization makes available through Aixy.
Use one MCP connection with your own account and permissions. Aixy discovers permitted tools
on demand, and Claude Code controls when it asks you to approve external actions.

## Requirements

- Claude Code 2.1.281 or later, in the terminal or the Code tab in Claude Desktop.
- An Aixy account with MCP access, tools enabled by your organization, and your provider accounts
  connected in **Agent tools**.
- A personal Aixy MCP token. A model API key cannot authenticate this connection.

This release supports Claude Code. Chat and Cowork cannot prompt for this plugin's sensitive
personal token; this package does not provide their connector login flow.

## Install and configure

Run these commands in Claude Code:

```text
/plugin marketplace add aixy-tech/aixy-claude-plugin
/plugin install aixy@aixy-plugins
```

1. In your Aixy dashboard, open **Agent tools → Connect an agent**.
2. Select **Create MCP token**. Choose a name, expiration and optional project restriction.
3. Copy **Your MCP endpoint** and the token, which is shown once.
4. When Claude Code asks, enter the endpoint in **Aixy MCP endpoint** and the token in
   **Personal Aixy MCP token**. Paste the token value without `Bearer `.
5. Restart Claude Code if prompted and open `/mcp` to check the Aixy connection.

The default endpoint is Aixy's hosted service. Replace it with the exact trusted HTTPS endpoint
from your dashboard when your deployment uses another address. Claude sends your token to this
address; verify it before saving. Enter credentials only in Claude's plugin configuration form.
Do not paste tokens into a conversation, issue, screenshot, repository or shell command.

For the dashboard flow, see [Connect an agent](https://docs.aixy-gateway.com/agent-tools/connect-agent).

## Verify the connection

Ask Claude to list your Aixy connections using `aixy_connections`, then search for a capability
available to you using `aixy_search_tools`. Search does not execute the returned action. Review
the action and its arguments before authorizing execution.

Tool availability still follows your current Aixy permissions, project membership, connected
provider account and your organization's tool allowlist. A project restriction also permits
organization-wide tools that are available to you. Installing the plugin does not grant new
permissions or connect upstream accounts. Use the browser link returned by `aixy_connect` when
an account needs to be connected; provider credentials belong in the dashboard connection flow.

## Data handling

The plugin contains a remote MCP configuration and documentation. It downloads and runs no
additional packages, scripts or hooks. Claude Code's native HTTP transport sends your personal
MCP token in the Authorization header to your configured Aixy endpoint. The token is declared
sensitive so Claude Code stores it in its secure credential store; the endpoint is ordinary
plugin configuration.

When you use a tool, Claude sends its search query or action arguments to Aixy. Authorized actions
can send arguments to the upstream services you have connected, and tool results return through
Aixy to Claude. Consider the data included in those requests and the permissions of each connected
service. The plugin adds no analytics, local data store or separate external service.

The Aixy service records execution metadata such as tool name, status and duration; MCP Activity
retains it for 30 days by default. Discovery retains action identity and revision metadata in an
expiring context. This is separate from Claude's own data handling. See the
[Aixy privacy notice](https://aixy-gateway.com/privacy) and
[Agent tools documentation](https://docs.aixy-gateway.com/agent-tools/overview) for service behavior.

## Change or remove access

Open `/plugin`, select Aixy, and use its configuration controls to update the endpoint or token.
Use **Disable** or **Revoke** on the token in Aixy to block new authentication. Revocation is
permanent and does not disconnect your provider accounts or cancel actions already sent.
Uninstalling the plugin removes the client integration; revoke an unused token separately in Aixy.

If authentication fails, check the endpoint and whether the token has expired, been disabled or
been revoked. If a tool is missing, check your provider connection and permissions in the dashboard.
If a modifying call has an uncertain outcome, inspect the external system and MCP Activity before
retrying it. Do not automatically repeat an action that may already have completed.

For support, [open an issue](https://github.com/aixy-tech/aixy-claude-plugin/issues) without credentials,
tool arguments or private results, or contact [Aixy](mailto:hello@aixy-gateway.com).

## License

MIT for plugin configuration and documentation. Aixy names and logos remain trademarks of their
owner. This license does not cover the Aixy gateway service or connected third-party services.
