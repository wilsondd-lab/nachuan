# 纳川 (Nachuan) · Content Acquisition Hub

> "The sea never refuses water, therefore it becomes great." — Guanzi

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-6C4DFF)](https://claude.com/code)

**纳川** is a Claude Code Skill that serves as the **single entry point** for all your content processing tasks.

Drop in any content (PPT, PDF, transcript, competitor doc, training material, webpage…) → 纳川 scans for key signals → presents 2-4 opinionated path recommendations (multiple choice, not open-ended) → you pick one → auto-dispatches to downstream pipelines → knowledge lands in your Obsidian vault.

---

## Why "Nachuan" (纳川)?

From the ancient Chinese text *Guanzi*: "The sea never refuses water, therefore it becomes great."

All content flows in like rivers to the sea. 纳川 sorts them — which should be distilled into a persona, which decomposed into frameworks, which extracted into knowledge notes, and which generated into new content.

---

## Installation

```bash
npx skills add wilsondd-lab/nachuan
```

Or manually:

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/wilsondd-lab/nachuan.git
```

**Prerequisite**: An Obsidian vault (or any Markdown folder) as the knowledge base backend. See [Obsidian Vault Setup Guide](references/obsidian-vault-setup.md).

---

## What It Does

Four processing pipelines covering all content scenarios:

| Path | Name | Input → Output | Use When |
|------|------|---------------|----------|
| **A** | Persona Distillation | Transcripts/talks → mental models + expression DNA + SKILL.md | "Extract this person's thinking style" |
| **B** | Structural Decomposition | PPTs → narrative frameworks + page patterns; any content → why it works | "How is this deck built?" / "Why did this go viral?" |
| **C** | Knowledge Extraction | Any document → Obsidian notes + wikilinks network | "Extract the insights into my knowledge base" |
| **D** | Content Generation | Vault knowledge + personas → scripts/copy/templates | "Write YY in XX's style, using these knowledge points" |

---

## Usage

### Basic

In Claude Code, drop any content and say anything that implies analysis/extraction:

```
"What's in this competitor's PPT?"
"Break down this training material"
"What's unique about XX's speaking style in this transcript?"
"Distill Yulinjia's thinking"
"Extract insights from this white paper into my vault"
```

纳川 scans first, then gives you choices:

```
Scanned: 30-page competitor nursing-care PPT. 12 related notes in vault.

A 🟢 Full Decomp (Recommended) — Structure + Knowledge in parallel
B 🟡 Knowledge Only — Extract insights to vault
C 🔵 Structure Only — Narrative frameworks and patterns
D ⚪ Custom
```

You pick, 纳川 executes.

### Distill a Persona

Say "Distill [name]" and 纳川 runs a dedicated interview:

```
Got it. Distilling Yulinjia. First, scope:

A 🟢 Full Portrait (Recommended) — Complete 6-dimension extraction
B 🟡 Specific Dimension — Expression / Decision-making / Content creation
C 🔵 Quick Distill — Highlights only
D ⚪ Custom
```

---

## Architecture

```
Any Content (PPT/PDF/Transcript/Webpage/Notes/...)
              │
              ▼
    ┌─────────────────┐
    │   Scan Layer     │  ← Identify type, scale, key signals
    │   Vault Search   │  ← Find existing knowledge for linking
    └───────┬─────────┘
            │
    ┌───────▼─────────┐
    │  Interview Layer │  ← Present 2-4 path options (multiple choice)
    │  User Decides    │  ← Pick A/B/C/D
    └───────┬─────────┘
            │
    ┌───────▼─────────┐
    │  Dispatch Layer  │  ← Single / Dual-parallel / Triple-parallel / Sequential
    └───┬───┬───┬─────┘
        │   │   │
   ┌────▼┐ ┌▼──┐ ┌▼────┐ ┌────┐
   │PathA│ │PathB│ │PathC│ │PathD│
   │Distil│ │Struct│ │Extract│ │Gen │
   └──┬─┘ └─┬──┘ └──┬──┘ └──┬─┘
      │      │       │       │
      ▼      ▼       ▼       ▼
  ┌────────────────────────────────┐
  │         Obsidian Vault          │
  │  wikilinks · tags · Git-ready   │
  └────────────────────────────────┘
```

---

## Knowledge Storage

纳川 uses **Obsidian** for knowledge management — no cloud lock-in:

- 📝 **Pure Markdown files** — readable forever
- 🔗 **wikilinks** (`[[note-name]]`) — explicit knowledge networks
- 🏷️ **YAML frontmatter tags** — organized and searchable
- 💾 **Git-friendly** — version control your knowledge
- 🆓 **Obsidian is free for personal use**

Example knowledge note:

```markdown
---
tags: [nachuan, insurance, product-design, Path-C]
created: 2026-06-18
source: "[[competitor-analysis-nursing-care-20260618]]"
related: [[taibao-yihu], [[long-term-care-policy]]
---

# Competitor X uses dual-primary-insurance structure

Competitor X's product differs from Taibao Yihu Tiannian:
uses annuity + nursing care as two independent primary insurances...
```

---

## Built-in Taxonomies

纳川 ships with mature taxonomies for **insurance/sales-presentation** content:

- **7 Narrative Frameworks**: Grand Launch / Problem-Solution / Policy-Driven / Coach Mode / Doubt-Destruction / Agent Mindset Upgrade / Shareholder Seat
- **20 Page Expression Patterns**: Cover, Data Impact, Concept Framing, Product Explanation, Comparison, Benefits & Services…
- **Cross-domain**: The framework methodology is domain-agnostic; only the label taxonomy needs adaptation for new domains

---

## vs. Traditional RAG

| | RAG (Retrieval-Augmented Generation) | 纳川 |
|---|---|---|
| Knowledge granularity | Vector chunks, lost context | Full notes + wikilinks network |
| Knowledge organization | Auto-chunked, uncontrollable | Human-confirmed notes, clear structure |
| Storage | Vector DB (platform-bound) | Local Markdown (any editor) |
| Linking | Similarity scores, opaque | Explicit wikilinks, traceable |
| Maintenance | Automatic but hard to clean | Manual but quality-controlled |

---

## Repo Structure

```
nachuan/
├── SKILL.md                           # Main orchestration (for Claude)
├── README.md                          # This file (for humans)
├── README.en.md                       # English version
├── LICENSE                            # MIT
├── references/
│   ├── interview-templates.md
│   ├── routing-matrix.md
│   ├── path-a-persona-distillation.md
│   ├── path-b-structural-decomposition.md
│   ├── path-c-knowledge-extraction.md
│   ├── path-d-content-generation.md
│   ├── obsidian-vault-setup.md
│   └── storage-rules.md
└── templates/
    ├── task-card.md
    ├── routing-decision-log.md
    └── learning-report.md
```

---

## Credit

- Persona distillation methodology inherited from [Nuwa · Skill Creator](https://github.com/alchaincyf/nuwa-skill) (by Huashu)
- PPT structural decomposition inspired by Claude PPT Engine
- Content generation pipeline based on insurance-content-transformer and [humanizer](https://github.com/blader/humanizer)

---

## License

MIT © Wilson