---
title: "From Stack v4 to Liquid Stack: A Complete Comparison"
description: "A file-by-file comparison of Liquid Stack with the official Hugo Theme Stack v4.0.3 release."
date: 2026-07-21
lastmod: 2026-08-02
slug: liquid-stack-customizations
categories: [Tutorials]
tags: [Liquid Stack, Stack v4, Theme Customization, Hugo]
---

This is a verifiable code comparison, not a feature overview. Liquid Stack uses [CaiJimmy/hugo-theme-stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3 as its baseline and documents exactly what remains upstream Stack and what this project changes.

## Comparison baseline and result

The comparison uses the official Stack v4.0.3 tag at commit [`3e123a3`](https://github.com/CaiJimmy/hugo-theme-stack/commit/3e123a30b79b5d52a3a8e88a9dd678fcfd28e418). A file-by-file comparison confirms that `themes/hugo-theme-stack/` in Liquid Stack matches that release.

Liquid Stack therefore does not mix custom code into the vendored theme. Hugo loads the changes from the project root. The current extension layer contains:

- 23 overrides of existing Stack templates;
- 12 templates that do not exist in upstream Stack;
- a separate `custom.scss` and `custom.ts` interaction layer;
- data sources for the launchpad, photo wall, friend links, and management menu;
- Sveltia CMS, enhanced Waline integration, an optional Cloudflare page-view Worker, and GitHub Pages deployment.

The accurate description is a **complete site starter built on the Stack v4 blog core**, not a recoloured fork.

## What still comes from Stack

Stack v4.0.3 still supplies the responsive three-column structure, left navigation, article lists and single pages, archives, categories and tags, search, table of contents, dark mode, image processing, related content, multilingual content, and the original comment-provider framework.

Posts remain normal Hugo bundles under `content/post/<slug>/`, and existing Stack configuration concepts continue to apply.

## Home: from a post list to a site portal

Upstream `layouts/home.html` renders the post list, pagination, and footer. Liquid Stack keeps those elements and the right-sidebar widgets, then adds a profile header, social links, and shortcut cards for the launchpad, About page, dashboard, and photo wall. The card previews are populated from `data/launchpad/` and `data/photo-wall/`.

The blog feed has not been removed; it is presented inside a broader personal-site homepage.

## Sidebar and management access

The upstream sidebar already contains the avatar, site metadata, social links, navigation, language selector, and dark-mode control. Liquid Stack preserves them and extends `layouts/_partials/sidebar/left.html` with an avatar-badge management trigger.

The new `sidebar/management-menu.html` reads `data/management_links.yaml` and can link to the CMS, comment moderation, backlink applications, GitHub Pages, search consoles, analytics, and deployment services.

## Articles: sharing, printing, and metadata

Liquid Stack adds `article/components/share.html` with print and copy actions, Web Share support, Chinese targets for Weibo, QQ, and X, and English targets for X, Reddit, LinkedIn, WhatsApp, and email. Printed pages include author and source attribution.

Overrides to `article.html`, `details.html`, `single.html`, and `list.html` connect that toolbar, refine bilingual and tag metadata, and ensure the dynamic footer is rendered per page.

## Launchpad: a new project presentation system

The launchpad does not exist in upstream Stack. `layouts/page/apps.html` reads `data/launchpad/*.yaml`, where each item can define bilingual labels, an icon, a preview image, a related article, and a repository. Selecting an app opens a desktop-like preview before following the article link.

Users replace data and assets under `static/img/launchpad/` without rewriting the template.

## Photo wall: an interactive gallery

`layouts/page/pictures.html`, `data/photo-wall/`, and the gallery code in `assets/ts/custom.ts` provide an independent photo wall. It respects portrait and landscape dimensions, supports drag-to-rearrange and focused viewing, and stores positions in the visitor's browser using stable item ids.

This is separate from Stack's normal article-cover image support.

## Dashboard generated from Hugo content

The new `layouts/page/dashboard.html` builds a site overview from Hugo content: published post and word counts, days online, category distribution, popular tags, publishing activity by weekday and hour, and an annual publishing heatmap. It also presents the configured Hugo, Stack, deployment, comments, and CMS stack.

These summaries do not require an external analytics service. Waline can optionally provide page-view and comment counts.

## Waline: extending an existing Stack provider

Stack already supports Waline. Liquid Stack overrides the provider rather than claiming a new comment system. The changes add bilingual guidance, engagement counts, theme-matched light and dark styling, custom reaction labels, primary/fallback server probing, comment-toolbar adjustments, and a site-wide page-view total in the footer.

The public starter contains placeholder endpoints; users must supply their own service.

## Friend links: from a compact list to a workflow

Upstream `article/components/links.html` renders a compact link list. Liquid Stack expands it into a platform section, data-driven friend cards, backlink rules, application and contact actions, and an optional embedded application form.

## Languages, SEO, sitemaps, and 404 search

The new `head/language-routing.html` remembers a visitor's language choice and selects the matching English or Chinese page. Head and Open Graph overrides add language routing, favicon handling, and richer social metadata.

Liquid Stack also adds bilingual human-readable sitemaps, an XML sitemap index and multilingual flat sitemap, a 404 page that turns the invalid path into a search query, a world-clock widget, and expanded taxonomy, archive, tag-cloud, and table-of-contents presentation.

## Icons and interaction layer

Upstream Stack's icon helper loads local SVG files. Liquid Stack retains that fallback and adds a consistent mapping for Simple Icons, Lucide, and Phosphor icons used by brands, management services, and interface controls.

The custom front-end layer initializes language behaviour, article sharing, homepage motion, navigation smoothing, the launchpad, photo wall, world clocks, dashboard, management menu, and mobile gestures, with reduced-motion fallbacks.

## CMS and template deployment

Stack does not ship a content-management backend. Liquid Stack exposes Sveltia CMS at `/admin/`; `layouts/admin/section.cmsconfig.yml` and `assets/admin/cms-config-base.yml` generate collections for bilingual posts, categories, launchpad entries, photo-wall items, and other editable data.

The repository also includes a GitHub Pages workflow. After choosing **Use this template**, users can update the identity and URL in `hugo.yaml` and deploy the same site from their own repository.

## The 35 template differences

Liquid Stack overrides these 23 upstream templates:

`404.html`, `article/article.html`, `article/components/details.html`, `article/components/links.html`, `comments/provider/giscus.html`, `comments/provider/waline.html`, `cookies/analytics.html`, `footer/footer.html`, `head/custom.html`, `head/head.html`, `head/opengraph/provider/base.html`, `head/opengraph/provider/twitter.html`, `helper/icon.html`, `sidebar/left.html`, `widget/archives.html`, `widget/categories.html`, `widget/tag-cloud.html`, `widget/toc.html`, `archives.html`, `home.html`, `list.html`, `page/search.html`, and `single.html`.

These 12 templates are new and have no upstream counterpart:

`article/components/share.html`, `head/language-routing.html`, `sidebar/management-menu.html`, `widget/world-clock.html`, `admin/section.cmsconfig.yml`, `index.sitemapflat.xml`, `page/apps.html`, `page/dashboard.html`, `page/pictures.html`, `page/sitemap.html`, `sitemap.xml`, and `sitemapindex.xml`.

That list is the compatibility boundary to review when updating the vendored Stack release.
