# Hugo 模板介绍

Hugo 使用 Go 的 `html/template` 和 `text/template` 库作为模板的基础。

> 以下只是 Go 模板的入门。 要深入了解 Go 模板，请查看官方的 Go 文档。

Go 模板提供了一种非常简单的模板语言，该语言坚持认为只有最基本的逻辑才属于模板或视图层。

## 基本语法

Go 模板是带有变量和函数的 HTML 文件。 Go 模板变量和函数可在 `{{ }}` 中访问。

## 访问预定义变量

预定义变量可以是当前范围中已经存在的变量（例如下面的“变量”部分中的 `.Title` 示例）或自定义变量（例如，同一部分中的 `$address` 示例）。

```
{{ .Title }}
{{ $address }}
```

函数的参数使用空格分隔。 通用语法为：

```
{{ FUNCTION ARG1 ARG2 .. }}
```

以下示例使用输入 1 和 2 调用 add 函数：

```
{{ add 1 2 }}
```

### 通过点表示法访问方法和字段

访问在一个内容前字段中定义的“页面参数” `bar`。

```
{{ .Params.bar }}
```

### 括号可用于将项目分组在一起

```
{{ if or (isset .Params "alt") (isset .Params "caption") }} Caption {{ end }}
```

## 变量

每个 Go 模板都会获取一个数据对象。 在 Hugo 中，每个模板都会传递一个 `Page`。 在下面的示例中，`.Title` 是该 Page 变量中可访问的元素之一。

由于 `Page` 是模板的默认范围，因此可以简单地通过点前缀（`.Title`）访问当前范围（ `.` ——“点”）中的 `Title` 元素：

```html
<title>{{ .Title }}</title>
```

> 自定义变量必须以 `$` 为前缀。

```
{{ $address := "123 Main St." }}
{{ $address }}
```

> 对于 Hugo v0.47 和更早的版本，在 `if` 条件语句或类似的语句中定义的变量在外面不可见。 参见 https://github.com/golang/go/issues/10608。
>
> Hugo 在 Scratch 中创建了解决此问题的方法。

对于 Hugo v0.48 和更高版本，可以使用新的 `=` 运算符（Go 1.11 中的新增功能）重新定义变量。

以下示例仅在这些较新的 Hugo 版本中有效。 该示例在主页上显示“ Var is Hugo Home”，在所有其他页面上显示“ Var is Hugo Page”：

```
{{ $var := "Hugo Page" }}
{{ if .IsHome }}
    {{ $var = "Hugo Home" }}
{{ end }}
Var is {{ $var }}
```

> “Introduction to Hugo Templating” was last updated: June 2, 2020: actually fix index function link this time (b20dba125)
