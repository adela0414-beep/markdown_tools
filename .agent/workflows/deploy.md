---
description: 部署 Markdown 切图工具到 Vercel 生产环境
---

# 部署流程

> ⚠️ **重要**：本项目不依赖 GitHub 推送自动触发 Vercel 部署，**必须手动执行部署命令**。

## 步骤

1. 确保所有更改已提交并推送到 GitHub：

```bash
cd "/Users/liuyi/IdeaProjects/Markdown 切图工具"
git add -A
git commit -m "描述性的提交信息"
git push origin main
```

// turbo
2. 手动触发 Vercel 生产部署：

```bash
cd "/Users/liuyi/IdeaProjects/Markdown 切图工具" && vercel --prod
```

3. 等待部署完成，确认输出中包含 `✅ Production` 字样。

## 项目信息

- **Vercel 项目名**：markdown-tool
- **生产地址**：https://markdown-tool-ten.vercel.app
- **Vercel 面板**：https://vercel.com/liuyi0414-sources-projects/markdown-tool
