# kkwalking的知识小站

基于 Hexo 的静态博客项目，使用 GitHub Actions 自动部署到 GitHub Pages。

## 项目结构

```
kkwalking.github.io/
├── .github/
│   └── workflows/
│       └── pages.yml          # GitHub Actions 部署配置
├── source/
│   └── _posts/                # 文章目录
├── scaffolds/
│   └── post.md                # 文章模板
├── themes/
│   └── baozi/                 # 主题文件
├── _config.yml                # Hexo 主配置文件
└── package.json               # 项目依赖和脚本
```

## 本地开发

### 安装依赖（可选）

如果需要在本地预览，安装依赖：

```bash
npm install
```

### 创建新文章

#### 方式一：使用 Hexo 命令（需要安装依赖）

```bash
npm run new post "文章标题"
# 或者
hexo new post "文章标题"
```

#### 方式二：手动创建文件（推荐 AI Agent 使用）

无需安装 Hexo，直接在 `source/_posts/` 目录下创建 Markdown 文件即可。

**文件格式：**
- 文件路径：`source/_posts/文章标题.md`

**文件内容模板：**
```markdown
---
title: 文章标题
date: 2024-02-19 20:00:00
tags: [标签1, 标签2]
categories: 分类
---

这里是文章正文内容...

## 一级标题

### 二级标题

- 列表项 1
- 列表项 2

代码示例：
```js
console.log("Hello, World!");
```

[链接文本](https://example.com)
```

## 部署流程

### 部署触发条件

GitHub Actions 工作流配置在 `.github/workflows/pages.yml`，触发条件为：

- 推送以 `v` 开头的标签（如 `v1.0.0`）

### 部署步骤

#### 步骤 1：编写文章

**AI Agent 操作流程：**

1. 在 `source/_posts/` 目录下创建新的 Markdown 文件
2. 文件命名建议：`YYYY-MM-DD-标题.md` 或直接使用 `标题.md`
3. 写入文章内容，包含完整的 front matter 和正文

**示例操作：**
```
创建文件：source/_posts/2024-02-19-hello-world.md
```

**文件内容：**
```markdown
---
title: Hello World
date: 2024-02-19 20:00:00
tags: [教程, Hexo]
categories: 技术
---

# Hello World

这是我的第一篇文章！
```

#### 步骤 2：提交代码
   ```bash
   git add .
   git commit -m "添加新文章"
   git push
   ```

#### 步骤 3：创建并推送标签触发部署
   ```bash
   # 创建标签（版本号递增，如 v1.0.1, v1.0.2）
   git tag v1.0.1
   
   # 推送标签到远程仓库
   git push origin v1.0.1
   ```

#### 步骤 4：查看部署状态
   - 访问 GitHub 仓库的 Actions 页面查看工作流运行状态
   - 部署完成后，博客会自动更新到 GitHub Pages

