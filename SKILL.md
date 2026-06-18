---
name: nachuan
description: |
  纳川 · 内容获取中间层。万物内容汇入 → 智能扫描分拣 → 四条管线加工 → 各归其位（Obsidian vault / 本地 / 项目记忆）。
  触发词：「拆解」「分析」「提取」「蒸馏」「融合」「这个 PPT/文档/转录里有什么」「帮我看看这个」。
  铁律：每次必问，但只问选择题。扫描内容后给倾向性建议，用户决策。
version: 1.0.0
tags: [content-acquisition, meta-routing, obsidian-integration, multi-agent, 纳川]
related_skills: [persona-fusion, content-expression-analysis, insurance-content-transformer, humanizer]
---

# 纳川 · 内容获取中间层

《管子·形势解》"海不辞水，故能成其大。"

**纳川** 是内容处理体系的唯一入口。任何内容丢入 → 扫描关键信号 → 给出 2-4 个倾向性路径建议（选择题）→ 用户决策 → 调度到下游管线执行 → 结果按合约存入 Obsidian vault / 本地 / 项目记忆。

本版本使用 **Obsidian** 作为知识库后端。所有知识记忆以 Markdown 文件存储在 Obsidian vault 中，通过 wikilinks (`[[note]]`) 建立关联，通过 YAML frontmatter tags 进行分类。

---

## 一、四条管线

| 路径 | 名称 | 做什么 | 下游系统 |
|------|------|--------|----------|
| **A** | 人物蒸馏 | 提炼心智模型、表达DNA、决策启发式 | Persona-Fusion（女娲方法论） |
| **B** | 结构拆解 | PPT→三层拆解(视觉+叙事+表达)；高绩效内容→逆向工程 | PPT Engine / content-expression-analysis |
| **C** | 知识提取 | 逐页/逐段提取知识点 → Obsidian vault notes + wikilinks | 知识提取协议（纳川内置） |
| **D** | 内容生成 | 基于 vault 知识 + 已蒸馏人格 → 话术/文案/脚本 | insurance-content-transformer + humanizer |

---

## 二、前置要求

### Obsidian Vault 设置

纳川需要一个 Obsidian vault 来存储知识。推荐结构：

```
your-vault/
├── 纳川/                        # 纳川知识根目录
│   ├── 学习报告/                 # Path C 产出的学习报告
│   ├── 知识记忆/                 # Path C 产出的独立知识笔记
│   │   ├── 保险/
│   │   ├── 养老/
│   │   └── ...
│   ├── 人物精华/                 # Path A 蒸馏产出
│   ├── 结构拆解/                 # Path B 拆解摘要
│   ├── 生成内容/                 # Path D 产出索引
│   └── 纳川_MOC.md              # 纳川总索引（Map of Content）
├── 模板/                        # Obsidian 模板
│   ├── 知识记忆模板.md
│   └── 学习报告模板.md
└── ...
```

### 纳川 Vault 搜索

在开始任何提取前，先搜索 vault 中已有知识：

```bash
# 用 grep 搜索 vault 中的已有内容
grep -rl "关键词" your-vault/纳川/

# 或在 Obsidian 中直接搜索
```

详见 `references/obsidian-vault-setup.md`。

---

## 三、快速路由

### 按内容类型

| 输入 | 默认推荐 | 说明 |
|------|----------|------|
| PPT（无讲稿） | B + C 并行 | 全拆：结构 + 知识 |
| PPT（有讲稿+演讲者） | A + B + C 并行 | 三线全开 |
| 转录/演讲（单一人物） | A + C 并行 | 蒸馏 + 捞知识 |
| 竞品 PPT/文档 | C + B 并行 | 情报 + 结构 |
| 培训材料 | C → D 串联 | 先提取再生成 |
| PDF/报告/白皮书 | C | 深度知识提取 |
| 网页/链接 | 先 fetch → 按类型匹配 | — |
| 混合批量 | 逐文件分类 → 并行 | — |
| 散装笔记 | 整理 + C | 先结构化再提取 |
| 会议记录（多人） | C | 提取决策+知识点 |
| 对比分析（2+ 份） | B/C + 对比维度 | 各自拆解并排对比 |

### 按用户指令

| 指令 | 行为 |
|------|------|
| "蒸馏 XX" | 走蒸馏专属访谈（范围→用途→素材），不走访谈模板 |
| "融合 XX 和 YY" | 先蒸馏缺失的人格，再融合 |
| "快 / 全拆 / 都要" | 跳 Step 1 访谈，直接全扇出 |

---

## 四、访谈流程

```
Step 0: 静默扫描
  ├─ 识别文件类型、规模、关键信号
  ├─ vault 预搜相关笔记（grep -rl）
  └─ 匹配场景模板（见 references/interview-templates.md）

Step 1: 扫描结论 + 选项（选择题）
  ├─ 一句话总结扫描发现
  ├─ A 🟢 推荐路径 — 理由
  ├─ B 🟡 备选路径 — 理由
  ├─ C 🔵 更轻路径 — 理由
  └─ D ⚪ 自定义

Step 2: 补充确认（按需，最多 1 题）
  └─ vault 关联范围 / 领域确认 / 自定义路径指定

Step 3: 执行完成 → vault 写入确认（选择题）
  └─ 展示预览 → 用户选：全部 / 仅知识 / 仅框架 / 暂不
```

