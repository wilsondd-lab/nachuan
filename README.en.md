# Nachuan · Distill Everything

> The sea never refuses water, therefore it becomes great.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-6C4DFF)](https://claude.com/code)

**Nachuan** is a Claude Code Skill for turning messy inputs into reusable knowledge, structure, and content assets.

Its English name is **Distill Everything**.

---

## Three Highlights

### 1. Scan Before Asking

Nachuan first reads the material type, scale, structure, keywords, and existing knowledge context. Then it asks with 2-4 clear options, not an open-ended prompt.

### 2. Route, Don't Stack Prompts

Different materials need different workflows. Nachuan routes work into four general pipelines: essence distillation, structure decomposition, knowledge extraction, and content generation.

### 3. Turn Output Into Assets

The result is not a one-off summary. Nachuan stores reusable notes, patterns, decisions, and generated assets as Markdown, ready for linking, search, and future reuse.

---

## Pipelines

| Path | Name | Input | Output |
|------|------|-------|--------|
| **A** | Essence Distillation | Any material | Core claims, judgments, reusable principles |
| **B** | Structure Decomposition | Decks, essays, webpages, proposals | Narrative structure, expression patterns, reusable frameworks |
| **C** | Knowledge Extraction | Documents, reports, notes, source packs | Markdown notes, wikilinks, tags |
| **D** | Content Generation | Extracted knowledge and structures | Copy, scripts, explainers, templates, drafts |

---

## Install

```bash
npx skills add wilsondd-lab/nachuan
```

Or manually:

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/wilsondd-lab/nachuan.git
```

---

## Storage

Nachuan uses an Obsidian vault or any Markdown folder as its local knowledge backend:

- **Plain Markdown** for long-term readability
- **wikilinks** with `[[note-name]]`
- **YAML tags** for classification
- **Git-friendly** local storage

---

## License

MIT © Wilson
