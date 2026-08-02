---
title: "主题改造说明：Liquid Stack 在 Stack v4 上做了什么"
description: "逐项说明 Liquid Stack 在 Hugo Theme Stack v4.0.3 基础上新增的页面、交互和管理能力。"
date: 2026-07-21
slug: liquid-stack-customizations
categories: [教程]
tags: [Liquid Stack, Stack v4, 功能, 配置]
---

Liquid Stack 不是用来取代 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) 的另一套主题。项目将 Stack v4.0.3 原样放在 `themes/hugo-theme-stack/` 中，再通过根目录的模板、样式、数据和脚本补充站点能力。本页明确区分原版 Stack 已有的内容与 Liquid Stack 新增的部分。

## Stack v4 保留了什么

博客的基础体验仍来自 Stack：Hugo 内容渲染、响应式导航、文章与列表页、归档、分类和标签、搜索、深色模式、多语言路由，以及文章元信息和常规小组件。文章依然是 `content/post/` 中的标准 Hugo 内容包。

Liquid Stack 有意不直接修改 vendored 的主题目录。新增与覆盖主要位于 `layouts/`、`assets/`、`data/` 和 `static/`；因此升级 Stack 时，可以清楚对照上游主题与本站扩展。

## 保留博客的个人主页式首页

`layouts/home.html` 将 Stack 默认的首页文章列表扩展为个人主页式布局：顶部有头像、站点介绍和社交链接，中间是快捷卡片，下面仍然保留近期文章、分页，以及 Stack 原有的右侧栏小组件。快捷卡片分别通向启动台、关于页面、仪表盘和照片墙，并没有删掉博客本身。

左侧栏由 `layouts/_partials/sidebar/left.html` 扩展：原有菜单、语言切换、深色模式和菜单图标都保留；头像角标额外打开仅供管理员使用的管理菜单。该菜单的链接来自 `data/management_links.yaml`，无需改模板。

## 启动台：项目数据驱动的应用展示

原版 Stack 没有应用启动台。`layouts/page/apps.html` 新增了这一页：`data/launchpad/*.yaml` 中的每个项目都可以配置名称、中英文标签、图标、预览图、对应文章和仓库地址。点击应用先打开预览层；“打开对应文章”可以指向公开网络地址，因此示例主题不必包含你的私人文章。

替换 `data/launchpad/` 中的示例数据与 `static/img/launchpad/` 中的素材即可使用自己的项目，不需要重写页面。

## 照片墙：可拖动且保留浏览器中的排列

`layouts/page/pictures.html`、`data/photo-wall/` 与 `assets/ts/custom.ts` 中的相册逻辑把普通图片列表变成照片墙。每张图拥有稳定的数据 id，会根据横图或竖图显示，可以在浏览器中拖动排序，并可点击进入聚焦查看。排列位置保存在访问者浏览器中，不会改动仓库里的源文件。

请为每张图片在 `data/photo-wall/` 中保留一份 YAML 条目，并把网页可直接使用的图片放进 `static/img/gallery/`。

## 仪表盘：从内容本身生成站点概览

`layouts/page/dashboard.html` 直接读取 Hugo 的内容数据，显示已发布文章数、总字数、运行天数、分类分布、热门标签、按星期与小时统计的发布节奏，以及年度文章贡献热力图。对应的前端绘制逻辑位于 `assets/ts/custom.ts`。

这是一份基于站内内容的概览，不是外部统计追踪服务。若启用评论，定制的 Waline 接入还能显示阅读量与评论数；公开使用前请先填写你自己的 Waline 服务地址。

## CMS、评论、友链与站点工具

Liquid Stack 还保留了原版 Stack 没有附带的管理工具：

- `/admin/` 使用 Sveltia CMS。生成配置来自 `layouts/admin/section.cmsconfig.yml` 和 `assets/admin/cms-config-base.yml`，覆盖双语文章、启动台条目和照片墙数据。
- `layouts/_partials/comments/provider/waline.html` 为 Waline 评论区补充了与主题一致的样式、配置提示与互动统计；仓库中仅保留示例服务地址。
- 友链页是数据驱动的链接中心，包含回链规则与可配置的申请、联系入口。
- 自定义站点地图、多语言路由元数据、世界时钟与分类小组件、页脚信息和文章详情组件共同组成了站点工具层。

## 要把它改成自己的站点，应从哪里开始

先在 `hugo.yaml` 修改站点名称、语言、菜单、社交链接与服务地址；再替换 `data/launchpad/`、`data/photo-wall/`、`data/friend-links/` 中的示例数据，编辑关于页面，并在 `content/post/` 下新增文章。不要把站点定制直接写进 `themes/hugo-theme-stack/`，应沿用现有的 Liquid Stack 覆盖文件。

升级 Stack 时，请对照 vendored 主题与根目录覆盖文件，并逐页检查上面列出的功能。这正是同时保留上游主题与这些扩展所需要的维护边界。
