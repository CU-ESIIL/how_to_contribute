---
title: Starter Kit
description: Copy-paste boilerplates for front matter, PR templates, and CI link checking.
---

# Starter Kit

## Front matter boilerplate
```yaml
---
title: TITLE
author: Your Name
date: YYYY-MM-DD
tags: [choose-from-/how_to_contribute/tag-vocab/]
summary: One-sentence description.
---
```

## Minimal README skeleton (template repos)

```markdown
# Project Template

## Quickstart
1. Create a repo using this template.
2. Create and activate an environment.
3. Run `python src/example.py`.

## Customize
- Replace names/placeholders in config files.
- Update docs navigation.
```

## PR template (`.github/PULL_REQUEST_TEMPLATE.md`)

```markdown
## Summary
- What changed and why

## Checklist
- [ ] Follows naming conventions
- [ ] Docs/examples updated
- [ ] Links validated
```

## Link checker workflow (`.github/workflows/link-check.yml`)

```yaml
name: link-check
on: [push, pull_request]
jobs:
  linkchecker:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: lycheeverse/lychee-action@v1
        with:
          args: --verbose --no-progress --exclude-mail --accept 200,429 "**/*.md"
```

