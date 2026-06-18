# 纳川 · Obsidian Vault 设置指南

## 为什么用 Obsidian？

纳川将知识存储在 **Obsidian vault**——一个由本地 Markdown 文件构成的文件夹。选择 Obsidian 的理由：

- **纯文本，未来可读**：所有知识是 `.md` 文件，不绑定任何平台
- **wikilinks 天然关联**：`[[笔记名]]` 语法让知识自动形成网络
- **本地优先**：你的知识完全在你自己的磁盘上
- **Git 友好**：整个 vault 可以用 Git 做版本控制和备份
- **免费开源**：Obsidian 个人使用完全免费

---

## 一、创建纳川 Vault

### 方式 A：现有 Obsidian 用户

在你的 vault 中创建 `纳川/` 目录：

```
your-existing-vault/
└── 纳川/
    ├── 学习报告/
    ├── 知识记忆/
    ├── 人物精华/
    ├── 结构拆解/
    ├── 生成内容/
    └── 纳川_MOC.md
```

### 方式 B：新建专用 Vault

```bash
# 创建新 vault 目录
mkdir -p ~/Documents/纳川-vault/纳川/{学习报告,知识记忆,人物精华,结构拆解,生成内容}
mkdir -p ~/Documents/纳川-vault/模板

# 在 Obsidian 中打开此文件夹作为 vault
```

---

## 二、笔记格式规范

### 知识记忆笔记（Path C 产出）

```markdown
---
tags: [纳川, 领域标签, 子主题, Path-C]
created: YYYY-MM-DD
source: "[[来源文档学习报告]]"
related:
  - "[[相关笔记1]]"
  - "[[相关笔记2]]"
---

# 笔记标题：一句话概括知识点

[正文：2-5 句展开]

**来源**：第 N 页
**可复用场景**：[在什么情况下有用]
```

### 学习报告笔记（Path C 产出）

```markdown
---
tags: [纳川, 学习报告, 领域标签, Path-C]
created: YYYY-MM-DD
knowledge_count: N
topics: [主题1, 主题2, 主题3]
---

# 文档名 · 学习报告

## 基本信息
- **文档类型**：PPT / PDF / ...
- **规模**：N 页 / N 字

## 知识提取成果
...

## 关联笔记
- [[笔记1]] — enriches
- [[笔记2]] — evolves
```

### 人物精华笔记（Path A 产出）

```markdown
---
tags: [纳川, 蒸馏, 人物名, Path-A]
created: YYYY-MM-DD
skill_path: ~/.hermes/skills/.../SKILL.md
---

# 人物名 · 精华摘要

## 心智模型（N 个）
1. **模型名** — 一句话描述

## 表达DNA
- 风格关键词：X / Y / Z

## 核心金句 TOP5
1. "..."
...

## 完整 Skill
本地路径：`[path]`
```

### 结构拆解摘要（Path B 产出）

```markdown
---
tags: [纳川, 结构拆解, 领域标签, Path-B]
created: YYYY-MM-DD
framework_type: A/B/C/D/E/F/G
page_types: [类型1, 类型2, ...]
---

# 项目名 · 拆解摘要

## 叙事框架
- **类型**：[A-G 之一]
- **步骤序列**：[5-10 步]
- **情绪曲线**：[描述]

## 关键页面类型
| 类型 | 页数 | 代表页 |
|------|------|--------|
| ... | ... | ... |
```

---

## 三、标签体系

纳川推荐以下标签层级（在 Obsidian 中通过 YAML frontmatter `tags` 字段使用）：

### 系统标签（每条笔记必带）
- `纳川` — 标识由纳川生成
- `Path-A` / `Path-B` / `Path-C` / `Path-D` — 来源路径

### 领域标签（至少 1 个）
- `保险` / `养老` / `护理` / `投资` / `销售` / `培训` / `竞品分析` / ...

### 内容类型标签
- `学习报告` / `知识记忆` / `框架` / `规律` / `话术模板` / `精华` / ...

### 在 Obsidian 中使用标签
标签出现在笔记的 YAML frontmatter 中后，Obsidian 的「标签面板」和「图谱视图」会自动识别并聚合。你也可以用 `tag:#标签名` 搜索。

---

## 四、Vault 预搜（Step 0 静默扫描用）

在开始知识提取前，搜索 vault 中已有内容以避免重复：

```bash
# 用 grep 搜索
grep -rl "关键词" ~/Documents/纳川-vault/纳川/

# 用 Obsidian 搜索
# 在 Obsidian 中 Ctrl/Cmd+Shift+F 全局搜索

# 搜索特定标签
grep -rl "tags:.*关键词" ~/Documents/纳川-vault/纳川/
```

---

## 五、Wikilinks 与知识关联

纳川用 Obsidian wikilinks (`[[笔记名]]`) 替代数据库的外键关系：

### 关系类型

| 关系 | wikilink 用法 | 说明 |
|------|-------------|------|
| **来源引用** | `source: "[[学习报告名]]"` | 笔记来源于哪个文档 |
| **丰富（enriches）** | `related: [[已有笔记]]` + 正文说明 | 新笔记补充/深化已有笔记 |
| **演进（evolves）** | `related: [[旧笔记]]` + 正文注明"此认知已演进" | 新认知推翻/升级旧认知 |
| **对比** | `related: [[竞品笔记]]` + 正文对比 | 两个竞争性观点 |

### MOC（Map of Content）索引

在 `纳川_MOC.md` 中维护总索引：

```markdown
# 纳川 · 知识索引

## 保险
- [[太保颐护添年产品设计]]
- [[长护险政策梳理_2026]]
- ...

## 养老
- [[南山居服务模式_1+1+N]]
- [[太保家园五大能力矩阵]]
- ...

## 竞品情报
- [[竞品A_护理险产说会_拆解]]
- ...
```

---

## 六、写入确认闸门

每次将笔记写入 vault 前，纳川展示预览：

```
准备写入 Obsidian vault：

Path B 产出（入 vault/纳川/结构拆解/）：
  • [笔记标题].md（标签：#纳川 #结构拆解 #保险）

Path C 产出（入 vault/纳川/知识记忆/保险/）：
  • [笔记1].md → wikilinks: [[已有笔记A]]
  • [笔记2].md → wikilinks: [[已有笔记B]]
  • ...
  学习报告（入 vault/纳川/学习报告/）

确认写入？【全部写入 / 仅知识 / 仅框架 / 暂不】
```

---

## 七、备份与版本控制

```bash
# 用 Git 管理 vault
cd ~/Documents/纳川-vault
git init
git add .
git commit -m "纳川知识库更新 YYYY-MM-DD"

# 可推送到私有 GitHub 仓库做远程备份
```