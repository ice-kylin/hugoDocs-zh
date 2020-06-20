# 配置 Hugo

> 如何配置您的 Hugo 网站。

## 配置文件

Hugo 使用 `config.toml`、`config.yaml` 或 `config.json`（如果在根目录中存在）作为默认网站配置文件。

用户可以使用命令行 `--config` 参数选择使用一个或多个站点配置文件覆盖默认值。

例子：

```
hugo --config debugconfig.toml
hugo --config a.toml,b.toml,c.toml
```

> 可以将多个站点配置文件指定为以逗号分隔的字符串传递给 `--config` 参数。

## 配置目录

除了使用单个站点配置文件之外，还可以使用 `configDir` 目录（默认为 `config/`）来更轻松的维护组织特定于环境的设置。

- 每个文件代表一个配置根对象，例如 Params（参数）、Menus（菜单）、Languages（语言）等。
- 每个目录包含一组文件，这些文件包含特定于环境的设置。
- 可以对文件进行本地化以使其成为特定于语言的文件。

```
├── config
│   ├── _default
│   │   ├── config.toml
│   │   ├── languages.toml
│   │   ├── menus.en.toml
│   │   ├── menus.zh.toml
│   │   └── params.toml
│   ├── production
│   │   ├── config.toml
│   │   └── params.toml
│   └── staging
│       ├── config.toml
│       └── params.toml
```

考虑到以上结构，在运行 `hugo --environment staging` 命令时，Hugo 将使用 `config/_default` 中的所有设置，并在这些设置为基础之上合并 `staging` 中的设置。

> 默认情况下，开发环境是使用 `hugo serve` 命令时， 生产环境是使用 `hugo` 命令时。

## 所有配置设置

以下是 Hugo 定义的变量的完整列表，其默认值用括号括起来。 用户可以选择在其站点配置文件中覆盖这些值。

### archetypeDir (“archetypes”)

Hugo 在其中找到原型文件（内容模板）的目录。 另请参阅模块安装配置，以获取配置此目录的另一种方式（来自 Hugo 0.56）。

### assetDir (“assets”)

Hugo 查找 Hugo Pipes 中使用的资产文件的目录。 另请参阅模块安装配置，以获取配置此目录的另一种方式（来自 Hugo 0.56）。

### baseURL

根的主机名（和路径），例如 https://bep.is/。

### blackfriday

请参阅配置 Blackfriday。

### build

请参阅配置构建。

### buildDrafts (false)

构建时包括草稿。

### buildExpired (false)

包含内容已过期。

### buildFuture (false)

包括将来发布的内容。

### caches

请参阅配置文件缓存

### canonifyURLs (false)

启用以将相对 URL 变为绝对 URL。

### contentDir (“content”)

Hugo 从中读取内容文件的目录。 另请参阅模块安装配置，以获取配置此目录的另一种方式（来自 Hugo 0.56）。

### dataDir (“data”)

Hugo 从中读取数据文件的目录。 另请参阅模块安装配置，以获取配置此目录的另一种方式（来自 Hugo 0.56）。

### defaultContentLanguage (“en”)

没有语言指示符的内容将默认为该语言。

### defaultContentLanguageInSubdir (false)

在 subdir 中呈现默认的内容语言，例如内容 `content/en/`。站点根目录 `/` 将重定向到 `/en/`。

### disableAliases (false)

将禁用别名重定向的生成。请注意，即使设置了 `disableAliases`，别名本身也会保留在页面上。这样做的目的是能够使用自定义输出格式在 `.htaccess`，Netlify `_redirects`文件或类似文件中生成 301 重定向。

### disableHugoGeneratorInject (false)

默认情况下，Hugo 只会在首页的 HTML 头中插入一个 generator meta 标签。您可以关闭它，但如果您不这样做，我们将不胜感激，因为这是观看雨果（Hugo）人气上升的好方法。

### disableKinds ([])

启用禁用所有指定种类的页面。此列表中允许的值："page", "home", "section", "taxonomy", "taxonomyTerm", "RSS", "sitemap", "robotsTXT", "404"。

disableLiveReload（假）

禁用自动实时重新加载浏览器窗口。

disablePathToLower（false）

请勿将网址/路径转换为小写。

enableEmoji（假）

为页面内容启用表情符号表情支持；请参阅表情符号备忘单。

enableGitInfo（假）

为每个页面启用.GitInfo 对象（如果 Hugo 网站由 Git 版本控制）。然后，它将使用该内容文件的最后 git 提交日期来更新每个页面的 Lastmod 参数。

enableInlineShortcodes（假）

启用内联短代码支持。请参阅内联简码。

enableMissingTranslationPlaceholders（false）

如果缺少翻译，请显示一个占位符而不是默认值或空字符串。

enableRobotsTXT（假）

启用生成 robots.txt 文件。

> “Configure Hugo” was last updated: May 27, 2020: Add redirect support to the server (2fd83db96)
