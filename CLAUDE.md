<!-- GSD:project-start source:PROJECT.md -->
## Project

**Bdon's Manager Readme**

A layered, scannable manager readme — Bdon's working philosophy, values, style, and management playbooks — for his direct reports at Vidyard. The hub (`readme.md`) is a one-page intro with links out to per-category deep-dives (`values.md`, `work.md`, `playbooks.md`, `style.md`), plus the existing per-level dev ladder docs (`coop-d1.md` through `staff-d5.md`). Used as a conversation companion during onboarding and as a refresher afterwards.

**Core Value:** Devs new to working with Bdon get the gist in one page — and can drill in on any topic when they need it — without him having to be in the room.

### Constraints

- **Format**: Markdown only — must render cleanly on plain GitHub
- **Hub length**: `readme.md` fits on one page / one screen — non-negotiable
- **Voice**: Preserve Bdon's existing voice; light editing only, no rewrites
- **Structure**: One file per major category, sub-topics inline within that file. D1–D5 ladder is the documented exception — already split, stays split.
- **Audience-first**: Optimized for Bdon's devs at Vidyard, not for public consumption
<!-- GSD:project-end -->

<!-- GSD:stack-start source:research/STACK.md -->
## Technology Stack

## Recommended Stack
### Markdown Flavor
| Decision | Choice | Why |
|----------|--------|-----|
| Target renderer | GitHub Flavored Markdown (GFM) | The audience reads on GitHub. GFM is cmark + tables, task lists, strikethrough, autolinks. It is a strict superset of CommonMark — any valid CommonMark is valid GFM. Write GFM, don't chase CommonMark purity. |
| Math rendering | Avoid LaTeX math blocks | GFM renders `$$...$$` in some contexts but it is unreliable in plain README files. The existing equation in `readme.md` is decorative — if it needs to stay, test it renders; otherwise convert to prose. |
| HTML in markdown | Avoid inline HTML | GitHub strips or sandboxes most HTML. The one exception worth knowing: `<img src="...">` is required for SVG files (see Diagrams below). No `<div>`, `<details>`, `<table>`, or custom anchors. |
### File Naming
| Decision | Choice | Why |
|----------|--------|-----|
| Hub filename | `README.md` (uppercase) | GitHub displays `README.md` automatically on the repo landing page. Case matters on Linux hosts — `readme.md` works today but is non-standard and fragile. Uppercase is the established GitHub convention. |
| Per-category files | lowercase with hyphens: `values.md`, `work.md`, `playbooks.md`, `style.md` | GitHub renders any `.md` file by URL. Lowercase-with-hyphens is the unix/web convention for non-root docs. No spaces, no underscores. |
| Dev ladder files | Keep existing: `coop-d1.md`, `junior-d2.md`, etc. | Already established; renaming breaks existing links and history. |
### File Layout
### Anchor and Deep-Link Conventions
- `## Values and Priorities` → `#values-and-priorities`
- `## Feedback and Performance` → `#feedback-and-performance`
- `## Bdons Style` → `#bdons-style` (apostrophe stripped)
### Table of Contents
### Diagrams and Images
| Need | Recommended Approach | Why |
|------|---------------------|-----|
| Simple flow/sequence diagrams | Mermaid fenced code block (` ```mermaid `) | GitHub has rendered Mermaid natively since Feb 2022. No external tooling. Renders in the browser, not as a static image. Supported types: flowchart, sequence, gantt, class, state, ER, pie. |
| More complex diagrams | Commit an SVG file, reference with `![alt](./diagram.svg)` | GitHub renders SVG via `<img>` tags. Clean, version-controlled, no JS risk. |
| Screenshots / photos | PNG preferred over JPG | PNG is lossless, diffs cleanly in git, renders reliably. |
| Inline SVG | Do not use | GitHub's markdown renderer strips `<svg>` elements entirely as a security measure. Must be a separate file referenced via `<img>`. |
| Base64 data URIs | Do not use | GitHub renders the `<img>` with an empty `src` — image is invisible. |
- Hyperlinks and tooltips inside Mermaid labels do not work on GitHub
- Some extended characters (emoji, non-ASCII) cause parse errors
- Gist editor preview does not render Mermaid (only post-publish)
- GitHub Pages does NOT render Mermaid — irrelevant here since there is no Pages layer, but good to know
### Linting
- `MD013` (line length): Disable. Long URLs and table cells will always trigger this. For prose, Prettier handles wrapping.
- `MD033` (inline HTML): Disable only if you use `<img>` for SVG files. If the repo stays HTML-free, keep it enabled — it catches accidental HTML.
- All other defaults: Keep enabled. They catch real problems (heading level jumps, missing blank lines around headings, inconsistent list markers).
### Development Tools
| Tool | Purpose | Notes |
|------|---------|-------|
| `markdownlint-cli2` | Lint all `.md` files on save and in CI | `npx markdownlint-cli2 "**/*.md"` |
| Prettier | Normalize whitespace, list indentation | `npx prettier --write "**/*.md"` |
| VSCode extension: `DavidAnson.vscode-markdownlint` | Inline lint feedback while editing | Reads `.markdownlint-cli2.mjs` or `.markdownlint.json` automatically |
| VSCode extension: `esbenp.prettier-vscode` | Format on save | Configure `"[markdown]": { "editor.defaultFormatter": "esbenp.prettier-vscode", "editor.formatOnSave": true }` |
## Alternatives Considered
| Recommended | Alternative | When to Use Alternative |
|-------------|-------------|-------------------------|
| Root-level files | `docs/` subdirectory | Only when the repo also contains source code and docs are a secondary concern |
| Mermaid for diagrams | Kroki, PlantUML, D2 | If Mermaid's diagram types are insufficient — none are needed for a manager readme |
| markdownlint-cli2 | markdownlint-cli | If already using the old CLI and not hitting feature gaps — no reason to migrate mid-project |
| `proseWrap: "preserve"` | `proseWrap: "always"` | Only if the team writes source markdown in narrow-terminal editors and never reads the raw file on GitHub |
| Auto-generated heading anchors | `<a id="...">` HTML anchors | Never — GitHub strips or ignores them in rendered markdown |
| Native GitHub TOC | Inline TOC (manual or generated) | Never for this project — hub has a hard length constraint |
## What NOT to Use
| Avoid | Why | Use Instead |
|-------|-----|-------------|
| Static site generators (Jekyll, Docusaurus, MkDocs) | Out of scope; adds a build step and hosting concern | Plain GitHub markdown rendering |
| Inline `<svg>` elements in markdown | GitHub strips the `<svg>` tag entirely — renders nothing | Commit as `.svg` file, reference with `![](./file.svg)` |
| Base64 data URIs in `<img src>` | GitHub nullifies the `src` attribute — invisible | Same as above |
| `<a name="...">` custom anchors | GitHub sanitizes these in most contexts; auto-generated heading IDs are sufficient | Use heading-based auto-anchors |
| Generated inline TOC (doctoc, gh-md-toc) | Becomes stale the moment headings change; adds maintenance burden; wastes vertical space on the hub | GitHub's native TOC button (automatic, always current) |
| Absolute GitHub URLs for cross-file links | Breaks on repo rename or transfer | Relative paths: `./file.md#section` |
| `README.md` (uppercase) in subdirectories | Creates confusion if there are ever subdirectories — but there shouldn't be any here | n/a |
| LaTeX math blocks (`$$...$$`) | Unreliable in plain README context on GitHub | Convert to prose or a Mermaid diagram |
| `proseWrap: "always"` in Prettier | Hard-wraps prose at print width, making raw markdown hard to read and creating spurious diffs | `proseWrap: "preserve"` |
## Installation
# Linting (dev-only, no runtime dependencies)
# Optional: GitHub's accessibility rule extensions
## Sources
- [GitHub Flavored Markdown Spec](https://github.blog/engineering/user-experience/a-formal-spec-for-github-markdown/) — GFM is CommonMark + extensions (HIGH confidence)
- [Markdown Rendering Engines: CommonMark, GFM, Pandoc Compared](https://dasroot.net/posts/2026/04/markdown-rendering-engines-commonmark-gfm-pandoc-compared/) — 2026 rendering comparison (MEDIUM confidence)
- [github/markdownlint-github](https://github.com/github/markdownlint-github) — GitHub's own ruleset, GH001–GH003 accessibility rules (HIGH confidence)
- [DavidAnson/markdownlint](https://github.com/DavidAnson/markdownlint) — markdownlint core, Prettier.md integration guide (HIGH confidence)
- [DavidAnson/markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) — recommended CLI, actively developed (HIGH confidence)
- [markdownlint Prettier.md](https://github.com/DavidAnson/markdownlint/blob/main/doc/Prettier.md) — official coexistence guide (HIGH confidence)
- [GitHub TOC Changelog](https://github.blog/changelog/2021-04-13-table-of-contents-support-in-markdown-files/) — native interactive TOC, 2+ headings, all 6 levels (HIGH confidence)
- [GitHub Heading Anchor Rules](https://gist.github.com/asabaylus/3071099) — slug generation: lowercase, spaces→hyphens, strip punctuation (MEDIUM confidence — community-documented, not official spec)
- [GitHub Basic Writing and Formatting Syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) — official GFM syntax reference (HIGH confidence)
- [SVGs on GitHub](https://alexwlchan.net/notes/2024/how-to-render-svgs-on-github/) — `<img src>` works; inline `<svg>` stripped; base64 invisible (HIGH confidence — verified 2024)
- [GitHub Mermaid announcement](https://github.blog/developer-skills/github/include-diagrams-markdown-files-mermaid/) — native Mermaid support since Feb 2022 (HIGH confidence)
- [Prettier prose-wrap options](https://prettier.io/docs/options) — `preserve` default behavior for markdown (HIGH confidence)
- [Configuring Markdownlint Alongside Prettier](https://www.joshuakgoldberg.com/blog/configuring-markdownlint-alongside-prettier/) — extends `markdownlint/style/prettier` pattern (MEDIUM confidence)
<!-- GSD:stack-end -->

<!-- GSD:conventions-start source:CONVENTIONS.md -->
## Conventions

Conventions not yet established. Will populate as patterns emerge during development.
<!-- GSD:conventions-end -->

<!-- GSD:architecture-start source:ARCHITECTURE.md -->
## Architecture

Architecture not yet mapped. Follow existing patterns found in the codebase.
<!-- GSD:architecture-end -->

<!-- GSD:skills-start source:skills/ -->
## Project Skills

No project skills found. Add skills to any of: `.claude/skills/`, `.agents/skills/`, `.cursor/skills/`, `.github/skills/`, or `.codex/skills/` with a `SKILL.md` index file.
<!-- GSD:skills-end -->

<!-- GSD:workflow-start source:GSD defaults -->
## GSD Workflow Enforcement

Before using Edit, Write, or other file-changing tools, start work through a GSD command so planning artifacts and execution context stay in sync.

Use these entry points:
- `/gsd-quick` for small fixes, doc updates, and ad-hoc tasks
- `/gsd-debug` for investigation and bug fixing
- `/gsd-execute-phase` for planned phase work

Do not make direct repo edits outside a GSD workflow unless the user explicitly asks to bypass it.
<!-- GSD:workflow-end -->



<!-- GSD:profile-start -->
## Developer Profile

> Profile not yet configured. Run `/gsd-profile-user` to generate your developer profile.
> This section is managed by `generate-claude-profile` -- do not edit manually.
<!-- GSD:profile-end -->
