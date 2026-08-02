---
title: 主题改造说明：Liquid Stack 包含什么
description: 认识首页、启动台、相册、仪表盘和内容管理入口。
date: 2026-07-21
slug: liquid-stack-customizations
categories: [教程]
tags: [Liquid Stack, 功能, 配置]
---

Liquid Stack 在 Hugo 与 Stack 的基础上保留博客写作，并加入更适合作品与个人站点的页面结构。

## 首页与侧栏

首页将近期文章、快捷入口和小组件放在一起。侧栏菜单由页面前置数据控制；保留原有图标和顺序，只修改标题或链接即可。

## 项目与视觉内容

启动台的数据位于 `data/launchpad/`，每个项目可包含图标、预览图、文章链接和仓库链接。相册的条目位于 `data/photo-wall/`，对应图片放在 `static/img/gallery/`。

## 管理与仪表盘

项目保留管理入口、仪表盘和静态 CMS 配置。接入自己的仓库、评论服务或统计服务前，请先替换示例地址与密钥；不要把真实凭据提交到公开仓库。
