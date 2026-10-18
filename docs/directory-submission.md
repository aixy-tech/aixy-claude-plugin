# Claude directory release

Version 0.2.0 prepares personal OAuth through the fixed hosted Aixy MCP endpoint. It is source-ready
for review; hosted OAuth deployment and successful real-account validation remain pending.
Do not merge, tag, release or submit 0.2.0 until those activation requirements are met.

The Aixy-owned marketplace is independent of Anthropic's curated directory and
`claude-plugins-official`. A direct install does not establish a directory listing or approval.

## Source

- Repository: `https://github.com/aixy-tech/aixy-claude-plugin`
- Plugin path: `plugins/aixy`
- Plugin name: `aixy`
- Prepared version: `0.2.0`
- Stable manual-token version: `v0.1.0`; preserve that tag and its contents.
- Suggested submission source: a version tag after runtime acceptance and source review, with
  automatic publication disabled.
- License: MIT for the integration, approved by the maintainer. Gateway licensing is unaffected.

## Validate before activation

Run the commands in the root README. Test installation in a disposable Claude configuration
directory without credentials or live MCP calls. Inspect the installed plugin to confirm its
regular files and fixed HTTPS endpoint contain no token headers, `userConfig`, secrets, machine
files or unrelated checkout content. No gateway build, database, development slot or inference
benchmark is needed for this configuration-only package.

## Accept the hosted connection before release

1. Verify that the hosted MCP endpoint advertises the intended Aixy OAuth sign-in flow.
2. Connect a real account from each Claude surface the listing will claim. Confirm the account,
   organization, callback and optional project restriction shown in consent.
3. Verify safe read-only tool discovery with current account permissions.
4. Verify denial, expired authorization, renewal and explicit revocation, including a revoked
   connection being rejected by Aixy.
5. Record the deployed behavior and evidence before merging or creating the 0.2.0 release tag.

After runtime acceptance and review, tag the validated source. In
[Claude's developer portal](https://claude.ai/directory/manage), choose **Plugin bundle**, enter the
repository, plugin path and release tag, and run **Validate**. The portal performs checks that the
local CLI does not. Revalidate whenever the submitted source changes. A passing validation is
separate from submission, Anthropic review and publication.

## Listing and data handling

The manifest supplies the name, description, author, icon, documentation, support and privacy links.
The plugin README describes what the client executes and transmits. Answers in the portal must
cover the remote service as well as the configuration-only package:

- Claude stores OAuth credentials and sends an access token to the hosted Aixy MCP endpoint.
- Tool queries, arguments and results can contain personal data. Connected upstream services receive
  the data needed to perform an authorized action. Do not describe the integration as processing no
  personal data merely because the package contains no executable code.
- The plugin adds no telemetry or storage. Aixy has service-side execution and discovery metadata;
  retention must match the current public documentation and deployed configuration.
- Intended for workplace use. Do not make unsupported age, legal, security or certification claims.
- Verify the contact address and legal acknowledgements at the point the portal requests them.

## Remote connector requirement

Anthropic's [directory publishing guide](https://claude.com/docs/directory/publish) asks publishers
that run a plugin's remote MCP server to submit it as an **MCP connector** separately. Prepare that
submission alongside the bundle and use the same fixed hosted URL so both refer to one connection.
Do not mark the connector approved before review.

The prepared plugin uses native OAuth discovery, not a manually supplied bearer header. Validate
the deployed authorization flow against [Claude's authentication requirements](https://claude.com/docs/connectors/building/authentication)
before acknowledging compliance or submitting. Upstream provider connections remain separate from
Claude's personal authorization to access Aixy.

The fixed URL is compatible with the remote connector structure used by Chat, Cowork and Claude
Code. Compatibility of the source format does not establish that the hosted OAuth service is
active or that any specific client has completed sign-in. See the
[platform support matrix](https://claude.com/docs/plugins/platform-support).

## Evidence states

Record the final commit and local checks in the PR. Record the hosted activation, personal-account
verification, portal validation findings, submission ID, source tag, review status and publication
status after the corresponding actions. Keep local checks, automatic CI, deployment, runtime
acceptance, directory review and publication distinct.
