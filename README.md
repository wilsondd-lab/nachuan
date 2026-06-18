# 纳川.Skill · Distill Everything.Skill

> 海不辞水，故能成其大。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-6C4DFF)](https://claude.com/code)

**纳川.Skill** 是一个 Claude Code Skill，也是一个内容处理入口：把任何材料丢进来，它先扫描、再分流、再沉淀，把混乱输入变成可复用的知识、结构和表达资产。

英文名叫 **Distill Everything.Skill**。

---

## 三个亮点

### 1. 先扫再问

纳川不会一上来就让你描述需求。它先读取材料类型、规模、结构、关键词和已有知识，再给出 2-4 个明确选项。你做选择，它负责拆解路径。

### 2. 路由而不是堆提示词

不同材料需要不同处理方式。纳川把任务拆成四条通用管线：精华萃取、结构拆解、知识提取、内容生成。它可以单跑、并行，也可以串联。

### 3. 结果沉淀为资产

输出不是一次性摘要。纳川会把结论写成 Markdown 笔记、结构模式、任务记录和生成素材，放进本地知识库，方便后续检索、链接和再创作。

---

## 来源与定位

纳川.Skill 的启蒙来自花叔的女娲 Skill。它让我意识到：Skill 不只是提示词，也不只是技巧合集，而是可以把经验、判断和工作流沉淀成可调用的系统。

在这个启发之上，纳川.Skill 结合真实工作场景迭代了四五轮，逐渐把重点收敛到更贴近一线需要的前段问题：材料很多、目标还不清楚、用户需要先知道“该怎么处理”。所以它不绑定任何行业，也不预设某种内容风格，而是先判断输入，再选择加工管线。

---

## 能处理什么

PPT、PDF、网页、转录、长文、培训资料、竞品文档、会议记录、研究材料、散装笔记、多个文件混合输入。

你可以这样说：

```text
帮我看看这个文档里有什么
把这份 PPT 拆一下
提取里面可以复用的知识点
把这些材料整理成内容资产
先分析，再给我几个处理选项
```

---

## 四条管线

| 路径 | 名称 | 输入 | 产出 |
|------|------|------|------|
| **A** | 精华萃取 | 任何材料 | 核心观点、关键判断、可复用规律 |
| **B** | 结构拆解 | PPT、长文、网页、方案 | 叙事结构、表达模式、内容框架 |
| **C** | 知识提取 | 文档、报告、记录、资料包 | Markdown 知识笔记、wikilinks、标签 |
| **D** | 内容生成 | 已提取的知识与结构 | 文案、脚本、说明、模板、草稿 |

---

## 工作方式

```text
任何内容
  ↓
静默扫描：类型 / 规模 / 结构 / 关键词 / 已有知识
  ↓
选择题访谈：给出 2-4 个推荐处理路径
  ↓
管线调度：A / B / C / D，可单跑、并行、串联
  ↓
本地沉淀：Markdown 笔记、结构资产、生成结果索引
```

纳川的铁律：**每次必问，但只问选择题。**

---

## 安装

```bash
npx skills add wilsondd-lab/nachuan
```

或手动安装：

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/wilsondd-lab/nachuan.git
```

---

## 知识库后端

纳川默认使用 Obsidian vault 或任意 Markdown 文件夹作为知识库后端：

- **纯 Markdown**：长期可读，不绑定平台
- **wikilinks**：用 `[[笔记名]]` 建立显式关联
- **YAML tags**：按主题、来源、路径分类
- **Git 友好**：可以进入版本控制或私有备份

推荐结构：

```text
your-vault/
└── 纳川/
    ├── 学习报告/
    ├── 知识单元/
    ├── 精华萃取/
    ├── 结构拆解/
    ├── 生成内容/
    └── 纳川_MOC.md
```

---

## 示例输出

```markdown
---
tags: [纳川, 知识单元, Path-C, 主题标签]
created: 2026-06-18
source: "[[来源材料_学习报告]]"
related:
  - "[[已有相关笔记]]"
---

# 一个可复用的知识点标题

这里用 2-5 句记录事实、判断、机制或方法，并说明它未来可以在哪些场景复用。

**来源**：第 N 页 / 第 N 段
**可复用场景**：内容生成、方案写作、研究整理、知识复盘
```

---

## 文件结构

```text
nachuan/
├── SKILL.md
├── README.md
├── README.en.md
├── LICENSE
├── references/
│   ├── interview-templates.md
│   ├── routing-matrix.md
│   ├── path-a-essence-distillation.md
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

## License

MIT © Wilson
