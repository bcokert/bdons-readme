# Stack Research

**Domain:** Markdown-only personal manager readme repo (GitHub-native, no web layer)
**Researched:** 2026-05-10
**Confidence:** HIGH on GitHub rendering behavior; MEDIUM on linting toolchain (actively evolving)

---

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

**Current mismatch to fix:** The project currently uses `readme.md` (lowercase). Rename to `README.md` — one `git mv readme.md README.md` and update all cross-file links.

### File Layout

```
/                     <- repo root
  README.md           <- hub (one-page intro, all outbound links live here)
  values.md
  work.md
  playbooks.md
  style.md
  coop-d1.md
  junior-d2.md
  intermediate-d3.md
  senior-d4.md
  staff-d5.md
```

**Do not use a `docs/` subdirectory.** The `docs/` convention is for software projects where the root holds source code and the docs are a secondary artifact. Here, the docs ARE the product. Root-level files render directly on the GitHub repo landing page without extra navigation — exactly what the audience needs.

### Anchor and Deep-Link Conventions

GitHub auto-generates heading anchors using these rules (HIGH confidence — verified against GitHub's cmark-gfm behavior):

1. Lowercase all text
2. Replace spaces with `-`
3. Strip everything that is not a letter, number, or hyphen

Examples:
- `## Values and Priorities` → `#values-and-priorities`
- `## Feedback and Performance` → `#feedback-and-performance`
- `## Bdons Style` → `#bdons-style` (apostrophe stripped)

**Cross-file deep links:** Use relative paths with fragment. Example from `README.md`:
```markdown
[Feedback style](./style.md#feedback-and-performance)
```

**Anti-pattern — do not use HTML anchor tags:** `<a name="...">` or `<a id="...">` are stripped by GitHub's sanitizer in most contexts and are unnecessary — auto-generated heading anchors cover all same-page and cross-file deep-linking needs for this doc set.

**Anti-pattern — do not use absolute GitHub URLs:** `https://github.com/bdon/bdon-readme/blob/main/values.md` breaks if the repo is renamed or transferred. Use relative paths: `./values.md`.

### Table of Contents

**Do not add an inline TOC to any file in this repo.**

GitHub has natively rendered an interactive TOC button in the header of all markdown files since April 2021 (triggered when a file has 2+ headings). It covers all 6 heading levels, requires zero maintenance, and never goes stale.

An inline TOC creates two problems:
1. It requires manual upkeep or a generator to stay accurate — both are friction
2. It adds length to the hub file, which has a hard one-page constraint

The native GitHub TOC is sufficient. Trust it.

**Exception:** If a file has a single long section with no headings (unlikely given the structured voice), you can't use heading-based anchors. In that case, restructure with headings rather than adding a TOC.

### Diagrams and Images

| Need | Recommended Approach | Why |
|------|---------------------|-----|
| Simple flow/sequence diagrams | Mermaid fenced code block (` ```mermaid `) | GitHub has rendered Mermaid natively since Feb 2022. No external tooling. Renders in the browser, not as a static image. Supported types: flowchart, sequence, gantt, class, state, ER, pie. |
| More complex diagrams | Commit an SVG file, reference with `![alt](./diagram.svg)` | GitHub renders SVG via `<img>` tags. Clean, version-controlled, no JS risk. |
| Screenshots / photos | PNG preferred over JPG | PNG is lossless, diffs cleanly in git, renders reliably. |
| Inline SVG | Do not use | GitHub's markdown renderer strips `<svg>` elements entirely as a security measure. Must be a separate file referenced via `<img>`. |
| Base64 data URIs | Do not use | GitHub renders the `<img>` with an empty `src` — image is invisible. |

**Mermaid limitations to know:**
- Hyperlinks and tooltips inside Mermaid labels do not work on GitHub
- Some extended characters (emoji, non-ASCII) cause parse errors
- Gist editor preview does not render Mermaid (only post-publish)
- GitHub Pages does NOT render Mermaid — irrelevant here since there is no Pages layer, but good to know

For a manager readme, Mermaid is appropriate for the `$$\text{Team Net Impact}$$` equation if converted to a diagram, or for any process flows in `playbooks.md`.

### Linting

**Primary linter: `markdownlint-cli2`** (not `markdownlint-cli`)

`markdownlint-cli2` is the actively developed tool from the same author (DavidAnson). The original `markdownlint-cli` will receive dependency updates but no new features. `markdownlint-cli2` uses config-file-first design and works with the VSCode markdownlint extension out of the box.

**Configuration file:** `.markdownlint-cli2.mjs` at repo root

**Recommended base config:**

```json
// .markdownlint.json (simpler alternative to .mjs for small repos)
{
  "default": true,
  "MD013": false,
  "MD033": false
}
```

Rule rationale:
- `MD013` (line length): Disable. Long URLs and table cells will always trigger this. For prose, Prettier handles wrapping.
- `MD033` (inline HTML): Disable only if you use `<img>` for SVG files. If the repo stays HTML-free, keep it enabled — it catches accidental HTML.
- All other defaults: Keep enabled. They catch real problems (heading level jumps, missing blank lines around headings, inconsistent list markers).

**Formatter: Prettier** — optional but recommended for consistent whitespace

Key Prettier settings for markdown:
```json
{
  "proseWrap": "preserve",
  "tabWidth": 2
}
```

`proseWrap: "preserve"` is the right choice here: it does not reflow existing prose (which would mangle Bdon's intentional line breaks and list formatting) but will normalize whitespace and trailing spaces. Do not use `"always"` — it hard-wraps prose at 80 chars which destroys readability in GitHub's rendered view and fights markdownlint line-length rules.

**Prettier + markdownlint coexistence:** Extend `markdownlint/style/prettier` to disable the handful of markdownlint rules that duplicate what Prettier handles (blank lines, indentation). With default `tabWidth: 2`, no further coordination is needed.

**GitHub's own ruleset:** `github/markdownlint-github` adds three accessibility rules (GH001–GH003) focused on image alt text. Incorporate these if images are used; skip for a text-only doc.

### Development Tools

| Tool | Purpose | Notes |
|------|---------|-------|
| `markdownlint-cli2` | Lint all `.md` files on save and in CI | `npx markdownlint-cli2 "**/*.md"` |
| Prettier | Normalize whitespace, list indentation | `npx prettier --write "**/*.md"` |
| VSCode extension: `DavidAnson.vscode-markdownlint` | Inline lint feedback while editing | Reads `.markdownlint-cli2.mjs` or `.markdownlint.json` automatically |
| VSCode extension: `esbenp.prettier-vscode` | Format on save | Configure `"[markdown]": { "editor.defaultFormatter": "esbenp.prettier-vscode", "editor.formatOnSave": true }` |

---

## Alternatives Considered

| Recommended | Alternative | When to Use Alternative |
|-------------|-------------|-------------------------|
| Root-level files | `docs/` subdirectory | Only when the repo also contains source code and docs are a secondary concern |
| Mermaid for diagrams | Kroki, PlantUML, D2 | If Mermaid's diagram types are insufficient — none are needed for a manager readme |
| markdownlint-cli2 | markdownlint-cli | If already using the old CLI and not hitting feature gaps — no reason to migrate mid-project |
| `proseWrap: "preserve"` | `proseWrap: "always"` | Only if the team writes source markdown in narrow-terminal editors and never reads the raw file on GitHub |
| Auto-generated heading anchors | `<a id="...">` HTML anchors | Never — GitHub strips or ignores them in rendered markdown |
| Native GitHub TOC | Inline TOC (manual or generated) | Never for this project — hub has a hard length constraint |

---

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

---

## Installation

```bash
# Linting (dev-only, no runtime dependencies)
npm init -y
npm install -D markdownlint-cli2 prettier

# Optional: GitHub's accessibility rule extensions
npm install -D markdownlint-github
```

No `package.json` scripts are required — the tooling is editor-integrated and optionally CI-invoked. If you want `npm run lint`:

```json
{
  "scripts": {
    "lint": "markdownlint-cli2 '**/*.md'",
    "format": "prettier --write '**/*.md'"
  }
}
```

---

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

---

*Stack research for: markdown-only personal manager readme repo*
*Researched: 2026-05-10*
