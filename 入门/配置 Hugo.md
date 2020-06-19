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

> “Configure Hugo” was last updated: May 27, 2020: Add redirect support to the server (2fd83db96)
