![Nachuan.skill · To be anyone, to be better you.](assets/nachuan-first-image.svg)

# Nachuan.skill

> To be anyone, to be better you.

[中文](README.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português](README.pt.md) · [العربية](README.ar.md)

**Distill Everything.skill** is the English name of **Nachuan.skill**.

Nachuan.skill is a universal material-distillation Skill for Claude Code. It turns PDFs, decks, webpages, transcripts, research packs, drafts, and scattered notes into reusable knowledge, structure, and content assets.

It is not a pile of prompts. It is a workflow: scan first, route next, execute with the right pipeline, and keep the output reusable.

---

## Why Nachuan

Nachuan means taking in many streams.

Real work rarely arrives as clean input. It comes as mixed documents, screenshots, slides, links, transcripts, half-written ideas, and fragments. Nachuan.skill first reads what is there, then decides which route makes the material useful.

**To be anyone, to be better you** does not mean copying another person. It means absorbing useful methods, structures, judgments, and expression patterns from many sources so your own work becomes stronger.

---

## Three Highlights

| Highlight | Problem solved | What it feels like |
|---|---|---|
| **Scan before asking** | The user may not know what to ask when the input is messy | It gives a material overview, then 2-4 concrete processing options |
| **Four routed pipelines** | Summary, structure, knowledge, and generation often get mixed together | Each route has a clear goal, output, and next step |
| **Output becomes assets** | Many AI outputs disappear inside one chat | It stores reusable Markdown, tags, wikilinks, and templates |

---

## Four Pipelines

| Path | Name | Use it when | Typical output |
|---|---|---|---|
| **A** | Essence Distillation | You need core claims, judgments, and reusable principles | Executive summary, decision list, principle cards |
| **B** | Structure Decomposition | You need to understand narrative, page, or argument structure | Structure map, expression pattern, reusable framework |
| **C** | Knowledge Extraction | You want to turn material into a long-term knowledge base | Markdown notes, YAML tags, `[[wikilinks]]` |
| **D** | Content Generation | You want new output based on extracted knowledge | Copy, scripts, outlines, explainers, templates, drafts |

Routes can be used alone, in parallel, or in sequence.

---

## Workflow

1. **Drop in material**: documents, links, transcripts, notes, or a mixed pack.
2. **Silent scan**: detect type, scale, structure, keywords, and potential value.
3. **Choose a route**: get a recommended path plus alternatives.
4. **Run the pipeline**: execute A/B/C/D alone, in parallel, or in sequence.
5. **Keep the result**: store it as searchable, linkable, reusable Markdown.

---

## Output Format

- **Markdown** for long-term readability
- **YAML metadata** for classification and automation
- **`[[wikilinks]]`** for Obsidian and graph-style notes
- **Routing logs** to record what path was chosen and why
- **Reusable assets** such as templates, scripts, outlines, and drafts

---

## Install

```bash
npx skills add wilsondd-lab/nachuan
```

Manual install:

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/wilsondd-lab/nachuan.git
```

---

## Origin

Nachuan.skill was inspired by Huashu's Nuwa Skill. The key lesson was that a Skill can be more than a prompt: it can turn experience, judgment, route selection, and workflow into a reusable system.

Built from that inspiration, Nachuan.skill went through four or five practical iterations and moved closer to real frontline knowledge work.

---

## License

MIT © Wilson
