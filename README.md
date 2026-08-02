# Liquid Stack

[简体中文](README.zh.md) · [Live demo](https://liquid-stack.pages.dev/) · [Use this template](https://github.com/new?template_name=Liquid-Stack&template_owner=Jingyuan-Zheng)

Liquid Stack is a complete bilingual Hugo site starter built on the unmodified [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3. It keeps Stack's blog foundation and adds a profile homepage, launchpad, interactive photo wall, content dashboard, Sveltia CMS, enhanced Waline integration, friend-link workflow, bilingual sitemaps, and ready-to-edit sample content.

## Create your site from the template

1. Select **Use this template** on GitHub, then create a public repository.
2. Open `hugo.yaml` and replace `baseURL`, the title, copyright, sidebar text, and social links.
3. Replace the sample data under `data/` and the visual assets under `static/img/`.
4. In **Settings → Pages**, select **GitHub Actions** as the source.
5. Push to `main`. The included workflow builds and publishes the site.

## Quick start

1. Install Hugo Extended.
2. Update `baseURL`, the site title, sidebar text, and social links in `hugo.yaml`.
3. Replace `static/img/liquid-stack/` with your own visual assets.
4. Add posts under `content/post/<slug>/`; use `index.md` for English and `index.zh.md` for Simplified Chinese.
5. Preview with `hugo server -D`, then build with `hugo --minify --cleanDestinationDir --ignoreCache`.

## Deployment

The public demo runs on Cloudflare Pages. Build the site with Hugo Extended 0.161.0 and deploy the generated `public/` directory to Cloudflare Pages or another static host of your choice.

## Customization map

- `hugo.yaml` — site identity, menus, widgets, languages, and theme options
- `content/` — pages, categories, and posts
- `static/img/liquid-stack/` — replaceable sample assets
- `layouts/` — local theme extensions; upstream Stack is vendored under `themes/hugo-theme-stack/`
- `data/launchpad/` — launchpad projects
- `data/photo-wall/` — interactive gallery entries
- `data/friend-links/` — friend-link cards
- `assets/admin/` and `layouts/admin/` — generated Sveltia CMS configuration

The vendored theme matches the official Stack v4.0.3 release. Liquid Stack adds its site features from the project root. See the [theme update overview](https://liquid-stack.pages.dev/p/liquid-stack-customizations/).

Sample text and images are generic placeholders. Replace them before launching your site.

## License

Liquid Stack is distributed under GPL v3.0 or later, consistent with the vendored upstream Stack theme. The full license text is at `themes/hugo-theme-stack/LICENSE`.
