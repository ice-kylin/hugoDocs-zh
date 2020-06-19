# 使用 Hugo 模块

> 如何使用 Hugo 模块构建和管理您的网站。

## 先决条件

> Hugo Modules 的大多数命令都需要安装更新版本的 Go（请参阅 https://golang.org/dl/）和相关的 VCS 客户端（例如 Git，请参阅 https://git-scm.com/downloads/） 。 如果您在 Netlify 上运行一个“较旧”的站点，则可能必须在环境变量中将 GO_VERSION 设置为 1.12。
>
> 有关 Go 模块的更多信息，请参见：
>
> https://github.com/golang/go/wiki/Modules
>
> https://blog.golang.org/using-go-modules

## 初始化新模块

使用 `hugo mod init` 初始化新的 Hugo 模块。 如果无法猜测模块路径，则必须将其作为参数提供，例如：

```
hugo mod init github.com/gohugoio/myShortcodes
```

另请参阅命令行工具文档。

## 使用主题模块

对主题使用模块的最简单方法是将其导入配置中。

初始化 hugo 模块系统：`hugo mod init github.com/<your_user>/<your_project>`

将主题导入到您的 `config.toml` 中：

```toml
[module]
  [[module.imports]]
    path = "github.com/spf13/hyde/"
```

## 更新模块

将模块作为导入添加到配置时，将下载并添加模块，请参阅模块导入。

要更新或管理版本，您可以使用 `hugo mod get`。

一些例子：

### 更新所有模块

```
hugo mod get -u
```

### 递归更新所有模块

v0.65.0 的新功能

```
hugo mod get -u ./...
```

### 更新一个模块

```
hugo mod get -u github.com/gohugoio/myShortcodes
```

### 获取特定版本

```
hugo mod get github.com/gohugoio/myShortcodes@v1.0.7
```

另请参阅命令行工具文档。

### 打印依赖图

在相关模块目录中使用 `hugo mod graph` 命令，它将打印依赖关系图，包括供应商，模块更换或禁用状态。

例如：

```
hugo mod graph

github.com/bep/my-modular-site github.com/bep/hugotestmods/mymounts@v1.2.0
github.com/bep/my-modular-site github.com/bep/hugotestmods/mypartials@v1.0.7
github.com/bep/hugotestmods/mypartials@v1.0.7 github.com/bep/hugotestmods/myassets@v1.0.4
github.com/bep/hugotestmods/mypartials@v1.0.7 github.com/bep/hugotestmods/myv2@v1.0.0
DISABLED github.com/bep/my-modular-site github.com/spf13/hyde@v0.0.0-20190427180251-e36f5799b396
github.com/bep/my-modular-site github.com/bep/hugo-fresh@v1.0.1
github.com/bep/my-modular-site in-themesdir
```

另请参阅命令行工具文档。

### 供应商您的模块

`hugo mod vendor` 会将所有模块依赖项写入 `_vendor` 文件夹，该文件夹随后将用于所有后续构建。

注意：

- 您可以在模块树的任何级别上运行 `hugo mod vendor`。
- 供应商将不会存储存储在您的 `themes` 文件夹中的模块。
- 大多数命令接受 `--ignoreVendor` 参数，该标志然后将像模块树中不存在 `_vendor` 文件夹一样运行。

另请参阅命令行工具文档。

### 整理 go.mod，go.sum

运行 `hugo mod tidy` 来删除 `go.mod` 和 `go.sum` 中未使用的条目。

另请参阅命令行工具文档。

### 清理模块缓存

运行 `hugo mod clean` 删除整个模块缓存。

请注意，您还可以使用 `maxAge` 配置 `modules` 缓存，请参见文件缓存。

另请参阅命令行工具文档。

> “Use Hugo Modules” was last updated: June 3, 2020: Fixing typos, whitespace issues and links (f47d6f1e3)
