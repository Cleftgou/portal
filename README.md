# 项目集 / Portal

梦长的项目入口页。一个静态站点，一个索引，目前一个入口。

- 视觉：米色纸底、巨号混排标题（无衬线 + 衬线斜体）、一个朱砂色、程序生成的金属物件
- 3D：Three.js（本地 vendor，无 CDN 依赖），环境贴图用 canvas 现场画，没有模型文件
- 依赖：无。单页 HTML + CSS + 原生 JS，Three.js 是唯一的第三方库
- 构建：没有构建。改完直接部署

## 本地预览

```powershell
# 在本目录
python -m http.server 8080
# 打开 http://127.0.0.1:8080
```

> 必须走 http：Three.js 用 ES Module 加载，`file://` 会被 CORS 挡。

## 部署

```powershell
npx wrangler pages deploy . --project-name mengchang
```

或把仓库连到 Cloudflare Pages（Build command 留空，Output directory 填 `/`）。

## 加一个项目

1. 在 `02 / SELECTED WORK` 里复制一份 `<a class="project">`，改三处：链接、标题、说明。
2. 截图存到 `assets/img/`，1200×675 的 WebP，控制在 100KB 内。
3. 多项目时把新增的放进列表，第一张卡保持大图。

## 细节

- 自定义光标、磁吸链接、卡片倾斜与图内视差、逐行遮罩揭示、滚动揭示、纸面颗粒
- `prefers-reduced-motion` 下关闭全部动效
- 全站正文 ≥ 12px；中文用系统黑体，拉丁用自托管的 Cormorant 子集（两个 woff2，共 43KB）
