# Aixy for Claude

Connect Claude to the tools available through your Aixy account. Version 0.2.0 uses a fixed
remote MCP connection with personal OAuth sign-in and explicit consent in your Aixy dashboard.

**Verified scope:** hosted OAuth is deployed. A dedicated review account completed one bounded,
read-only check through Claude chat's remote connector: connection listing, a dashboard connection
link, on-demand discovery with an input schema, and one approved public documentation search.
There were no retries or modifying actions. The review authorization was revoked and the client
disconnected after the test. MCP Inspector separately verified discovery, a read action,
authorization denial and revocation. Published versions are listed in
[GitHub Releases](https://github.com/aixy-tech/aixy-claude-plugin/releases). The retained
[v0.1.0 release](https://github.com/aixy-tech/aixy-claude-plugin/tree/v0.1.0)
retains the manual personal-token flow for Claude Code.

## Install

In Claude Code, run:

```text
/plugin marketplace add aixy-tech/aixy-claude-plugin
/plugin install aixy@aixy-plugins
```

These commands install from the default branch. The OAuth instructions describe 0.2.0; if you
use the retained manual-token release, follow its
[v0.1.0 setup instructions](https://github.com/aixy-tech/aixy-claude-plugin/blob/v0.1.0/plugins/aixy/README.md).

For OAuth setup, permissions, data handling and revocation, see the
[plugin README](plugins/aixy/README.md).

## Claude surfaces

The 0.2.0 package declares the fixed hosted endpoint `https://api.aixy-gateway.com/mcp` and uses
Claude's native OAuth connection flow. Keep these verification states distinct:

| Surface or check | Verified scope |
| --- | --- |
| Claude chat remote connector | One personal OAuth connection and bounded read-only tool round-trip |
| Claude Code plugin package | Strict validation and disposable installation; live OAuth and tool execution not verified |
| Cowork | Intended source format; real client connection and tool execution not verified |

The Claude chat check used the remote connector. It did not exercise plugin installation,
establish a directory listing, or verify live Cowork or Claude Code use.
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
