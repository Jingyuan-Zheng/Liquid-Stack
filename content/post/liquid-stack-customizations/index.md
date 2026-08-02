---
title: "Liquid Stack Theme Update: What's New Beyond Stack v4"
description: "A user-friendly guide to Liquid Stack's homepage, launchpad, photo wall, dashboard, CMS, bilingual experience, and comment enhancements."
date: 2026-07-21
lastmod: 2026-08-02
slug: liquid-stack-customizations
categories: [Tutorials]
tags: [Liquid Stack, Stack v4, Theme Update, Hugo]
---

Liquid Stack is built on [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3. It keeps Stack's familiar blogging experience and expands it into a complete personal-site starter for stories, projects, photos, and site information.

You do not need to understand Hugo templates before using it. Select **Use this template** on GitHub, replace the sample identity and content, and start from a working bilingual site.

## A homepage that introduces the whole site

Stack's original homepage focuses on the article feed. Liquid Stack adds a profile-style introduction while keeping the blog beneath it:

- avatar, greeting, site description, and social links;
- shortcut cards for the launchpad, About page, dashboard, and photo wall;
- recent posts plus search, archives, categories, tags, and world clocks;
- responsive layouts for desktop, tablet, mobile, and dark mode.

Visitors can understand the site at a glance and still browse it as a normal blog.

## A project launchpad

The launchpad presents projects like desktop applications. Each item can have an icon, title, preview image, related article, and repository link. Selecting an app opens its preview before taking the visitor to the full story.

Replace the included examples with software, research, design work, downloads, or useful links without rebuilding the page.

## An interactive photo wall

The photo wall supports both portrait and landscape images without forcing them into one crop. Visitors can rearrange photos by dragging them and open an image for a focused view. Their arrangement is remembered in the current browser.

It works for travel photography, portfolios, event memories, design work, or project screenshots.

## A flexible About page

The About page is not limited to a résumé. The starter uses a fictional résumé to demonstrate the original animations, timeline, floating navigation, and section layout.

You can turn it into a personal introduction, a story about the website, a team page, a portfolio history, or a formal résumé.

## A content dashboard

The dashboard reads the site's Hugo content and automatically presents:

- published posts and total word count;
- days online;
- category distribution and popular tags;
- publishing patterns by weekday and hour;
- an annual publishing heatmap;
- Hugo, Stack, deployment, comments, and CMS status.

These summaries work without connecting an external analytics platform.

## Site management remains included

The emoji badge beside the avatar opens a management menu for the CMS, comment moderation, backlink applications, GitHub Pages, search consoles, analytics, and deployment services.

Sveltia CMS remains available at `/admin/`. After connecting your own GitHub repository, it can manage bilingual posts, categories, launchpad projects, and photo-wall entries. The public starter uses generic service placeholders instead of the original author's private backends.

## Comments that match the theme

Stack already supports Waline. Liquid Stack improves how it fits into the site:

- light and dark styling aligned with the theme;
- bilingual commenting guidance;
- page-view and comment totals;
- reply notifications and article reactions;
- optional fallback server support;
- a site-wide page-view total in the footer.

The demo does not connect to a personal comment database. Add your own Waline endpoint when you are ready.

## Friend links as a complete page

The friend-links page expands the original compact list into site cards, exchange rules, application and contact actions, and an optional embedded form. A separate platform area can link to GitHub, portfolios, or other public profiles.

## Better reading and sharing

Articles include print, copy-link, and system-share actions. Chinese pages can share to Weibo, QQ, and X; English pages support X, Reddit, LinkedIn, WhatsApp, and email. Printed articles include author and source attribution.

The 404 page also turns an invalid path into a search query, helping visitors recover instead of stopping at an error.

## One design for English and Simplified Chinese

The English and Chinese versions use the same homepage, sidebar, articles, launchpad, photo wall, About page, and dashboard structure. Only the displayed content changes. The browser remembers the language choice and tries to open the matching translation of the current page.

Liquid Stack also includes bilingual human-readable sitemaps and multilingual XML sitemaps for search engines.

## Replaceable icons and visual assets

The starter includes a consistent icon system plus generic 3D artwork for the avatar, logo, post covers, categories, and launchpad examples. These assets keep a new site visually complete and prevent empty cards or broken images.

Replace them one at a time with your own identity when convenient.

## Stack's original blog features remain

Liquid Stack still uses the official Stack v4.0.3 release as its blog foundation. Article lists, single pages, search, archives, categories, tags, table of contents, related posts, dark mode, and the responsive sidebar remain available.

The additions use Hugo's project-level override system instead of editing the official files under `themes/hugo-theme-stack/`. This preserves the upstream structure while keeping Liquid Stack's features maintainable.

## Who is it for?

Liquid Stack is a useful starting point for:

- personal blogs and digital gardens;
- developer, designer, or researcher portfolios;
- project showcases and download pages;
- photography, travel, and life journals;
- bilingual sites that need a browser-based CMS.

Explore the live demo, then select **Use this template** on GitHub to create your own copy. The public starter keeps the complete framework and example content without publishing the original author's private posts, real résumé, avatar, or service credentials.
