# Liquid Stack

Liquid Stack is a polished bilingual Hugo starter built on the vendored [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4. It includes a custom profile-style home page, responsive article cards, dark mode, search, archives, taxonomy widgets, and ready-to-edit English and Simplified Chinese sample posts.

## Quick start

1. Install Hugo Extended.
2. Update `baseURL`, the site title, sidebar text, and social links in `hugo.yaml`.
3. Replace `static/img/liquid-stack/` with your own visual assets.
4. Add posts under `content/post/<slug>/`; use `index.md` for English and `index.zh.md` for Simplified Chinese.
5. Preview with `hugo server -D`, then build with `hugo --minify --cleanDestinationDir --ignoreCache`.

## GitHub Pages

The included workflow deploys the generated `public/` folder to GitHub Pages. Set **Settings → Pages → Build and deployment → Source** to **GitHub Actions**, and update `baseURL` before publishing.

## Customization map

- `hugo.yaml` — site identity, menus, widgets, languages, and theme options
- `content/` — pages, categories, and posts
- `static/img/liquid-stack/` — replaceable sample assets
- `layouts/` — local theme extensions; upstream Stack is vendored under `themes/hugo-theme-stack/`

Sample text and images are generic placeholders. Replace them before launching your site.

## License

Liquid Stack is distributed under GPL v3.0 or later, consistent with the vendored upstream Stack theme. The full license text is at `themes/hugo-theme-stack/LICENSE`.
