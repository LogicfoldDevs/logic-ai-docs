# LogicAI Documentation

This repo contains the documentation and changelog for [LogicAI](https://www.logicfold.com) — an AI assistant for Salesforce.

## Structure

```
docs/           Product documentation (rendered at /docs)
changelog/      Release notes (rendered at /changelog)
```

## How to update

1. Edit or add markdown files in `docs/` or `changelog/`
2. Commit and push to `main`
3. The website automatically picks up changes

## Docs

Each file in `docs/` is a page. Files are ordered by the `order` field in frontmatter. Example:

```markdown
---
title: Getting Started
order: 1
---

Your content here...
```

## Changelog

Each file in `changelog/` is a release entry. Name files by date: `YYYY-MM-DD.md`. Example:

```markdown
---
title: v1.42 - Agent Memory and Streaming
date: 2026-05-27
---

Your release notes here...
```
