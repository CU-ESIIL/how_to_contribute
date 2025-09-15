title: "How to Contribute to OASIS"
description: "Author guidelines for contributing templates and documentation to the OASIS GitHub organization. MkDocs-Material friendly version (no inline HTML)."

# How to Contribute to OASIS

OASIS is a GitHub organization that serves as a **third space for collaborative development**. We accept two contribution types:

1. **Templates** — repository scaffolds that others can clone and adapt.
2. **Documentation** — structured guides, quickstarts, and lessons in shared docs repos.

This page is a **detailed, style-aligned guide** for authors. It uses MkDocs-Material conventions: plain Markdown, admonitions, and optional collapsible examples. No inline HTML or custom CSS.

---

## Templates

Templates are starting points for common project types. Typical categories:

* Research project template (analysis + code + data)
* Data repository template (metadata + structure)
* Documentation site template (MkDocs or Pages)
* Workshop/event template (agendas, slides, materials)

### Required Files and Structure

* Repository name: **kebab-case**, e.g. `research-template`.
* Root files:

  * `README.md` — purpose, quickstart, customization notes
  * `LICENSE` — Apache-2.0 by default (or another OSI license with rationale)
  * `CONTRIBUTING.md` — how to contribute back
  * `CODE_OF_CONDUCT.md` — use OASIS code of conduct
* GitHub configuration:

  * `.github/ISSUE_TEMPLATE/bug_report.md`
  * `.github/ISSUE_TEMPLATE/feature_request.md`
  * `.github/PULL_REQUEST_TEMPLATE.md`
  * `.github/workflows/ci.yml` (lint/tests) and/or `link-check.yml`
* Suggested layout:

  * `src/` or `notebooks/` — code
  * `data/` — sample or placeholder with a README describing expected contents
  * `docs/` — quickstart, examples, decisions

!!! tip
Include a **minimal working example** (one script + tiny dataset) so users can run the template in under a minute.

### Authoring Guidelines (Templates)

* Quickstart in `README.md` should be **≤10 lines** to execute an example.
* Use **relative paths** only; avoid user-specific or absolute paths.
* Comment code for newcomers; prefer explicit over clever.
* Keep external dependencies minimal and documented.
* Include a **changelog** in `CHANGELOG.md` once the template is public.

### Submission Checklist (Templates)

* [ ] Naming follows kebab-case
* [ ] Required root files present
* [ ] `.github` templates and workflows included
* [ ] Minimal working example runs as written
* [ ] README quickstart tested on a fresh machine

??? example "Example: README skeleton"
````markdown
# Research Project Template

## Quickstart
1. Create a new repo using this template.
2. Create and activate an environment.
3. Run `python src/example.py`.
4. Expected output: a plot saved to `docs/example.png`.

## Customize
- Replace `project_name` and `author` in `pyproject.toml`.
- Update `docs/index.md` navigation.
````

---

## Documentation

Documentation contributions live in shared documentation repositories (e.g., `/docs/`, `/guides/`). Common types:

* Quickstart (minimal, task-oriented)
* Tutorial (longer walkthrough with context)
* Reference (commands, API, options)
* Lesson plan (structured multi-day teaching material)

### File Conventions

* **Format**: Markdown (`.md`) only.

* **Names**: kebab-case, e.g. `ndvi-change-points.md`.

* **Front matter** (YAML):

  ```yaml
  ---
  title: NDVI Change-Points Tutorial
  author: Jane Doe
  date: 2025-09-15
  tags: [tutorial, python, remote-sensing]
  summary: Detect change points in NDVI for post-fire vegetation recovery.
  ---
  ```

* **Headings** (recommended outline):

  1. Introduction (scope and audience)
  2. Prerequisites (software, data, credentials)
  3. Steps (numbered tasks with code + expected output)
  4. Troubleshooting (common errors and fixes)
  5. References (links, citations)

* **Code blocks**: fenced with language hints (` ```python `, ` ```bash `). Show **exact commands**.

* **Figures**: store in a local `images/` folder; reference with relative paths; include **alt text**.

* **Links**: site-relative paths (e.g., `/templates/`, `/lounge/`, `/events/`).

!!! note
Keep paragraphs short. Prefer imperative voice: “Run the script,” “Verify the output.” Define acronyms on first use.

### Authoring Guidelines (Docs)

* Use consistent units (metric preferred) and date format `YYYY-MM-DD`.
* Provide copy-paste blocks for commands and config.
* Indicate expected runtime and resource needs when relevant.
* For external data, include access instructions and license.
* Add a “Last reviewed” date at the bottom of each page.

### Submission Checklist (Docs)

* [ ] Filename in kebab-case; front matter present
* [ ] Intro, prerequisites, steps, troubleshooting, references
* [ ] Code blocks render and run as shown
* [ ] Images have alt text and relative paths
* [ ] Links are site-relative and valid

??? example "Example: Troubleshooting section"
``markdown
## Troubleshooting
- ImportError: `ruptures` not found → run `pip install ruptures` in the active environment.
- Plot not rendering → ensure `matplotlib` backend is available on your platform.
- Path errors → use the provided relative paths; avoid `C:` or absolute POSIX paths.
``

---

## Naming and Branching

* **Repositories**: kebab-case (e.g., `data-template`)
* **Branches**: `type/short-description` (e.g., `feat/new-template`, `fix/readme-typo`)
* **Files**: kebab-case, no spaces (e.g., `ndvi-change-points.md`)
* **Images**: `topic-shortdescription.png` or `.svg`

---

## Submission Process

1. Fork the target repository.
2. Create a branch using the naming convention.
3. Add files and update navigation (if applicable).
4. Run any local checks (lint, tests, link checker).
5. Open a Pull Request with a clear title and short summary of changes.
6. Address reviewer feedback.

!!! tip
If unsure, draft your idea in the Lounge first: `/lounge/`.

---

## Review Standards

* Templates must run as-is with minimal setup.
* Docs must be reproducible on a fresh machine using listed prerequisites.
* Conventions on naming, front matter, links, and structure are required.
* Submissions that fail checks will be returned with requested revisions.

---

## Events and Support

* Monthly community call with demos and Q&A: see `/events/`.
* Questions: open an issue with the `question` label.
* Mentorship: ask for a pairing in `/lounge/`.

---

## Licensing

* Code defaults to **Apache-2.0** unless specified.
* Written content defaults to **CC-BY-4.0**.
* Always cite sources and include data licenses.

---

*Consistency is what makes OASIS usable. Thanks for taking the time to format carefully.*
