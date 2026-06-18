# Handoff: 纳川 GitHub 发布

> 给 Codex / Computer Use Agent 的执行指令。本地仓库已就绪，只需完成 GitHub 远端操作。

---

## 背景

这是一个 Claude Code Skill——**纳川 · Distill Everything**。本地 Git 仓库已完成初始化和首次提交（branch: `main`）。

## 任务

1. 在 GitHub 创建公开仓库 `wilsondd-lab/nachuan`
2. 推送本地仓库到 GitHub
3. 验证 `npx skills add wilsondd-lab/nachuan` 可用

---

## 执行步骤

### Step 1: 确认本地仓库状态

```bash
cd /Users/wilson/Documents/纳川-github
git status
git log --oneline
```

预期：clean working tree，1 个 commit "纳川 v1.0.0 · 内容获取中间层"。

### Step 2: 安装 GitHub CLI（如果没有）

```bash
# 检查
which gh

# 如果没有，通过 Homebrew 安装
# 如果 Homebrew 也没有，先装 Homebrew: /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install gh
```

### Step 3: 登录 GitHub

```bash
gh auth login
```

按提示完成浏览器登录流程。

### Step 4: 创建 GitHub 仓库

```bash
cd /Users/wilson/Documents/纳川-github
gh repo create wilsondd-lab/nachuan --public --source=. --remote=origin --push
```

这行命令会：
- 在 GitHub 创建公开仓库 `wilsondd-lab/nachuan`
- 将当前目录设为源代码
- 添加 `origin` 远程
- 推送到 GitHub

**如果 `wilsondd-lab` 不是你的 GitHub 用户名**，替换为你实际的用户名。

### Step 5: 验证

```bash
# 确认远程已设置
git remote -v

# 确认推送成功
gh repo view wilsondd-lab/nachuan --web
```

浏览器中应能看到 README.md 渲染的页面。

### Step 6: 测试安装命令（可选）

推送成功后，理论上可以通过以下方式安装：

```bash
npx skills add wilsondd-lab/nachuan
```

---

## 仓库内容概览

```
nachuan/
├── SKILL.md                           # 主编排文件（给 Claude 读）
├── README.md                          # 说明文档（给人读）
├── README.en.md                       # 英文版
├── LICENSE                            # MIT
├── .gitignore
├── references/
│   ├── interview-templates.md         # 11 种场景模板
│   ├── routing-matrix.md              # 完整路由矩阵
│   ├── obsidian-vault-setup.md        # Obsidian vault 设置指南
│   ├── path-a-essence-distillation.md
│   ├── path-b-structural-decomposition.md
│   ├── path-c-knowledge-extraction.md
│   ├── path-d-content-generation.md
│   └── storage-rules.md
└── templates/
    ├── task-card.md
    ├── routing-decision-log.md
    └── learning-report.md
```

---

## 故障排查

| 问题 | 解决 |
|------|------|
| `gh auth login` 失败 | 确认浏览器可以访问 github.com，DNS 正常 |
| `gh repo create` 报 "name already exists" | 说明仓库已存在，用 `git remote add origin https://github.com/wilsondd-lab/nachuan.git && git push -u origin main` |
| 推送被拒（权限） | 检查 `gh auth status`，确认登录的是正确的 GitHub 账号 |
| `brew` 不存在 | 先安装 Homebrew：`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` |
