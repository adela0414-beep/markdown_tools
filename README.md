# Markdown 智能分页切图工具

一个单文件静态网页工具，用于把 Markdown 内容实时渲染为固定比例的分页图片，并打包导出 PNG。

## 快速开始

直接用浏览器打开 `index.html` 即可使用。也可以在项目根目录启动本地静态服务：

```bash
python3 -m http.server 8000
```

然后访问：

```text
http://localhost:8000/index.html
```

## 核心能力

- 左侧编辑 Markdown，右侧实时分页预览。
- 每页固定 `330x440`，保持 `3:4` 图片比例。
- 页面内容边距固定为 `15px`。
- 支持 `001` 到 `010` 共 10 个主题风格。
- 支持内容字体选择和字体大小调节。
- 支持底部水印开关和水印文案自定义。
- 水印包含文字和点状背景层。
- 支持宽表格转图片，避免表格挤压分页。
- 支持代码高亮，包含 `javascript`、`json` 等常用语言。
- 支持复制 HTML 和导出 ZIP 图片包。

## 导出说明

导出按钮会把右侧每一页预览生成 PNG，并打包为 `markdown_pages.zip`。

实现要点：

- 导出前会等待网页字体加载完成，避免导出字体和预览字体不一致。
- 主导出路径使用 `html2canvas`。
- `dom-to-image` 保留为兜底方案。
- 页面尺寸固定，不会因为水印开关或最后一页内容少而改变图片比例。

## 部署

本项目部署到 Vercel。推送到 GitHub 的 `main` 分支后会自动触发生产部署。

部署信息见 [.agent/workflows/deploy.md](.agent/workflows/deploy.md)。

## 项目结构

```text
.
├── index.html
├── README.md
├── AGENTS.md
└── .agent/workflows/deploy.md
```

## 维护注意

- 这是单文件静态工具，没有构建步骤。
- 不要提交 `.vercel` 或 `.DS_Store`。
- 调整分页逻辑时必须保持每页 `330x440`。
- 调整水印时必须保留点状背景层，除非产品明确要求删除。
