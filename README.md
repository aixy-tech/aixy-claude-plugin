# Aixy for Claude

Connect Claude to the tools available through your Aixy account. Version 0.2.0 prepares a fixed
remote MCP connection with personal OAuth sign-in and explicit consent in your Aixy dashboard.

**Activation pending:** 0.2.0 is source-ready for review. Hosted OAuth deployment and a successful
real-account connection are still required before merging, tagging, releasing or submitting it to
the Claude directory. The stable [v0.1.0 release](https://github.com/aixy-tech/aixy-claude-plugin/tree/v0.1.0)
retains the manual personal-token flow for Claude Code.

## Install

The default branch currently serves the stable release. In Claude Code, run:

```text
/plugin marketplace add aixy-tech/aixy-claude-plugin
/plugin install aixy@aixy-plugins
```

Follow the [v0.1.0 setup instructions](https://github.com/aixy-tech/aixy-claude-plugin/blob/v0.1.0/plugins/aixy/README.md)
for that release. These commands will serve 0.2.0 only after its reviewed source is merged and
the hosted OAuth path has been accepted.

For the proposed OAuth setup, permissions, data handling and revocation, see the
[plugin README](plugins/aixy/README.md).

## Claude surfaces

The 0.2.0 package declares the fixed hosted endpoint `https://api.aixy-gateway.com/mcp` and uses
Claude's native OAuth connection flow. This configuration is intended for Chat, Cowork and Claude
Code. Hosted Aixy OAuth and each claimed client experience still need deployment and verification.
The [Claude platform support matrix](https://claude.com/docs/plugins/platform-support) explains
how remote connectors are connected on each surface.

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
