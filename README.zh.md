# Liquid Stack

[English](README.md) · [主题 Demo](https://liquid-stack.pages.dev/zh/) · [真实站点演示](https://jingyuan-zheng.github.io/) · [使用此模板](https://github.com/new?template_name=Liquid-Stack&template_owner=Jingyuan-Zheng)

Liquid Stack 是一套基于原版 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3 的完整双语 Hugo 站点模板。它保留 Stack 的博客基础，并加入个人主页式首页、启动台、可交互照片墙、内容仪表盘、Sveltia CMS、Waline 扩展、友链申请流程、双语站点地图和可直接替换的示例内容。

## Liquid Stack 新增内容

### 视觉系统

- 以苹果 Liquid Glass 设计语言为灵感，加入半透明弹层、背景模糊、柔和表面和明暗模式适配
- 为文章卡片、主页组件、面板、控件和角标建立统一的圆角层级
- 使用 Lucide 轻量线性图标统一功能入口与导航
- 使用浅灰紫与中性色作为主要配色，以少量功能色帮助识别状态

### 主页组件

- 可替换身份信息、介绍和社交链接的个人信息区域
- 连接启动台、关于页面、仪表盘和照片墙的快捷卡片
- 显示访客本地时间和站点设置时间的双模拟世界时钟
- 采用同一视觉系统的搜索、归档、分类、标签和文章列表

### 阅读与双语发布

- 按照浏览器地区显示文章日期，并提供打印、分享、相关文章、目录和全文搜索
- 根据浏览器语言自动选择英文或简体中文，保存手动语言偏好，并优先进入同一文章的译文
- 提供面向读者的双语网站地图、多语言 XML sitemap 和带搜索入口的 404 页面

### 项目、照片与关于页面

- 通过数据文件管理图标、预览图、文章和仓库链接的项目启动台
- 支持横图、竖图、拖动排列、聚焦查看和浏览器位置记忆的照片墙
- 带进入动画、时间线和浮动菜单的关于页面，可用于个人介绍、网站故事、作品经历或简历

### 管理与互动

- 可配置的管理菜单，集中连接内容后台、评论、部署、分析和其他站点工具
- 位于 `/admin/` 的 Sveltia CMS，可在浏览器中编辑双语文章和网站数据
- 根据 Hugo 内容生成文章统计、分类、标签、发布习惯和年度热力图的网站仪表盘
- 与主题样式统一的 Waline 评论和完整友链申请流程

## 使用模板创建站点

1. 在 GitHub 点击 **Use this template**，创建一个新的公开仓库。
2. 打开 `hugo.yaml`，替换 `baseURL`、站点名称、版权、侧栏介绍和社交链接。
3. 替换 `data/` 下的示例数据和 `static/img/` 下的通用素材。
4. 使用 Hugo Extended 构建网站。
5. 将生成的 `public/` 目录发布到 Cloudflare Pages 或你选择的静态托管平台。

## 本地预览

安装 Hugo Extended，然后在仓库根目录运行：

```bash
hugo server -D
```

正式构建使用：

```bash
hugo --minify --cleanDestinationDir --ignoreCache
```

## 目录说明

- `hugo.yaml`：站点信息、语言、菜单、小组件和服务配置
- `content/`：双语页面、分类和文章
- `layouts/`：Liquid Stack 的模板覆盖和新增页面
- `assets/`：定制样式、交互脚本和 CMS 基础配置
- `data/launchpad/`：启动台项目
- `data/photo-wall/`：照片墙条目
- `data/friend-links/`：友链卡片
- `static/img/`：可以替换的示例图片与图标
- `themes/hugo-theme-stack/`：未经修改的官方 Stack v4.0.3

官方 Stack 主题文件保持原样，Liquid Stack 的站点功能通过项目根目录扩展。完整说明见[欢迎使用 Liquid Stack：主题新增功能](https://liquid-stack.pages.dev/zh/p/welcome-to-liquid-stack/)。

## 许可证

Liquid Stack 与内置的上游 Stack 主题一致，采用 GPL v3.0 或更高版本。完整许可证位于 `themes/hugo-theme-stack/LICENSE`。
