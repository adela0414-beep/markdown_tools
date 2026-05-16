---
description: 部署 Markdown 切图工具到 Vercel 生产环境
---

# 部署流程

> 本项目已连接 Vercel，推送到 GitHub 的 `main` 分支后会自动触发生产部署。

## 步骤

1. 确保所有更改已提交并推送到 GitHub：

```bash
cd "/Users/liuyi/IdeaProjects/Markdown 切图工具"
git add -A
git commit -m "fix: 中文提交标题" -m "主要改动：
- 补充本次核心变更。
- 说明影响范围和验证结果。"
git push origin main
```

2. 等待 Vercel 自动部署完成，并访问生产地址验证页面。

## 项目信息

- **Vercel 项目名**：markdown-tool
- **生产地址**：https://markdown-tool-ten.vercel.app
- **Vercel 面板**：https://vercel.com/liuyi0414-sources-projects/markdown-tool
