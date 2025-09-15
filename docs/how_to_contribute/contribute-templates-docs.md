---
title: Templates & Documentation Contributions
description: Author requirements for OASIS templates and shared documentation repos.
---

# Templates & Documentation Contributions

OASIS welcomes two closely related contribution types:

- **Templates** provide reusable repository scaffolds that accelerate new projects.
- **Documentation** captures formal guides, tutorials, and references maintained in shared docs repos.

Use this guide alongside the [Starter Kit](/how_to_contribute/starter-kit/) to assemble files quickly and stay aligned with review expectations.

## Required files
- `README.md` summarizing purpose, quickstart, and customization guidance.
- `LICENSE` using Apache-2.0 unless another OSI license is justified in the README.
- `CONTRIBUTING.md` describing how to file issues and open PRs.
- `CODE_OF_CONDUCT.md` referencing the OASIS code of conduct.
- GitHub metadata under `.github/`:
  - issue templates for bugs and feature requests
  - `.github/PULL_REQUEST_TEMPLATE.md`
  - `.github/workflows/` with at least a link checker or primary CI job
- Optional but recommended: `CHANGELOG.md` once the repo is public.

## Recommended repository structure
- `src/` or `notebooks/` for runnable examples.
- `data/` with placeholder files plus a `README` describing expected contents.
- `docs/` for extended guides and decision records.
- `tests/` or `examples/` when relevant.
- `images/` for screenshots or diagrams referenced in Markdown.

!!! tip
    Ship a minimal working example that new users can run in under five minutes. It doubles as a smoke test for reviewers.

## Authoring rules
- Favor relative paths and explicit configuration over environment-specific shortcuts.
- Keep dependency lists short and document how to install them.
- Write imperatively (“Run the script,” “Verify the output”) and define acronyms on first use.
- Include last-reviewed dates at the end of long-form docs.
- Use site-relative links (for example, `/how_to_contribute/tag-vocab/`).

??? example "README quickstart excerpt"
    ```markdown
    # Project Template

    ## Quickstart
    1. Create a repository from this template.
    2. Set up the environment with `uv sync`.
    3. Run `python src/example.py` to produce `docs/example.png`.

    ## Customize
    - Update the project name fields in `pyproject.toml`.
    - Replace this README section with your workflow.
    ```

## Submission checklist
- [ ] Repository name and files use kebab-case (no spaces).
- [ ] Required files and GitHub workflows are present.
- [ ] Minimal example runs on a clean environment.
- [ ] README quickstart tested line by line.
- [ ] Docs include front matter and last-reviewed dates where applicable.
- [ ] Links resolve and are relative within the site.

## Naming and branching conventions
- Repositories: `topic-template`, `workflow-docs`, or similar kebab-case names.
- Branches: `type/short-description` (for example, `feat/new-template` or `fix/typo-readme`).
- Images and assets: `topic-shortdescription.png` or `.svg`.
- Commits: follow `feat`, `fix`, `docs`, etc., with concise summaries.

## Submission process
1. Fork the relevant OASIS repository.
2. Create a branch using the naming convention above.
3. Add or update files, including navigation entries for documentation sites.
4. Run local checks (tests, linting, link checking) before opening a PR.
5. Open a pull request that summarizes scope, testing, and follow-up actions.
6. Respond to reviewer feedback and rerun checks after changes.

## Review standards
- Templates must clone and run without additional configuration beyond documented steps.
- Documentation must contain full prerequisites, runnable commands, and accessible images.
- Naming, front matter, and navigation updates must match this guide.
- Licensing statements must be explicit and compatible with dependencies or data sources.
- Reviewers will request revisions when steps are ambiguous or code is not reproducible.

## Licensing
- Code defaults to **Apache-2.0** unless a different OSI-approved license is justified in the README.
- Narrative content defaults to **CC-BY-4.0**.
- Cite external data, images, or text and include source licenses when applicable.

## Events and support
- Join the monthly community call for demos and Q&A (listed on `/events/`).
- Ask quick questions in the Lounge before drafting a PR.
- Request pairing or review support via a GitHub issue labeled `help-wanted`.
- Track recognition, spotlights, and maintenance expectations on the [Recognition & Maintenance](/how_to_contribute/recognition/) page.
