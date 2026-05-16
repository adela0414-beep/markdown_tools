# AGENTS.md

## 项目概览

这是一个单文件静态网页工具，核心文件是 `index.html`。它把 Markdown 内容分页渲染为固定比例图片，并支持复制 HTML、导出 PNG ZIP。

## 硬约束

- 页面预览和导出图片必须保持 `330x440`，即 `3:4` 比例。
- `.preview-page` 必须是固定高度，不要恢复动态高度或最后一页自适应高度。
- 页面内容边距固定为 `15px`，不要恢复左侧“页面边距”滑块，除非用户明确要求。
- 水印必须保留文字和点状背景层：`createWatermarkLayer()`、`.preview-page-watermark-dots`、`.preview-page-watermark-dot`。
- 主题下拉显示为 `001` 到 `010`，不要改回中文主题名。
- 主题配置集中在 `themes` 对象里；切换主题时会同步默认字体。

## 实现要点

- Markdown 解析使用 `marked.js`。
- 代码高亮使用 `highlight.js`，已有语言别名和自动识别回退。
- 导出主路径使用 `html2canvas`，`dom-to-image` 是兜底。
- 导出前必须等待 `document.fonts.ready`，避免导出字体和预览不一致。
- 宽表格会先转成图片再参与分页。

## 常用检查

```bash
node - <<'NODE'
const fs = require('fs');
const html = fs.readFileSync('index.html', 'utf8');
const scripts = [...html.matchAll(/<script>([\s\S]*?)<\/script>/g)].map(match => match[1]);
for (const script of scripts) new Function(script);
console.log(`checked ${scripts.length} inline script(s)`);
NODE
```

```bash
git diff --check
```

## 部署

推送到 GitHub 的 `main` 分支后会自动触发 Vercel 生产部署。详见 `.agent/workflows/deploy.md`。
