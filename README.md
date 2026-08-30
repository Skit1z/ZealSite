# ZealSite

Zeal 官方产品展示网站。基于 Astro + Tailwind CSS 构建，采用 MiniMax 风格的白色调设计语言，呈现 Hero、应用截图轮播、产品卡片、功能特性等模块。

## 技术栈

- [Astro](https://astro.build/) `^5.18.1` — 静态站点框架
- [Tailwind CSS](https://tailwindcss.com/) `^4.2.4` — 原子化 CSS（通过 `@tailwindcss/vite` 插件集成）
- TypeScript（`astro/tsconfigs/strict` 严格模式）

## 环境要求

- Node.js ≥ 18.20 / 20.3（推荐使用 LTS 最新版）
- npm（或 pnpm / yarn，下文以 npm 为例）

## 快速开始

```bash
# 1. 安装依赖
npm install

# 2. 启动本地开发服务器（默认 http://localhost:4321）
npm run dev
```

## 构建命令

| 命令              | 说明                          |
| ----------------- | ----------------------------- |
| `npm run dev`     | 启动开发服务器，支持热更新    |
| `npm run build`   | 生产构建，产物输出到 `dist/`  |
| `npm run preview` | 本地预览 `dist/` 中的构建产物 |

### 生产构建与部署

```bash
# 构建静态站点
npm run build

# 本地验证构建产物
npm run preview
```

构建产物位于 `dist/` 目录，可直接托管到任意静态站点平台（Vercel、Netlify、Cloudflare Pages、GitHub Pages、Nginx 等）。

> 由于 `astro.config.mjs` 中未配置 `site` 与 `base`，部署到带子路径的平台（如 GitHub Pages 项目站点）时，需在配置中补充：
>
> ```js
> export default defineConfig({
>   site: 'https://your-domain.com',
>   base: '/your-repo', // 仅在子路径部署时需要
>   // ...
> });
> ```

## 项目结构

```
ZealSite/
├── public/                 # 静态资源（原样拷贝）
│   ├── favicon.svg
│   └── images/             # 站点用到的图片素材
├── src/
│   ├── components/         # Astro 组件
│   │   ├── Navbar.astro        # 顶部导航
│   │   ├── Hero.astro          # 首屏主视觉
│   │   ├── AppShowcase.astro   # 应用截图交错展示
│   │   ├── ProductShowcase.astro
│   │   ├── ProductCard.astro
│   │   ├── Features.astro
│   │   ├── FeatureCard.astro
│   │   ├── Footer.astro
│   │   └── Icon.astro          # SVG 图标封装
│   ├── layouts/
│   │   └── Layout.astro        # 页面骨架（<html>/<head>）
│   ├── pages/
│   │   └── index.astro         # 首页入口，按顺序组合各组件
│   └── styles/
│       └── global.css          # 全局样式 / Tailwind 指令
├── ZealNeed/               # 设计稿与参考素材（不参与构建）
├── DESIGN.md               # 设计系统说明（配色、字体、阴影等）
├── astro.config.mjs        # Astro 配置（含 Tailwind 插件）
├── tsconfig.json           # TypeScript 配置
└── package.json
```

### 页面组件顺序

`src/pages/index.astro` 按以下顺序组合首页：

```
Navbar → Hero → AppShowcase → ProductShowcase → Features → Footer
```

## 设计系统

完整的设计 Token（品牌色、字体、阴影、圆角等）见 [DESIGN.md](./DESIGN.md)。

- 主背景：纯白 `#ffffff`
- 品牌主色：Brand Blue `#1456f0`、Sky Blue `#3daeff`、Brand Pink `#ea5ec1`
- 字体：DM Sans（UI）、Outfit（标题）、Poppins（中层级标题）、Roboto（数据展示）
- 按钮几何：导航 / CTA 使用 9999px 胶囊按钮，产品卡片使用 20–24px 圆角

## 许可证

本项目为内部产品展示站点，未包含开源许可证。
