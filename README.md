# Aixy for Claude Code

Connect Claude Code to the tools available through your Aixy account. The plugin asks for your
MCP endpoint and personal MCP token, then uses Claude Code's native Streamable HTTP transport.

## Install

In Claude Code, run:

```text
/plugin marketplace add aixy-tech/aixy-claude-plugin
/plugin install aixy@aixy-plugins
```

When Claude asks for configuration, paste the endpoint and personal MCP token from
**Agent tools → Connect an agent** in your Aixy dashboard. The token field is sensitive and
uses Claude Code's secure credential storage. Restart Claude Code if prompted.

See the [plugin README](plugins/aixy/README.md) for account setup, permissions, data handling,
verification and troubleshooting. Use Claude Code 2.1.281 or later.

## Supported clients

This version supports Claude Code, including the Code tab in Claude Desktop. Chat and Cowork
do not support this plugin's personal-token configuration flow. The
[Claude platform support matrix](https://claude.com/docs/plugins/platform-support) describes
the current differences.

## Maintain and validate

The directory submission folder is `plugins/aixy`. The repository's
`.claude-plugin/marketplace.json` is a separate Aixy-owned catalog for direct installation.

```sh
claude plugin validate plugins/aixy --strict
claude plugin validate .claude-plugin/marketplace.json --strict
git diff --check
```

Changes to the plugin require a version bump in `plugins/aixy/.claude-plugin/plugin.json`.
The marketplace reads that version from the plugin. See the
[directory release guide](docs/directory-submission.md) before submitting or releasing.

## License

The plugin configuration and documentation are MIT licensed. Aixy names and logos remain
trademarks of their owner; see [NOTICE](NOTICE). This repository contains only the Claude
integration. It does not license or distribute the Aixy gateway service.
