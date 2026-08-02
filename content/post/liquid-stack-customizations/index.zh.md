---
title: "从 Stack v4 到 Liquid Stack：完整改造对比"
description: "基于官方 Hugo Theme Stack v4.0.3 的逐文件对比，说明 Liquid Stack 新增、覆盖和保留了什么。"
date: 2026-07-21
lastmod: 2026-08-02
slug: liquid-stack-customizations
categories: [教程]
tags: [Liquid Stack, Stack v4, 主题改造, Hugo]
---

本文不是功能宣传，而是一次可以复核的代码对比：Liquid Stack 以 [CaiJimmy/hugo-theme-stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3 为基线，说明原版 Stack 已经提供什么，以及本项目究竟修改了什么。

## 对比基线与结论

本次对照的是 Stack 官方 v4.0.3 标签，对应 commit [`3e123a3`](https://github.com/CaiJimmy/hugo-theme-stack/commit/3e123a30b79b5d52a3a8e88a9dd678fcfd28e418)。对官方仓库与本项目 `themes/hugo-theme-stack/` 做逐文件比较后，结果是：**vendored 主题目录与官方 v4.0.3 一致**。

也就是说，Liquid Stack 没有把改动混进 Stack 源码。全部定制都放在 Hugo 项目根目录，由 Hugo 的模板覆盖机制加载。目前共有：

- 23 个覆盖官方 Stack 同名模板的文件；
- 12 个 Stack 原版不存在的全新模板；
- 一套独立的 `custom.scss` 与 `custom.ts` 交互层；
- 启动台、照片墙、友链和管理入口的数据文件；
- Sveltia CMS、Waline 扩展、Cloudflare Worker 浏览量示例与 GitHub Pages 工作流。

因此它更准确的定位是：**保留 Stack v4 博客内核的完整站点模板**，而不是只换配色的皮肤。

## 原版 Stack 保留了什么

下列基础能力仍直接来自 Stack v4.0.3：响应式三栏结构、左侧导航、文章列表与文章页、归档、分类与标签、全文搜索、目录小组件、深色模式、图片处理、相关文章、多语言内容，以及 Stack 原有的评论 provider 框架。

Liquid Stack 没有重新实现这些基础能力，而是在它们之上增加站点级页面和交互。因此普通文章仍然放在 `content/post/<slug>/`，Stack 的参数与内容组织方式仍可继续使用。

## 首页：从文章列表变成完整门户

原版 `layouts/home.html` 只负责输出文章列表、分页和页脚。Liquid Stack 的同名覆盖在保留文章列表、分页和右侧小组件的同时，增加了：

- 头像、欢迎语、站点介绍和社交链接组成的主页头部；
- 启动台、关于页面、仪表盘和照片墙四类快捷卡片；
- 从 `data/launchpad/` 与 `data/photo-wall/` 自动读取的卡片预览；
- 独立的响应式首页布局、悬停动画和深色模式样式。

因此首页不是取消博客列表，而是把 Stack 的文章列表放进一个更完整的个人站点入口。

## 左侧栏与管理入口

原版 Stack 左侧栏包含头像、站点信息、社交链接、菜单、语言切换和深色模式。Liquid Stack 保留这些结构和菜单图标，并在 `layouts/_partials/sidebar/left.html` 中加入头像角标管理入口。

新增的 `layouts/_partials/sidebar/management-menu.html` 从 `data/management_links.yaml` 生成管理菜单，可统一放置 CMS、评论后台、友链申请、GitHub Pages、搜索控制台、数据分析与部署平台入口。普通访客看到的是同一套站点侧栏，管理者则可以从角标快速进入工具。

## 文章页：分享、打印与元信息布局

原版 Stack 没有本项目这套分享工具栏。Liquid Stack 新增 `article/components/share.html`，提供：

- 打印与复制链接；
- 支持浏览器原生分享；
- 中文页的微博、QQ、X 分享；
- 英文页的 X、Reddit、LinkedIn、WhatsApp 与邮件分享；
- 打印时显示作者和文章来源。

`article.html`、`details.html`、`single.html` 和 `list.html` 的覆盖用于接入分享区、整理双语与标签元信息，并让动态页脚在所有页面正确更新。

## 启动台：原版没有的项目展示系统

`layouts/page/apps.html` 是 Liquid Stack 全新页面。每个 `data/launchpad/*.yaml` 条目可以配置中英文名称、应用图标、预览图、相关文章与仓库地址。点击图标先打开类似桌面应用的预览层，再由按钮进入文章。

项目数据和页面模板分离，所以使用者只需替换 YAML 与 `static/img/launchpad/` 中的素材，不需要修改页面代码。

## 照片墙：不只是 Stack 的文章图片

`layouts/page/pictures.html` 与 `data/photo-wall/` 组成独立照片墙。`assets/ts/custom.ts` 会读取真实图片比例，支持横图与竖图、拖动排列、点击聚焦、关闭动画，并按照稳定 id 将排列保存在浏览器本地。

这与原版 Stack 在文章卡片中显示封面图不同：照片墙是一个独立、可交互、数据驱动的展示页面。

## 仪表盘：从 Hugo 内容生成站点统计

`layouts/page/dashboard.html` 是另一项全新功能。它在构建时读取 Hugo 内容，在浏览器中绘制：

- 已发布文章数、总字数和运行天数；
- 分类分布与热门标签；
- 按星期和小时统计的发布习惯；
- 年度文章贡献热力图；
- Hugo、Stack、部署平台、评论和 CMS 状态。

这些内容来自仓库本身，不依赖外部分析服务。若配置 Waline，页脚和评论区还可以显示阅读量与评论数。

## Waline：保留 Stack provider，改造交互层

Stack v4 原本已经支持 Waline。Liquid Stack 没有把它冒充为全新评论系统，而是覆盖原 provider，增加：

- 中英文评论提示与互动统计；
- 与主题深色模式一致的完整样式；
- 自定义反应文案和图标；
- 主服务不可用时的备用服务探测；
- 评论列表中 RSS 和管理操作的位置调整；
- 页脚全站浏览量显示。

开源模板只保留示例地址，使用者需要配置自己的 Waline 后端。

## 友链：从紧凑链接列表扩展为申请流程

原版 `article/components/links.html` 只显示紧凑链接列表。Liquid Stack 将它扩展为：

- 个人平台链接区；
- 由 `data/friend-links/` 生成的友链卡片；
- 友链规则入口；
- 申请与联系按钮；
- 可选的嵌入式申请表单。

因此友链页不再只是静态链接集合，而是一套可以直接替换数据和申请地址的公开页面。

## 双语、SEO、站点地图与 404

新增的 `head/language-routing.html` 会保存语言偏好，并在中英文对应页面之间选择正确目标。Head 与 Open Graph 覆盖还补充了语言路由、favicon 和社交元数据处理。

Liquid Stack 同时新增：

- 面向读者的中英文 HTML 网站地图；
- XML sitemap index 与包含全部语言页面的 flat sitemap；
- 能从错误路径提取关键词并直接搜索的 404 页面；
- 世界时钟小组件；
- 更完整的分类、归档、标签云和目录样式。

## 图标系统与视觉层

原版 Stack 的图标 helper 只从本地 `assets/icons/` 读取 SVG。Liquid Stack 的 helper 在保留本地图标回退的同时，统一映射 Simple Icons、Lucide 与 Phosphor 图标，供社交品牌、管理工具和通用界面使用。

视觉与交互主要集中在 `assets/scss/custom.scss` 和 `assets/ts/custom.ts`。前端脚本分别初始化语言体验、文章分享、首页动画、平滑导航、启动台、照片墙、世界时钟、仪表盘、管理菜单和移动端手势，并为减少动态效果的系统偏好提供降级。

## CMS 与公开模板工作流

原版 Stack 不包含内容管理后台。Liquid Stack 的 `/admin/` 加载 Sveltia CMS，配置由 `layouts/admin/section.cmsconfig.yml` 与 `assets/admin/cms-config-base.yml` 生成，覆盖双语文章、分类、启动台、照片墙等内容类型。

仓库还附带 GitHub Pages Action。使用者通过 GitHub 的 **Use this template** 创建自己的仓库后，修改 `hugo.yaml` 中的站点名称与地址，即可用同一工作流部署。

## 35 个模板差异文件

相对官方 Stack v4.0.3，Liquid Stack 覆盖了以下 23 个同名模板：

`404.html`、`article/article.html`、`article/components/details.html`、`article/components/links.html`、`comments/provider/giscus.html`、`comments/provider/waline.html`、`cookies/analytics.html`、`footer/footer.html`、`head/custom.html`、`head/head.html`、`head/opengraph/provider/base.html`、`head/opengraph/provider/twitter.html`、`helper/icon.html`、`sidebar/left.html`、`widget/archives.html`、`widget/categories.html`、`widget/tag-cloud.html`、`widget/toc.html`、`archives.html`、`home.html`、`list.html`、`page/search.html`、`single.html`。

以下 12 个模板则是 Liquid Stack 新增、官方 Stack 中不存在的文件：

`article/components/share.html`、`head/language-routing.html`、`sidebar/management-menu.html`、`widget/world-clock.html`、`admin/section.cmsconfig.yml`、`index.sitemapflat.xml`、`page/apps.html`、`page/dashboard.html`、`page/pictures.html`、`page/sitemap.html`、`sitemap.xml`、`sitemapindex.xml`。

这份清单就是升级上游 Stack 时应重点复核的兼容边界。
