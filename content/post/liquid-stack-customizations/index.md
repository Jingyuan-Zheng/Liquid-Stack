---
title: "From Stack v4 to Liquid Stack: What Changed"
description: "A concrete map of the extensions Liquid Stack adds on top of Hugo Theme Stack v4.0.3."
date: 2026-07-21
slug: liquid-stack-customizations
categories: [Tutorials]
tags: [Liquid Stack, Stack v4, Features, Configuration]
---

Liquid Stack is not a replacement for [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack). It vendors Stack v4.0.3 in `themes/hugo-theme-stack/` and adds its own site features through root-level layouts, styles, data files, and scripts. This page explains the boundary so you know what comes from Stack and what this starter changes.

## The Stack v4 foundation stays intact

Stack still provides the core blog experience: Hugo content rendering, responsive navigation, article and list pages, archives, taxonomies, search, colour-scheme switching, multilingual routing, and the theme's normal post metadata and widgets. Your posts remain ordinary Hugo bundles under `content/post/`.

Liquid Stack deliberately leaves the vendored theme as the upstream baseline. Its changes live outside that directory, mainly in `layouts/`, `assets/`, `data/`, and `static/`. That separation makes it easier to inspect an update to Stack before adopting it.

## A profile-style home page, without removing the blog

`layouts/home.html` replaces Stack's standard home-list presentation with a profile header, social links, shortcut cards, recent articles, pagination, and Stack's existing right sidebar. The shortcuts lead to the launchpad, About page, dashboard, and photo wall; the article list and sidebar widgets are still part of the page.

The left sidebar is extended in `layouts/_partials/sidebar/left.html`. It keeps the normal menu, language selector, dark-mode control, and configured icons, while adding an administrator-only management menu triggered from the avatar badge. Links in that menu are data-driven through `data/management_links.yaml`.

## Launchpad: project cards with a real data source

Stack does not include an application launcher. `layouts/page/apps.html` adds one: every entry in `data/launchpad/*.yaml` can define a name, translated label, icon, preview image, related article, and repository URL. The page opens a preview overlay rather than navigating immediately, while the related-article action can point to a public URL when a project is not included in the starter.

Replace the example entries and files in `static/img/launchpad/` with your own projects. The page itself does not need to be rewritten.

## Photo wall with persistent arrangement

`layouts/page/pictures.html`, `data/photo-wall/`, and the gallery code in `assets/ts/custom.ts` turn a normal image gallery into a movable photo wall. Each image has a stable data id, supports portrait and landscape dimensions, can be rearranged in the browser, and can be opened for a focused view. Positions are saved in the visitor's browser, so the source files remain unchanged.

Add one YAML entry per image under `data/photo-wall/` and keep browser-ready images in `static/img/gallery/`.

## Dashboard for content, not analytics tracking

`layouts/page/dashboard.html` builds a site dashboard from Hugo's own content data. It shows the number of published posts and words, running days, category distribution, popular tags, publishing patterns by weekday and hour, and a yearly publishing heatmap. The client-side rendering is in `assets/ts/custom.ts`.

This is a local content summary, not an external analytics service. If you enable comments, the custom Waline integration can also display page-view and comment counts; configure your own Waline endpoint before using it publicly.

## CMS, comments, links, and site utilities

Liquid Stack keeps the management tools that do not ship with Stack:

- `/admin/` loads Sveltia CMS. Its generated configuration comes from `layouts/admin/section.cmsconfig.yml` and `assets/admin/cms-config-base.yml`, including bilingual posts, launchpad entries, and photo-wall data.
- `layouts/_partials/comments/provider/waline.html` restyles and extends Waline comments, including a short configuration notice and engagement counts. The repository uses placeholder service addresses only.
- The friend-links page is a custom data-driven hub with backlink rules and configurable application/contact actions.
- Custom sitemap templates, language-routing metadata, world-clock and taxonomy widgets, footer metadata, and small article-detail overrides round out the site-level utilities.

## What to edit when making it yours

Start with `hugo.yaml` for title, language, menus, social links, and service URLs. Then replace the sample data in `data/launchpad/`, `data/photo-wall/`, and `data/friend-links/`; update the About content; and add your own posts under `content/post/`. Do not edit `themes/hugo-theme-stack/` for site-specific changes—place overrides beside the existing Liquid Stack files instead.

When upgrading Stack, compare the vendored theme with the root-level overrides and test the pages above. That is the trade-off for keeping these additions while still benefiting from the upstream theme.
