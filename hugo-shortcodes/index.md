---
title: Hugo shortcodes
summary: 将 HTML 封装为函数。
tags: [hugo]
date: 2024-04-14
lastmod: 2024-04-14
---

shortcode 是内容文件中调用内置或自定义模板的简单片段。

shortcode 的好处是抽象了 HTML 片段，一次定义多次调用，大大降低了编写和维护的成本，能方便地保持重复内容的一致性，就像编程语言中的函数一样。

{{< admonition warning >}}
部分 shortcode 因为其实现代码或懒加载行为，可能会造成页面布局偏移问题，影响页面的 [CLS 分数](https://web.dev/cls/)。
{{< /admonition >}}

## 自定义

要自定义 shortcode，需要将 HTML 源码放到 `layouts/shortcodes` 目录下，HTML 文件的名称即为 shortcode 的名称。

### Admonition 提醒

{{< admonition note >}}
Fork from [martignoni/hugo-notice: A Hugo theme component to display nice notices](https://github.com/martignoni/hugo-notice).
{{< /admonition >}}

在写作和文档撰写中，admonition 是一种用于强调或提醒读者的特殊文本块或元素。admonition 通常以一种特定的样式或格式呈现，以引起读者的注意。这种元素通常用于突出重要信息、提供警告、注意事项、提示或其他特殊类型的内容。

语法：

```
{{</* admonition note */>}}
用户即使在略读内容时也应该了解的有用信息。
{{</* /admonition */>}}

{{</* admonition tip */>}}
有助于更好或更轻松地做事的建议。
{{</* /admonition */>}}

{{</* admonition important */>}}
用户为实现目标需要了解的关键信息。
{{</* /admonition */>}}

{{</* admonition warning */>}}
需要用户立即注意以避免出现问题的紧急信息。
{{</* /admonition */>}}

{{</* admonition caution */>}}
针对某些行动的风险或负面结果提出建议。
{{</* /admonition */>}}

{{</* admonition changelog */>}}
文章的变动历史。
{{</* /admonition */>}}
```

效果：

{{< admonition note >}}
用户即使在略读内容时也应该了解的有用信息。
{{< /admonition >}}

{{< admonition tip >}}
有助于更好或更轻松地做事的建议。
{{< /admonition >}}

{{< admonition important >}}
用户为实现目标需要了解的关键信息。
{{< /admonition >}}

{{< admonition warning >}}
需要用户立即注意以避免出现问题的紧急信息。
{{< /admonition >}}

{{< admonition caution >}}
针对某些行动的风险或负面结果提出建议。
{{< /admonition >}}

{{< admonition changelog >}}
文章的变动历史。
{{< /admonition >}}

## 显示 shortcode 源代码

要想让 shortcode 在页面中不渲染，而是显示其源代码，需要在 shortcode 中添加 `/* */`，如：

```
{{</* admonition note */>}}
用户即使在略读内容时也应该了解的有用信息。
{{</* /admonition */>}}
```

变为：

```
{{</*/* admonition note */*/>}}
用户即使在略读内容时也应该了解的有用信息。
{{</*/* /admonition */*/>}}
```

## 相关链接

- [Shortcodes | Hugo](https://gohugo.io/content-management/shortcodes/)
- [How to display the source code of a shortcode in a code block？ - support - HUGO](https://discourse.gohugo.io/t/how-to-display-the-source-code-of-a-shortcode-in-a-code-block/48717)
