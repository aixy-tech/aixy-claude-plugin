# Claude connector icon

These assets provide a standalone Aixy mark for Claude connector display metadata:

- `claude-connector-icon.svg`: native vector source with a transparent background.
- `claude-connector-icon.png`: matching transparent 1024 × 1024 PNG for a custom icon URL.

The existing A and coral dot are preserved. The A uses a cream fill and navy outline so the
mark remains visible on light and dark surfaces. The square background is omitted.

For Claude's **Custom icon URL**, use the PNG pinned to a full merged commit SHA:

```text
https://raw.githubusercontent.com/aixy-tech/aixy-claude-plugin/<full-commit-sha>/assets/claude-connector-icon.png
```

Replacing the placeholder with a reviewed merge commit keeps that URL stable. The files are
not applied to a connector automatically; configure its display metadata separately.

These assets live outside `plugins/aixy`. They do not change the plugin package, version,
manifest, packaged icon, OAuth behavior or permissions, and do not replace the website favicon.
When updating the vector source, regenerate the PNG from it and verify transparency and small
icon rendering on both backgrounds.
