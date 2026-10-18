# Claude directory release

The package is intended for Claude Code. The Aixy-owned marketplace is independent of Anthropic's
curated directory and `claude-plugins-official`. A working direct install does not establish a
directory listing or approval.

## Source

- Repository: `https://github.com/aixy-tech/aixy-claude-plugin`
- Plugin path: `plugins/aixy`
- Plugin name: `aixy`
- Initial version: `0.1.0`
- Suggested first submission: a version tag after review, with automatic publication disabled.
- License: MIT for the integration, approved by the maintainer. Gateway licensing is unaffected.

## Validate and release

Run the commands in the root README. Test installation in a disposable Claude configuration
directory, using synthetic values only. Inspect the artifact to ensure it contains the plugin
folder's regular files, with no secrets, machine files or other checkout content. No gateway build,
database, development slot or inference benchmark is needed for this configuration-only package.

After review, publish the standalone repository and tag the validated commit. In
[Claude's developer portal](https://claude.ai/directory/manage), choose **Plugin bundle**, enter the
repository, plugin path and release tag, and run **Validate**. The portal performs checks that the
local CLI does not. Revalidate whenever the submitted source changes.

## Listing and data handling

The manifest supplies the name, description, author, icon, documentation, support and privacy links.
The plugin README describes what the client executes and transmits. Answers in the portal must
cover the remote service as well as the configuration-only package:

- The client stores a personal MCP credential securely and sends it to the configured Aixy endpoint.
- Tool queries, arguments and results can contain personal data. Connected upstream services receive
  the data needed to perform an authorized action. Do not describe the integration as processing no
  personal data merely because the package contains no executable code.
- The plugin adds no telemetry or storage. Aixy has service-side execution and discovery metadata;
  retention must match the current public documentation and deployed configuration.
- Intended for workplace use. Do not make unsupported age, legal, security or certification claims.
- Verify the contact address and any legal acknowledgements with the maintainer at the point the
  portal requests them.

## Remote connector requirement

Anthropic's [directory publishing guide](https://claude.com/docs/directory/publish) asks publishers
that run the plugin's remote MCP server to submit it as an **MCP connector** separately. Prepare
that submission alongside the bundle; do not mark it approved before review.

Aixy currently authenticates inbound MCP using a personal bearer token. Its provider OAuth flows
connect Aixy to upstream accounts; they do not implement OAuth for Claude to sign in to Aixy.
Claude Code supports the manifest's `userConfig` prompt. Chat ignores a server whose URL includes
`user_config`, and Cowork cannot prompt for the required sensitive value. See the
[platform support matrix](https://claude.com/docs/plugins/platform-support).

The connector's `static_headers` authentication is a limited beta with an organization-owner
credential shared by members. It must not be presented as a personal-token replacement. A universal
Chat/Cowork connector needs a separately agreed authentication design and end-to-end verification;
see [connector authentication](https://claude.com/docs/connectors/building/authentication).

## Evidence states

Record the final commit and local checks in the PR. Record the portal validation findings,
submission ID, source tag, review status and publication status after the corresponding actions.
A passing scan is separate from publication, and publication is separate from a successful
personal-account connection and safe read-only tool discovery.
