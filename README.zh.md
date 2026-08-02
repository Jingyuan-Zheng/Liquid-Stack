# Liquid Stack

[English](README.md) · [在线 Demo](https://jingyuan-zheng.github.io/Liquid-Stack/zh/) · [使用此模板](https://github.com/new?template_name=Liquid-Stack&template_owner=Jingyuan-Zheng)

Liquid Stack 是一套基于原版 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) v4.0.3 的完整双语 Hugo 站点模板。它保留 Stack 的博客基础，并加入个人主页式首页、启动台、可交互照片墙、内容仪表盘、Sveltia CMS、Waline 扩展、友链申请流程、双语站点地图和可直接替换的示例内容。

## 使用模板创建站点

1. 在 GitHub 点击 **Use this template**，创建一个新的公开仓库。
2. 打开 `hugo.yaml`，替换 `baseURL`、站点名称、版权、侧栏介绍和社交链接。
3. 替换 `data/` 下的示例数据和 `static/img/` 下的通用素材。
4. 在 **Settings → Pages** 中将发布来源设为 **GitHub Actions**。
5. 推送到 `main`；仓库内置的工作流会自动构建并发布站点。

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

官方 Stack 主题文件保持原样，Liquid Stack 的站点功能通过项目根目录扩展。具体更新见[主题更新说明](https://jingyuan-zheng.github.io/Liquid-Stack/zh/p/liquid-stack-customizations/)。

## 许可证

Liquid Stack 与内置的上游 Stack 主题一致，采用 GPL v3.0 或更高版本。完整许可证位于 `themes/hugo-theme-stack/LICENSE`。
