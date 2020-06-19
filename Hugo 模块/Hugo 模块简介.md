# Hugo 模块

Hugo 模块 是 Hugo 的核心构建模块。 一个模块可以是您的主项目，也可以是一个较小的模块，提供 Hugo 中定义的 7 种组件类型中的一种或多种：static（静态）、content（内容）、layouts（布局）、data（数据）、assets（资产）、i18n 和 archetypes（原型）。

您可以按自己喜欢的任何方式组合模块，甚至可以从非 Hugo 项目中挂载目录，从而形成一个大型的虚拟联合文件系统。

Hugo Modules 由 Go Modules 驱动。 有关 Go 模块的更多信息，请参见：

- https://github.com/golang/go/wiki/Modules
- https://blog.golang.org/using-go-modules

这都是全新的，周围只有几个示例项目：

- https://github.com/bep/docuapi 是在测试此功能时已移植到 Hugo Modules 的主题。 这是将非 Hugo 项目安装到 Hugo 文件夹结构中的一个很好的例子。 它甚至显示了常规 Go 模板中的 JS Bundler 实现。
- https://github.com/bep/my-modular-site 是用于测试的非常简单的站点。
