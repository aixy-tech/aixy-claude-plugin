# Plugin maintenance

- This repository distributes only the Aixy integration for Claude. Keep gateway implementation,
  internal documentation, credentials and tenant data out of it.
- Plugin source lives in `plugins/aixy`; the root marketplace catalog references that folder.
- Preserve personal bearer authentication, sensitive token configuration, configurable deployment
  endpoints, and the client's normal action approval policy. Do not add broad tool preapprovals.
- Describe the supported Claude surfaces accurately. Do not claim OAuth or Chat/Cowork support
  until that path is implemented and verified.
- Use an issue, a branch and isolated worktree for changes, then open a linked PR. Validate the
  plugin and catalog with `claude plugin validate --strict`, and run `git diff --check`.
- Do not manually dispatch, rerun or enable GitHub Actions without a maintainer's specific request.
- Increment the plugin version for releases. Keep public-repository delivery, local validation,
  automatic CI, Anthropic validation/review, publication and real-account verification distinct.
