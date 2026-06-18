# 纳川 · 内容获取中间层

> 《管子·形势解》"海不辞水，故能成其大。"

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-6C4DFF)](https://claude.com/code)

**纳川** 是一个 Claude Code Skill，作为你所有内容处理任务的**唯一入口**。

丢入任何内容（PPT、PDF、转录、竞品文档、培训材料、网页……）→ 纳川扫描关键信号 → 给你 2-4 个倾向性路径建议（选择题，不是开放题）→ 你选一个 → 自动调度到下游管线 → 知识归位到 Obsidian vault。

---

## 先说源头：来自花叔的启蒙

纳川的起点，来自花叔 [女娲 · Skill 造人术](https://github.com/alchaincyf/nuwa-skill) 的启蒙。

花叔让我意识到：Skill 不只是提示词，也不是一堆技巧的拼贴。一个真正有生命力的 Skill，应该能把一个人的判断、经验、表达习惯和工作流，沉淀成可复用、可传承、可继续生长的系统。

如果说女娲关注的是"把一个人炼成可调用的人格 Skill"，纳川关注的就是另一件事：**让任何内容进入正确的加工管线**。它先分流，再调度，再沉淀，让散落的材料变成可搜索、可链接、可再创作的知识资产。

---

## 纳川的特性

| 特性 | 说明 |
|------|------|
| **唯一入口** | 不再为每种材料临时想 prompt。PPT、PDF、转录、网页、竞品文档都先交给纳川扫描。 |
| **选择题式访谈** | 每次必问，但只问选择题。纳川给出 2-4 个倾向性路径，用户只需要做决策。 |
| **四管线调度** | 人物蒸馏、结构拆解、知识提取、内容生成，可以单跑、并行，也可以串联。 |
| **本地知识沉淀** | 结果进入 Obsidian vault，用 Markdown、wikilinks、tags 形成长期可维护的知识网络。 |
| **面向再创作** | 不只是总结材料，而是把内容拆成以后能调用、融合、生成的素材和方法。 |

---

## 为什么叫纳川？

《管子·形势解》："海不辞水，故能成其大。"

所有内容如百川汇入大海，纳川负责分拣——哪些该蒸馏成人格，哪些该拆解成框架，哪些该提取成知识笔记，哪些该直接生成内容。

---

## 安装

```bash
npx skills add wilsondd-lab/nachuan
```

或手动：

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/wilsondd-lab/nachuan.git
```

**前置依赖**：需要一个 Obsidian vault（或任意 Markdown 文件夹）作为知识库后端。详见 [Obsidian Vault 设置指南](references/obsidian-vault-setup.md)。

---

## 能做什么

纳川有四条加工管线，覆盖内容处理的全部场景：

| 路径 | 名称 | 输入 → 产出 | 适用于 |
|------|------|------------|--------|
| **A** | 人物蒸馏 | 转录/演讲 → 心智模型+表达DNA+SKILL.md | "帮我把这个人的思维方式炼出来" |
| **B** | 结构拆解 | PPT → 叙事框架+页面表达模式；高绩效内容 → 为什么有效 | "这组PPT是怎么搭的？" / "这篇为什么爆？" |
| **C** | 知识提取 | 任何文档 → Obsidian 知识笔记 + wikilinks 关联网络 | "把里面的干货捞出来，存进我的知识库" |
| **D** | 内容生成 | vault知识 + 人格 → 话术/文案/脚本 | "用 XX 的风格，基于这些知识点，写一篇 YY" |

---

## 怎么用

### 基础用法

在 Claude Code 中，丢入任何内容，说任何表示"分析/提取/拆解"的话：

```
"帮我看看这个竞品PPT里有什么"
"拆一下这份培训材料"
"这段转录里XX的讲法有什么特点"
"蒸馏虞林佳"
"这份白皮书捞干货存我知识库"
```

纳川会先扫描内容，然后给你选择题：

```
扫了一遍：30 页竞品护理险 PPT。vault 有 12 条相关笔记可做对比。

A 🟢 全拆（推荐）— 结构拆解 + 知识提取并行
B 🟡 仅捞知识 — 竞品信息入 vault
C 🔵 仅拆结构 — 叙事框架和表达手法
D ⚪ 自定义
```

你选一个，纳川自动执行。

### 蒸馏人物

说"蒸馏 XX"，纳川会走专属访谈：

```
收到，蒸馏虞林佳。先确认范围：

A 🟢 全面画像（推荐）— 六维全采，完整 SKILL.md
B 🟡 特定维度 — 表达力 / 决策力 / 内容创作
C 🔵 快速蒸馏 — 仅 highlights
D ⚪ 自定义
```

---

## 架构

```
任何内容（PPT/PDF/转录/网页/笔记/...）
              │
              ▼
    ┌─────────────────┐
    │   纳川 · 扫描层   │  ← 识别类型、规模、关键信号
    │    vault 预搜     │  ← 搜索已有知识，准备关联
    └───────┬─────────┘
            │
    ┌───────▼─────────┐
    │   纳川 · 访谈层   │  ← 给 2-4 个倾向性路径建议（选择题）
    │   用户决策        │  ← 选 A/B/C/D
    └───────┬─────────┘
            │
    ┌───────▼─────────┐
    │   纳川 · 调度层   │  ← 单/双并行/三并行/串联
    └───┬───┬───┬─────┘
        │   │   │
   ┌────▼┐ ┌▼──┐ ┌▼────┐ ┌────┐
   │PathA│ │PathB│ │PathC│ │PathD│
   │蒸馏 │ │拆解│ │提取 │ │生成 │
   └──┬─┘ └─┬──┘ └──┬──┘ └──┬─┘
      │      │       │       │
      ▼      ▼       ▼       ▼
  ┌────────────────────────────────┐
  │         Obsidian Vault          │
  │  wikilinks 关联 · tags 分类     │
  │  Git 版本控制 · 本地优先        │
  └────────────────────────────────┘
```

---

## 知识存储

纳川用 **Obsidian** 管理知识，不绑定任何云服务：

- 📝 **纯 Markdown 文件**，未来永远可读
- 🔗 **wikilinks** (`[[笔记名]]`) 自动形成知识网络
- 🏷️ **YAML frontmatter tags** 分类检索
- 💾 **Git 友好**，可推到私有仓库备份
- 🆓 **Obsidian 个人使用完全免费**

每条知识记忆长这样：

```markdown
---
tags: [纳川, 保险, 产品设计, Path-C]
created: 2026-06-18
source: "[[竞品分析_护理险_20260618]]"
related: [[太保颐护添年]], [[长护险政策梳理]]
---

# 竞品X的护理险采用"年金+护理"双主险结构

竞品 X 的产品设计与太保颐护添年不同：
采用养老年金和护理险作为两个独立主险...
```

---

## 适用场景

| 你是谁 | 纳川能帮你 |
|--------|-----------|
| 🧠 知识工作者 | 把散落的白皮书/研报/长文系统化提取为可检索的知识网络 |
| 📊 商业分析师 | 竞品 PPT/文档 → 结构化情报 + 对比分析 |
| 🎤 内容创作者 | 蒸馏优秀创作者的心智模型，融合生成新内容 |
| 📚 培训师 | 培训材料 → 知识点提取 → 用专家人格生成一线话术 |
| 🏢 保险/金融从业者 | 产说会 PPT 拆解、竞品分析、产品话术生成（内置保险领域分类体系） |

---

## 内置分类体系

纳川为**保险/产说会**领域内置了成熟的分类体系：

- **7 种叙事框架**：大戏型 / 问题解决型 / 政策驱动型 / 教练型 / 疑虑打破型 / 代理人认知升级型 / 股东席位型
- **20 种页面表达模式**：封面、数据冲击、理念铺垫、产品讲解、对比、权益服务……
- **跨领域复用**：框架方法论是领域无关的，新领域只需新建分类标签

---

## 与传统 RAG 的区别

| | RAG（检索增强生成） | 纳川 |
|---|---|---|
| 知识粒度 | 向量片段，丢失上下文 | 整篇笔记 + wikilinks 关系网络 |
| 知识组织 | 自动分块，不可控 | 人工确认的笔记，结构清晰 |
| 存储 | 向量数据库（绑定平台） | 本地 Markdown（任何编辑器可读） |
| 关联 | 相似度计算，不可见 | wikilinks 显式关联，可追溯 |
| 维护 | 自动但难以清理 | 手动但质量可控 |

---

## 文件结构

```
nachuan/
├── SKILL.md                           # 主编排文件（给 Claude 读）
├── README.md                          # 本文件（给人读）
├── README.en.md                       # English version
├── LICENSE                            # MIT
├── references/
│   ├── interview-templates.md         # 11 种场景模板
│   ├── routing-matrix.md              # 完整路由矩阵
│   ├── path-a-persona-distillation.md # Path A 调度
│   ├── path-b-structural-decomposition.md # Path B 调度
│   ├── path-c-knowledge-extraction.md # Path C 协议（Obsidian 版）
│   ├── path-d-content-generation.md   # Path D 调度
│   ├── obsidian-vault-setup.md        # ★ Obsidian vault 设置指南
│   └── storage-rules.md               # 存储规则
└── templates/
    ├── task-card.md
    ├── routing-decision-log.md
    └── learning-report.md
```

---

## Credit

- 人物蒸馏方法论继承自 [女娲 · Skill 造人术](https://github.com/alchaincyf/nuwa-skill)（by 花叔）
- PPT 结构拆解借鉴自 Claude PPT Engine
- 内容生成管线基于 [insurance-content-transformer](https://github.com/) 和 [humanizer](https://github.com/blader/humanizer)

---

## License

MIT © Wilson