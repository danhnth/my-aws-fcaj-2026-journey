# AGENTS.md — my-aws-fcaj-2026-journey

Bilingual Hugo documentation site for the "AWS Security Operations & Hardening" workshop (insecure-by-design → managed remediation). The only git repo in the workspace. Deployed to GitHub Pages at `https://danhnth.github.io/my-aws-fcaj-2026-journey/`.

## STRUCTURE

```
my-aws-fcaj-2026-journey/
├── content/          # ALL authored prose. 62 .md files, 31 EN/VI pairs.
├── layouts/          # 6 theme overrides only (partials + shortcodes)
├── static/           # css/{theme-mine,theme-workshop}.css, fonts, images, AWS_Logo.svg
├── archetypes/       # default.md — Hugo `new` template
├── themes/           # hugo-theme-learn — GIT SUBMODULE, 236 tracked files
├── public/           # gitignored build output
├── amazon-guardduty-tester-master/   # gitignored upstream clone, NOT tracked (0 files in git)
└── config.toml
```

## WHERE TO LOOK

| Task | Location |
|---|---|
| Add/edit a weekly worklog | `content/1-Worklog/1.{N}-Week{N}/_index.md` + `_index.vi.md` |
| Add/edit a workshop step | `content/5-Workshop/5.{N}-{Step}/_index.md` (+ `.vi`) |
| Step screenshots | `content/5-Workshop/5.{6,7,8}-*/Screenshots/` (colocated, not in `static/`) |
| Site title / languages / theme variant | `config.toml` |
| Override theme header/footer/logo | `layouts/partials/{custom-footer,logo,menu-footer}.html` |
| Tabbed code blocks in content | `layouts/shortcodes/{tab,tabs}.html` |
| Deploy pipeline | `.github/workflows/hugo.yml` |

## CONVENTIONS

- **Branch bundles only.** Every page is `{folder}/_index.md`. There are zero leaf `.md` pages — do not create `content/foo.md`.
- **Every page is a pair.** `_index.md` (English) + `_index.vi.md` (Vietnamese). Adding one without the other breaks the language switcher.
- **Front-matter shape** (all five keys, in this order):
  ```yaml
  ---
  title: "Week 1 Worklog"
  date: 2026-06-25
  weight: 1
  chapter: false
  pre: " <b> 1.1. </b> "
  ---
  ```
  `weight` = the number in the folder name. `pre` = the dotted section number as bold HTML, with surrounding spaces. `chapter: false` on leaf sections.
- **Folder naming**: top-level `{N}-{PascalOrKebab}/`, nested `{N}.{M}-{Name}/`. Section 5 goes to 5.10 — `weight` ordering (not lexical) keeps 5.10 after 5.9.
- **Body starts at `###`.** The theme renders the H1 from front-matter `title`; do not add `#` in the body.
- **Screenshots** live beside their page under `Screenshots/`, referenced relatively — not under `static/images/`.
- `markup.goldmark.renderer.unsafe = true` — raw HTML is permitted in content.

## ANTI-PATTERNS

- **Do not edit `themes/hugo-theme-learn/`.** It is a submodule (`.gitmodules` → matcornic/hugo-theme-learn). Customize via `layouts/` overrides and `static/css/theme-workshop.css` instead.
- **Do not commit inside `amazon-guardduty-tester-master/`.** `.gitignore` excludes it; git tracks 0 files there. Work is lost silently.
- **Do not hand-write `public/`.** `.gitignore` has `public/*`; CI regenerates it into the `gh-pages` branch with `force_orphan: true`, discarding any manual history.
- **Do not change `baseURL` in `config.toml` to fix a broken deploy.** CI overrides it: `hugo --minify --baseURL "https://<owner>.github.io/<repo>/"`. The `config.toml` value (`workshop-sample.awsfcaj.com`) is inherited boilerplate and is only used locally.
- **Do not rename a numbered folder without updating `weight` and `pre`** in both language files — the sidebar order and the displayed section number are independent of the path.

## COMMANDS

```bash
hugo server -D                # local preview, drafts included
hugo new content/5-Workshop/5.11-Foo/_index.md   # applies archetypes/default.md
git submodule update --init --recursive          # required on fresh clone or theme is missing
```

CI: push to `main` → Hugo 0.134.3 extended → `peaceiris/actions-gh-pages@v4` → `gh-pages`.

## NOTES

- `config.toml` `params.author` is still `thienlh@thienlu.com` from the upstream template.
- `themeVariant = "workshop"` selects `static/css/theme-workshop.css`; `theme-mine.css` is unused.
- Working tree currently has ~15 modified content files uncommitted.