**设计原则**：
- 先扫再问，给倾向性建议
- 每个选项是完整路径组合，用户只选不做开放题
- 第一个选项永远是推荐项
- 蒸馏不走访谈模板，走专属访谈

---

## 五、执行模式

### 单路径
用户目标明确且单一（"只捞知识"）→ 一条 sub-agent

### 双并行（最常见）
B + C（PPT 全拆）或 A + C（蒸馏+知识）→ 两条 sub-agent 并发

### 三并行
A + B + C（PPT 有讲稿 + 演讲者）→ 三条 sub-agent 并发，限 3 条

### 串联
C → D（培训材料：先提取知识入 vault，再生成话术）→ D 依赖 C 的 vault 输出

---

## 六、Obsidian Vault 写入合约

### 四条路径各存什么

| 路径 | 存入 Obsidian Vault | 存本地磁盘（不入 vault） |
|------|---------------------|--------------------------|
| A · 蒸馏 | 素材索引 + 精华摘要（≤500字）+ Skill引用 + 可复用规律 | 原始转录、完整SKILL.md、六维调研文档 |
| B · 结构拆解 | 拆解索引 + 框架摘要 + 模式索引 + 可复用规律 | 完整框架分析.md、表达模式库.md、图片素材 |
| C · 知识提取 | 学习报告 + N条知识笔记 + wikilinks（`[[note]]`） | 完整学习报告.md、逐页笔记 |
| D · 内容生成 | 生成品索引 + 可复用话术模板 | 生成的全文 |

### Vault 笔记格式

每条知识记忆是一个独立 `.md` 文件：

```markdown
---
tags: [纳川, 保险, 产品设计, Path-C]
created: 2026-06-18
source: "[[竞品分析_护理险_20260618]]"
related: [[太保颐护添年]], [[长护险政策梳理]]
---

# [笔记标题：一句话概括知识点]

[2-5 句展开：关键事实、数据、机制、背景]

**来源**：第 N 页
**可复用场景**：[在什么情况下有用]
```

### 写入闸门

每次写入 vault 前：展示预览 → 用户选择题确认 → 执行。

详见 `references/obsidian-vault-setup.md`。

---

## 七、完整示例

### 示例 1：竞品 PPT 全拆

```
用户：丢了一份竞品护理险 PPT（30页）

纳川 Step 0（静默）：
  - .pptx，30页，保险/护理险
  - vault 预搜：12 条护理险相关笔记

纳川 Step 1：
  "扫了一遍：30 页竞品护理险 PPT。vault 有 12 条护理险笔记可做对比。

  A 🟢 全拆（推荐）— 结构拆解 + 知识提取并行
  B 🟡 仅捞知识 — 竞品信息入 vault
  C 🔵 仅拆结构 — 叙事框架和表达手法
  D ⚪ 自定义"

用户选 A

纳川：
  → Sub-agent 1: Path B1 — 三层拆解
  → Sub-agent 2: Path C  — 逐页提取 + wikilinks 到已有笔记
  → 两者并行

执行完成：
  "B 产出：1 条拆解索引 + 2 条框架摘要 + 1 条模式索引
   C 产出：1 份学习报告 + 18 条知识笔记 + 6 个 wikilinks
   完整分析：~/Documents/Claude ppt engine/02_拆解沉淀/竞品_护理险_30p/
   写入 vault？"

用户选"全部写入" → 笔记写入 Obsidian vault → 完成
```

### 示例 2：蒸馏人物

```
用户："蒸馏虞林佳"

纳川 Step 1（蒸馏专属访谈）：
  "收到，蒸馏虞林佳。

  A 🟢 全面画像（推荐）— 六维全采
  B 🟡 特定维度 — 表达力 / 决策力 / 内容创作
  C 🔵 快速蒸馏 — 仅 highlights
  D ⚪ 自定义"

用户选 A → 选 B（用途：角色扮演）→ 选 A（全部纳入本地 17 份素材）

纳川：
  → 调度 Persona-Fusion Phase 1
  → 六维采集 → 三重验证 → SKILL.md → highlights → vault 精华笔记
  → vault 写入确认 → 完成
```

---

## 八、参考文件索引

| 文件 | 内容 |
|------|------|
| `references/interview-templates.md` | 11 种场景模板 + 2 种蒸馏场景 + 选项生成逻辑 |
| `references/routing-matrix.md` | 完整路由矩阵 |
| `references/path-a-persona-distillation.md` | Path A 调度说明 |
| `references/path-b-structural-decomposition.md` | Path B 调度说明（B1/B2） |
| `references/path-c-knowledge-extraction.md` | Path C 协议（Obsidian 版流水线） |
| `references/path-d-content-generation.md` | Path D 调度说明 |
| `references/obsidian-vault-setup.md` | ★ Obsidian vault 设置指南 + 笔记格式规范 |
| `references/storage-rules.md` | vault vs 本地 vs 项目记忆判定 |
| `templates/task-card.md` | sub-agent task card 模板 |
| `templates/routing-decision-log.md` | 路由决策记录 |
| `templates/learning-report.md` | Path C 学习报告模板（Obsidian 版） |