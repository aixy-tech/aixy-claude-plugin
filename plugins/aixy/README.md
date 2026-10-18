# Aixy

Connect Claude to the external tools your organization makes available through Aixy. Use one MCP
connection with your own account and permissions. Aixy discovers permitted tools on demand, and
Claude controls when it asks you to approve external actions.

**Version 0.2.0 is not released.** Hosted OAuth and a dedicated review account's public documentation
search have been verified with MCP Inspector, including denial and revocation. A complete Claude
client connection and tool round-trip remain pending before release or directory submission. The
stable [v0.1.0 package](https://github.com/aixy-tech/aixy-claude-plugin/tree/v0.1.0/plugins/aixy)
continues to document the manual-token flow for Claude Code.

## Requirements

- A Claude client and account that support remote MCP connections and OAuth sign-in.
- An Aixy account with MCP access and a server enabled for your organization or project.
- Your own provider account connected in **Agent tools** when that server requires authentication.

This package targets Aixy's hosted service at `https://api.aixy-gateway.com/mcp`. It contains no
token configuration prompt. The fixed remote connection is intended for Chat, Cowork and Claude
Code; each client experience needs verification before it is claimed as supported. See the
[Claude support matrix](https://claude.com/docs/plugins/platform-support).

## Install and connect after activation

In Claude Code, add the Aixy marketplace and install the plugin:

```text
/plugin marketplace add aixy-tech/aixy-claude-plugin
/plugin install aixy@aixy-plugins
```

Until version 0.2.0 is merged and released, the default branch serves the stable manual-token
version. After 0.2.0 is accepted and released:

1. Select the intended organization in Aixy before starting the connection.
2. Open `/mcp` in Claude Code and use Aixy's authentication action. In Chat or Cowork, connect
   Aixy from the plugin's **Connectors** tab once the plugin is available in your account.
3. Sign in to your Aixy account in the browser when prompted.
4. Review the app's name, callback address, your account and organization on the consent screen.
   If you change organizations while that screen is open, restart the connection from Claude.
5. Optionally restrict access to a project, then select **Allow access**. Organization-wide tools
   available to you remain accessible with a project restriction.
6. Return to Claude and confirm the Aixy connection is available.

Choose **Deny access** if you did not start the connection or do not recognize the callback
address. Enter credentials only in the Aixy sign-in flow. Do not paste tokens or authorization
codes into a conversation, issue, screenshot, repository or shell command.

For the dashboard flow, see [Connect an agent](https://docs.aixy-gateway.com/agent-tools/connect-agent).

## Verify the connection

Ask Claude to list your Aixy connections using `aixy_connections`, then search for a capability
available to you using `aixy_search_tools`. Search does not execute the returned action. Review
the action and its arguments before authorizing execution.

Tool availability follows your current Aixy permissions, project membership, provider connection
when required, and your organization's tool allowlist. Organization administrators configure
servers and their allowed tools; your OAuth consent authorizes your access to Aixy. Installing the
plugin does not grant new permissions or connect upstream accounts. Use the browser link returned
by `aixy_connect` when an account needs to be connected; provider credentials belong in the
dashboard connection flow.

If your organization has enabled the Aixy public documentation server, you can ask Claude to
find its search capability and search those docs for MCP setup guidance. That server needs no
provider sign-in. Review the tool and arguments returned for your account; this example does not
enable the documentation server automatically.

## Data handling

The plugin contains a fixed remote MCP configuration and documentation. It downloads and runs no
additional packages, scripts or hooks. Claude's native OAuth client obtains and stores the access
and refresh credentials for the Aixy connection. Its native HTTP transport sends an access token
in the Authorization header to `https://api.aixy-gateway.com/mcp`.

When you use a tool, Claude sends its search query or action arguments to Aixy. Authorized actions
can send arguments to the upstream services you have connected, and tool results return through
Aixy to Claude. Consider the data included in those requests and the permissions of each connected
service. The plugin adds no analytics, local data store or separate external service.

The Aixy service records execution metadata such as tool name, status and duration; MCP Activity
retains it for 30 days by default. Discovery retains action identity and revision metadata in an
expiring context. This is separate from Claude's own data handling. See the
[Aixy privacy notice](https://aixy-gateway.com/privacy) and
[Agent tools documentation](https://docs.aixy-gateway.com/agent-tools/overview) for service behavior.

## Revoke or remove access

In Aixy, open **Agent tools → Connect an agent → Authorized apps**, find the app and select
**Revoke access**. Revoking a connection blocks its OAuth credentials; it does not disconnect your
provider accounts or cancel actions already sent to an external service.

You can also disconnect Aixy in Claude or uninstall the plugin. Revoke the app in Aixy to remove
its server-side authorization. Connecting again requires a new consent flow.

If sign-in fails, confirm your intended organization and restart the connection from Claude. If a
tool is missing, check the enabled server, permissions and any required provider connection in
the dashboard. If a modifying call has an uncertain outcome, inspect the external system and
MCP Activity before retrying it.
Do not automatically repeat an action that may already have completed.

For support, [open an issue](https://github.com/aixy-tech/aixy-claude-plugin/issues) without credentials,
tool arguments or private results, or contact [Aixy](mailto:hello@aixy-gateway.com).

## License

MIT for plugin configuration and documentation. Aixy names and logos remain trademarks of their
owner. This license does not cover the Aixy gateway service or connected third-party services.
