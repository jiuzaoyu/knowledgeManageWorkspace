# 个人知识管理系统

基于 **Obsidian + Claude Code + GitHub** 搭建的个人知识管理工作流。

## 工具介绍

| 工具 | 用途 |
|------|------|
| [Obsidian](https://obsidian.md/) | 本地 Markdown 笔记管理，支持双向链接、图谱视图、插件扩展 |
| [Claude Code](https://docs.anthropic.com/en/docs/claude-code) | AI 辅助编程与内容处理，自动化知识整理 |
| [GitHub](https://github.com/) | 远程仓库托管，版本控制，多设备同步 |

## 目录结构

```
knowledgeManageWorkspace/
├── .gitignore          # 忽略 Claude/Obsidian 本地配置
├── README.md           # 本说明文件
└── 原始数据/            # 知识素材存放
    ├── html/           # 网页抓取的 HTML 内容
    └── pdf/            # PDF 文档资料
```

## 搭建步骤

### 1. 创建 GitHub 仓库

在 GitHub 上创建一个私有仓库，用于托管知识管理内容。

### 2. 克隆到本地

```bash
git clone git@github.com:your-username/your-repo.git
cd your-repo
```

### 3. 用 Obsidian 打开仓库目录

1. 打开 Obsidian
2. 点击「打开其他仓库」→「打开本地文件夹」
3. 选择克隆下来的仓库目录
4. Obsidian 会自动识别 `.md` 文件并建立索引

### 4. 安装第三方插件

1. 在 Obsidian 设置中禁用安全模式
2. 主要用的第三方插件如图：
![[Pasted image 20260522203943.png]]
3. 插件说明：

| 插件                       | 用途                                   |
| ------------------------ | ------------------------------------ |
| **Obsidian Git**         | 自动拉取/推送仓库，定时同步笔记到 GitHub             |
| **Claudian**             | 在 Obsidian 中集成 Claude Code，辅助写作与知识整理 |
| **Obsidian MarkMind**    | 思维导图插件，支持在 Obsidian 中绘制和浏览思维导图       |
| **Obsidian HTML Plugin** | 在 Obsidian 中渲染 HTML 页面，方便查看抓取的网页内容   |
| **Translate**            | 翻译插件，支持选中文本快速翻译                      |

### 5. 安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### 6. 日常使用工作流

```
信息获取          →    知识整理          →    版本同步
网页/PDF/文档          Claude Code              GitHub
     ↓                     ↓                      ↓
 原始数据/              格式化/提炼            git push
                   生成 .md 笔记
                       ↓
                  Obsidian 浏览
```

1. **收集素材**：将感兴趣的网页内容、PDF 等放入 `原始数据/` 目录
2. **AI 处理**：使用 Claude Code 对素材进行整理、总结、格式化为 Markdown
3. **笔记链接**：在 Obsidian 中建立笔记之间的双向链接，构建知识图谱
4. **自动同步**：Obsidian Git 插件定时推送/拉取，或手动 `git push`

### 7. 多设备同步

```bash
# 在其他设备上
git clone git@github.com:your-username/your-repo.git
# 用 Obsidian 打开该目录即可
```

每次使用前先 `git pull` 获取最新内容。

## 注意事项

- 仓库建议设为**私有**，避免个人笔记泄露
- `.obsidian/` 目录包含本地插件和配置，已加入 `.gitignore`，多设备需分别配置插件
- 大文件（PDF、图片）可用 Git LFS 管理，或单独存放云端
- 图片粘贴可使用 Obsidian 本地图片存储，目录也建议加入 `.gitignore` 避免仓库过大
