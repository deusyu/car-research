# AGENTS.md

## Cursor Cloud specific instructions

### What this repo is
This repository is a **prompt-based Agent Skill** named `car-research` (see `SKILL.md`), not a
traditional software application. It contains only:
- Methodology / framework Markdown (`framework/`, `README.md`, `SKILL.md`)
- Completed research instances (e.g. `2026-04-七车对比/`) with self-contained HTML/PDF exports

There is **no package manager, no dependencies, no build system, no test suite, and no lint config**.
`git grep`-ing for `package.json` / `requirements.txt` / `Makefile` returns nothing. Do not add a
build toolchain unless the task explicitly asks for one. The update script is intentionally a no-op.

### How the "application" runs
The skill is executed by an AI agent that follows `SKILL.md`: it collects candidate cars, runs a
6-phase research pipeline using `WebSearch`/`WebFetch`/`Read`/`Write`, and writes Markdown reports
into a new instance directory. The tangible deliverables are the Markdown files plus the shareable
HTML/PDF exports under `<instance>/export/`.

### Previewing deliverables (build/run equivalent)
- Python 3 and Node are provided by the base image; nothing to install.
- Serve the repo and open an export in a browser:
  ```
  python3 -m http.server 8000   # run from repo root
  ```
- Instance directories and export filenames use **Chinese characters**, so URLs must be
  percent-encoded. Example: the report `2026-04-七车对比/export/su7-vs-model-y.html` is served at
  `http://localhost:8000/2026-04-%E4%B8%83%E8%BD%A6%E5%AF%B9%E6%AF%94/export/su7-vs-model-y.html`.

### Lint / test / build
None exist. Validation is limited to reviewing Markdown content and confirming the HTML exports
render correctly in a browser. Do not fabricate a CI/test setup.
