# Plugin maintenance

- This repository distributes only the Aixy integration for Claude. Keep gateway implementation,
  internal documentation, credentials and tenant data out of it.
- Plugin source lives in `plugins/aixy`; the root marketplace catalog references that folder.
- Version 0.2.0 uses the fixed hosted HTTPS MCP endpoint and the client's native personal OAuth
  connection flow. Do not add token headers, secret defaults, `userConfig`, scripts or hooks.
  Preserve the client's normal action approval policy. Do not add broad tool preapprovals.
- Keep the v0.1.0 manual-token release available. Hosted OAuth deployment and real-account
  verification are separate from preparing this plugin source. Do not merge, tag, release or
  submit version 0.2.0 to the directory until that runtime acceptance is complete.
- Describe supported Claude surfaces accurately. A fixed remote endpoint can be connected from
  Chat, Cowork and Claude Code, but do not claim a verified Aixy experience until each claimed
  path has been tested against the deployed service.
- Use an issue, a branch and isolated worktree for changes, then open a linked PR. Validate the
  plugin and catalog with `claude plugin validate --strict`, and run `git diff --check`.
- Build every PR body from `.github/PULL_REQUEST_TEMPLATE.md`; the CLI and API do not load it.
  Keep its headings unchanged and in order (`Related issue`, `Implementation`, `Validation`,
  `Risks and deviations`) and remove the guidance comments. Mark only verified checklist items
  and explain the others in place, report local validation and automatic CI separately, and
  write `None` when there are no risks or deviations.
- Do not manually dispatch, rerun or enable GitHub Actions without a maintainer's specific request.
- Increment the plugin version for releases. Keep public-repository delivery, local validation,
  automatic CI, Anthropic validation/review, publication and real-account verification distinct.
