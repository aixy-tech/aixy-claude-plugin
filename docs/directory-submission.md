# Claude directory release

Version 0.2.0 prepares personal OAuth through the fixed hosted Aixy MCP endpoint. Hosted OAuth is
deployed. A dedicated review account has completed public documentation discovery and a read
action through MCP Inspector, including authorization denial and revocation checks. This finite
result does not establish Claude client acceptance. Do not merge, tag, release or submit 0.2.0
until a complete Claude client connection and tool round-trip have been accepted; verify each
additional client experience the listing will claim.

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
   organization, callback and optional project restriction shown in consent. Select the intended
   organization before starting; restart the connection if it changes while consent is open.
3. Verify safe read-only tool discovery with current account permissions.
4. Verify denial, expired authorization, renewal and explicit revocation, including a revoked
   connection being rejected by Aixy.
5. Record the deployed behavior and evidence before merging or creating the 0.2.0 release tag.

The Inspector result verifies one discovery search, one exact schema lookup and one explicitly
reviewed public documentation read. Package validation and isolated installation are also
verified. Claude, Cowork and Claude Code client acceptance remain separate from those checks.

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

## Isolated reviewer workspace

Use a dedicated review account with access only to a review project and its public documentation
server. The upstream documentation server requires no provider credentials. Allow only its
read-only search capability; exclude feedback and other write tools. Keep reviewer credentials,
invitation links and account instructions in the portal's private review fields, outside this
public repository.

Prepare these examples against that enabled fixture and confirm each in the claimed client:

1. **"Show my available Aixy connections and the dashboard link for the documentation server."**
   Expected: only permitted connections and the relevant dashboard link; no upstream action.
2. **"Find the search capability for the enabled Aixy documentation server."**
   Expected: the permitted action and its current input schema, without executing it.
3. **"Search those docs for MCP setup guidance."**
   Expected: a read action using the discovered schema and bounded public documentation results.

Resolve tool names and arguments from current discovery; do not treat tenant-specific action
names as a universal contract. These review examples do not make all Aixy tools read-only:
administrators can enable other upstream actions, subject to account permissions and approvals.

## Remote connector requirement

Anthropic's [directory publishing guide](https://claude.com/docs/directory/publish) asks publishers
that run a plugin's remote MCP server to submit it as an **MCP connector** separately. Prepare that
submission alongside the bundle and use the same fixed hosted URL so both refer to one connection.
Do not mark the connector approved before review.

The prepared plugin uses native OAuth discovery, not a manually supplied bearer header. Validate
the deployed authorization flow against [Claude's authentication requirements](https://claude.com/docs/connectors/building/authentication)
before acknowledging compliance or submitting. Upstream provider connections remain separate from
Claude's personal authorization to access Aixy.

The fixed URL follows the remote connector structure used by Chat, Cowork and Claude Code.
Compatibility of the source format and Inspector verification do not establish that any specific
Claude client has completed sign-in and a tool round-trip. See the
[platform support matrix](https://claude.com/docs/plugins/platform-support).

## Evidence states

Record the final commit and local checks in the PR. Record the hosted activation, personal-account
verification, portal validation findings, submission ID, source tag, review status and publication
status after the corresponding actions. Keep local checks, automatic CI, deployment, runtime
acceptance, directory review and publication distinct.
