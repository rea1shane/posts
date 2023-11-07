---
title: Markdown 语法
summary: 一些基本的示例。
tags:
  - markdown
date: 2020-10-02
lastmod: 2023-11-10
---

Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。

## Heading 标题

`H1` - `H6` 代表六个级别的章节标题，`H1` 是最高的章节级别，`H6` 是最低的。语法：

```
# H1

## H2

### H3

#### H4

##### H5

###### H6
```

效果：

# H1

## H2

### H3

#### H4

##### H5

###### H6

## Paragraph 段落

语法：

```
不同的段落之间需要有一行空行。

如果没有空行的话会被视为同一段落
回车符会被视为空格
```

效果：

不同的段落之间需要有一行空行。

如果没有空行的话会被视为同一段落
回车符会被视为空格

## Blockquote 块引用

块引用表示从其他来源引用的内容。语法：

```
> > > 这是一段描述。
> >
> > 这点还不错！
> >
> > > 这是另一段描述。
> >
> > 这个就差点意思...
>
> 这些都是引用。
```

效果：

> > > 这是一段描述。
> >
> > 这点还不错！
> >
> > > 这是另一段描述。
> >
> > 这个就差点意思...
>
> 这些都是引用。

## Footnote 脚注

语法：

```
这是一个脚注。[^1]

[^1]: 这是脚注的内容。

这是另一个脚注。[^2]

[^2]: 这是另一个脚注的内容。
```

效果：

这是一个脚注。[^1]

[^1]: 这是脚注的内容。

这是另一个脚注。[^2]

[^2]: 这是另一个脚注的内容。

## Table 表格

表格可以使用冒号 `:` 来定义表格的对齐方式。语法：

```
| Name  | Age |   Skin | Describe |
|:----- |:---:| ------:| -------- |
| Bob   | 27  |  white | tall     |
| Alice | 23  | yellow | fat      | 
```

效果：

| Name  | Age |   Skin | Describe |
|:----- |:---:| ------:| -------- |
| Bob   | 27  |  white | tall     |
| Alice | 23  | yellow | fat      |

## Code 代码

### Inline code 行内代码

语法：

```
`This is Inline Code`
```

效果：

`This is Inline Code`

### Code block 代码块

#### 通过反引号声明

语法：

    ```
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="utf-8" />
            <title>Example HTML5 Document</title>
        </head>
        <body>
            <p>Test</p>
        </body>
    </html>
    ```

效果：

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Example HTML5 Document</title>
    </head>
    <body>
        <p>Test</p>
    </body>
</html>
```

可以在前面的三个反引号后声明代码的语言种类，语法：

    ```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="utf-8" />
            <title>Example HTML5 Document</title>
            <meta name="description" content="Sample article showcasing basic Markdown syntax and formatting for HTML elements.">
        </head>
        <body>
            <p>Test</p>
        </body>
    </html>
    ```

效果：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Example HTML5 Document</title>
        <meta name="description" content="Sample article showcasing basic Markdown syntax and formatting for HTML elements.">
    </head>
    <body>
        <p>Test</p>
    </body>
</html>
```

#### 通过四个空格声明

语法：

```
    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>
```

效果：

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

## List 列表

### Ordered list 有序列表

语法：

```
1.  First item
	1.  Sub 1
	2.  Sub 2
	3.  Sub 3
2.  Second item
3.  Third item
```

或者：

```
1.  First item
	1.  Sub 1
	1.  Sub 2
	1.  Sub 3
1.  Second item
1.  Third item
```

效果：

1.  First item
	1.  Sub 1
	1.  Sub 2
	1.  Sub 3
1.  Second item
1.  Third item

### Nested list 无序列表

语法：

```
-   Fruit
    -   Apple
    -   Orange
    -   Banana
-   Dairy
    -   Milk
    -   Cheese
```

效果：

-   Fruit
    -   Apple
    -   Orange
    -   Banana
-   Dairy
    -   Milk
    -   Cheese

## Image 图片

语法：

```
![图片加载失败时显示的文字](assets/example.png "鼠标悬浮时的提示")
```

效果：

![图片加载失败时显示的文字](assets/example.png "鼠标悬浮时的提示")

## Dividing line 分割线

语法：

```
---
```

效果：

---

## 其他

| 名称   | 语法                                                   | 效果                                                 |
| ------ | ------------------------------------------------------ | ---------------------------------------------------- |
| 粗体   | `**bold**`                                             | **bold**                                             |
| 斜体   | `_italics_`                                            | _italics_                                            |
| 粗斜体 | `_**text**_`                                           | _**text**_                                           |
| 删除线 | `~~delete~~`                                           | ~~delete~~                                           |
| 缩写   | `<abbr title="Graphics Interchange Format">GIF</abbr>` | <abbr title="Graphics Interchange Format">GIF</abbr> |
| 下标   | `H<sub>2</sub>O`                                       | H<sub>2</sub>O                                       |
| 上标   | `X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>`        | X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>        |
| 按键   | `<kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd>`     | <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd>     |
| 标记   | `<mark>mark</mark>`                                    | <mark>mark</mark>                                    |

## 相关链接

- [Basic Syntax | Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [styleguide/style.md at gh-pages · google/styleguide · GitHub](https://github.com/google/styleguide/blob/gh-pages/docguide/style.md)
- [styleguide/markdown.md at master · fex-team/styleguide · GitHub](https://github.com/fex-team/styleguide/blob/master/markdown.md)
