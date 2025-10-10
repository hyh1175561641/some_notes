翻译Markdow的使用方法及手册

[TOC]
# Quick Start 快速入门

# Welcome欢迎

Thank you for choosing **Typora**. This document will help you to start Typora.
感谢你选择了**Typora**。这篇文档将帮助你入门Typora。



## Live Preview及时预览

**Typora** use the feature: *Live Preview*, meaning that you could see these inline styles after you finish typing, and see block styles when you type or after you press `Enter` key or focus to another paragraph. Just try to type some markdown in typora, and you would see how it works.

**Note**: Markdown tags for inline styles, such as `**` will be hidden or displayed smartly. Markdown tags for block level styles, such as `###` or `- [x]` will be hidden once the block is rendered.

## Markdown For Typora Typora使用Markdown语言*为typora定制的markdown*

**Typora** is using [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/), For more detail, please open [Markdown Reference](Markdown%20Reference.md).
**Typora**是使用了GitHub Flavored Markdown，为更多细节，请打开Markdown Reference。

To see full markdown Syntax references and extra usage, please check `Help`->`Markdown Reference` in menu bar.
了解完整的Markdown语法手册和，请在菜单栏点击`Help`->`Markdown Reference`

## Useful Shortcuts 实用的快捷键

#### Writing Assist Key

`Esc` key will trigger assistant behavior, like open inline preview for inline math, auto-complete for emoji, etc. More behavior will be supported in future.

#### Actions

- Select word: cmd+D
- Delete word: shift+cmd+D
- Select line/sentence: cmd+L
- Select row in table: cmd+L
- Add row in table: cmd+Enter
- Select Styled Scope (or cell in a table) cmd+E
- Jump to selection: cmd+J
- Jump to Top: cmd+↑
- Jump To Bottom: cmd+↓
- Increase/decrease heading level from `<p>` to `<h1>`: cmd+-/+
- New line: shift+Return
- Move table row/column: ⌘ + ⌃ + arrow key.

#### Styles

Please check the `Paragraph` and `Format` menu in menu bar.

#### Custom Shortcut Keys

Most shortcut keys are configurable, see [this document](Custom-Key-Binding/) for detail.

## Outline

Mouse over the windows toolbar and click the outline icon on the right top of the window can open outline panel. This Panel can be pinned to left side.

## Word Count

Mouse over the windows toolbar will make word count visible. "Always show word count" can be set from preference panel. Click it will popup detailed word count tooltip. If a range of text is selected word count for selection will also be displayed on word count tooltip.

## Quick Open

Currently Typora only provides a simple "Quick Open" function. Recent opened files, files from same folder or context folder (like a git repository) will be include in quick open file list. This features replies on OS X Spotlight to work correctly.

## Copy

We create typora and want to make it your default markdown editor, thus copy and paste means copy from another app or paste to another app, instead of *copy/paste from/to another markdown editor*. Therefore, by default, `Copy` means `Copy As HTML` ( and `Paste` means `Paste from HTML`). 

However, after click "**Copy Markdown source by default**", typora will copy selected text in HTML/markdown format (When pasting, rich editors will accept the HTML format, while plain text / code editor will accept the markdown source code format).

To **copy Markdown source code** explicitly, please use shortcut key `shift+cmd+c` or `Copy as Markdown` from menu. To **Copy as HTML Code**, please select `Copy as HTML Code` from menu.

## Smart Paste

**Typora** is able to analyze styles of the text content in your clipboard when pasting. For example, after pasting a `<h1>HEADING</h1>` from some website, typora will keep the 'first level heading’ format instead of paste ‘heading’ as plain text. 

To **paste as markdown source** or plain text, you should use `paste as plain text` or press the shortcut key: `shift+cmd+v`.

## Themes 主题

Please refer to `Help` → `Custom Themes` from menu bar.
请从菜单栏查找`Help`→`Custom Themes`。

## Publish 

Currently Typora only support to export as **PDF** or **HTML**. More data format support as import/export will be integrated in future.

## Command Line Tool 命令行工具

To launch typora from Terminal, you could add
从终端启动typora，你可以添加

```bash
alias typora="open -a typora"
```

in your `.bash\_profile` or other configuration file, then you would be able to do `typora file.md` for opening files by typora from shell/terminal.

## More Useful Tips & Documents 更多有用的提示和文档

<http://support.typora.io/>

## And More ? 更多？

For more questions or feedbacks, please contact us by:

- Home Page: http://typora.io
- Email: <hi@typora.io>
- Twitter [@typora](https://twitter.com/typora)

We opened a Github issue page in case you want to start a discussion or as an alternative way to report bugs/suggestions: https://github.com/typora/typora-issues/issues


# ################
# Markdown Reference 使用手册

# Markdown For Typora Typora使用Markdown语言

## Overview 概述

**Markdown** is created by [Daring Fireball](http://daringfireball.net/); the original guideline is [here](http://daringfireball.net/projects/markdown/syntax). Its syntax, however, varies between different parsers or editors. **Typora** is using [GitHub Flavored Markdown][GFM].
**Markdown**出自Daring Fireball之手；原始准则出自这里。但是它的语法在不同解析器或编辑器之间是不同的。**Typora**使用GitHub Flavored Markdown来作为语法标准。
**Markdown**是[Daring Fireball](http://daringfireball.net/)创建的;组织坐落在


## Block Elements[^elements] 块元素

### Paragraph and line breaks

A paragraph is simply one or more consecutive lines of text. In markdown source code, paragraphs are separated by two or more blank lines. In Typora, you only need one blank line (press `Return` once) to create a new paragraph.

Press `Shift` + `Return` to create a single line break. Most other markdown parsers will ignore single line breaks, so in order to make other markdown parsers recognize your line break, you can leave two spaces at the end of the line, or insert `<br/>`.

### Headers

Headers use 1-6 hash (`#`) characters at the start of the line, corresponding to header levels 1-6. For example:

``` markdown
# This is an H1

## This is an H2

###### This is an H6
```

In Typora, input ‘#’s followed by title content, and press `Return` key will create a header.

### Blockquotes

Markdown uses email-style > characters for block quoting. They are presented as:

``` markdown
> This is a blockquote with two paragraphs. This is first paragraph.
>
> This is second pragraph. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.



> This is another blockquote with one paragraph. There is three empty line to seperate two blockquote.
```

In Typora, inputting ‘>’ followed by your quote contents will generate a quote block. Typora will insert a proper ‘>’ or line break for you. Nested block quotes (a block quote inside another block quote) by adding additional levels of ‘>’.

### Lists

Input `* list item 1` will create an unordered list - the `*` symbol can be replace with `+` or `-`.

Input `1. list item 1` will create an ordered list - their markdown source code is as follows:

``` markdown
## un-ordered list
*   Red
*   Green
*   Blue

## ordered list
1.  Red
2. 	Green
3.	Blue
```

### Task List

Task lists are lists with items marked as either [ ] or [x] (incomplete or complete). For example:

``` markdown
- [ ] a task list item
- [ ] list syntax required
- [ ] normal **formatting**, @mentions, #1234 refs
- [ ] incomplete
- [x] completed
```

You can change the complete/incomplete state by clicking on the checkbox before the item.

### (Fenced) Code Blocks

Typora only supports fences in GitHub Flavored Markdown. Original code blocks in markdown are not supported.

Using fences is easy: Input \`\`\` and press `return`. Add an optional language identifier after \`\`\` and we'll run it through syntax highlighting:

``` markdown
Here's an example:

​```
function test() {
  console.log("notice the blank line before this function?");
}
​```

syntax highlighting:
​```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
​```
```

### Math Blocks数学块

You can render *LaTeX* mathematical expressions using **MathJax**.

To add a mathematical expression, input `$$` and press the 'Return' key. This will trigger an input field which accepts *Tex/LaTex* source. For example:


$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$


In the markdown source file, the math block is a *LaTeX* expression wrapped by a pair of ‘$$’ marks:

``` markdown
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
```

You can find more details [here](http://support.typora.io/Math/).

### Tables

Input `| First Header  | Second Header |` and press the `return` key. This will create a table with two columns.

After a table is created, putting focus on that table will open up a toolbar for the table where you can resize, align, or delete the table. You can also use the context menu to copy and add/delete individual columns/rows.

The full syntax for tables is described below, but it is not necessary to know the full syntax in detail as the markdown source code for tables is generated automatically by Typora.

In markdown source code, they look like:

``` markdown
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

You can also include inline Markdown such as links, bold, italics, or strikethrough in the table.

Finally, by including colons (`:`) within the header row, you can define text in that column to be left-aligned, right-aligned, or center-aligned:

``` markdown
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

A colon on the left-most side indicates a left-aligned column; a colon on the right-most side indicates a right-aligned column; a colon on both sides indicates a center-aligned column.

### Footnotes 脚注

``` markdown
You can create footnotes like this[^footnote].
你可以这样创建脚注[^脚注]。

[^footnote]: Here is the *text* of the **footnote**.
[^脚注]: 这是上句 **文字** 的**脚注**。
```

will produce示例:

You can create footnotes like this[^footnote].
你可以这样创建脚注[^脚注].

[^footnote]: Here is the *text* of the **footnote**.
[^脚注]: 这是上句 **文字** 的**脚注**。

Hover over the ‘footnote’ superscript to see content of the footnote.
将鼠标悬停在"脚注"的上标以查看脚注的内容.


### Horizontal Rules

Inputting `***` or `---` on a blank line and pressing `return` will draw a horizontal line.

------

### YAML Front Matter

Typora now supports [YAML Front Matter](http://jekyllrb.com/docs/frontmatter/). Input `---` at the top of the article and then press `Return` to introduce a metadata block. Alternatively, you can insert a metadata block from the top menu of Typora.

### Table of Contents (TOC)

Input `[toc]` and press the `Return` key. This will create a  “Table of Contents” section. The TOC extracts all headers from the document, and its contents are updated automatically as you add to the document.

## Span Elements[^elements] 行内元素

Span elements will be parsed and rendered right after typing. Moving the cursor in middle of those span elements will expand those elements into markdown source. Below is an explanation of the syntax for each span element.

### Links

Markdown supports two styles of links: inline and reference.

In both styles, the link text is delimited by [square brackets].

To create an inline link, use a set of regular parentheses immediately after the link text’s closing square bracket. Inside the parentheses, put the URL where you want the link to point, along with an optional title for the link, surrounded in quotes. For example:

``` markdown
This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.
```

will produce:

This is [an example](http://example.com/"Title") inline link. (`<p>This is <a href="http://example.com/" title="Title">`)

[This link](http://example.net/) has no title attribute. (`<p><a href="http://example.net/">This link</a> has no`)

#### Internal Links

**You can set the href to headers**, which will create a bookmark that allow you to jump to that section after clicking. For example:

Command(on Windows: Ctrl) + Click [This link](#block-elements) will jump to header `Block Elements`. To see how to write that, please move cursor or click that link with `⌘` key pressed to expand the element into markdown source.

#### Reference Links

Reference-style links use a second set of square brackets, inside which you place a label of your choosing to identify the link:

``` markdown
This is [an example][id] reference-style link.

Then, anywhere in the document, you define your link label on a line by itself like this:

[id]: http://example.com/  "Optional Title Here"
```

In Typora, they will be rendered like so:

This is [an example][id] reference-style link.

[id]: http://example.com/	"Optional Title Here"

The implicit link name shortcut allows you to omit the name of the link, in which case the link text itself is used as the name. Just use an empty set of square brackets — for example, to link the word “Google” to the google.com web site, you could simply write:

``` markdown
[Google][]
And then define the link:

[Google]: http://google.com/
```

In Typora, clicking the link will expand it for editing, and command+click will open the hyperlink in your web browser.

### URLs

Typora allows you to insert URLs as links, wrapped by `<`brackets`>`.

`<i@typora.io>` becomes <i@typora.io>.

Typora will also automatically link standard URLs. e.g: www.google.com.

### Images

Images have similar syntax as links, but they require an additional `!` char before the start of the link. The syntax for inserting an image looks like this:

``` markdown
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
```

You are able to use drag & drop to insert an image from an image file or your web browser. You can modify the markdown source code by clicking on the image. A relative path will be used if the image that is added using drag & drop is in same directory or sub-directory as the document you're currently editing.

If you’re using markdown for building websites, you may specify a URL prefix for the image preview on your local computer with property `typora-root-url` in YAML Front Matters. For example, input `typora-root-url:/User/Abner/Website/typora.io/` in YAML Front Matters, and then `![alt](/blog/img/test.png)` will be treated as `![alt](file:///User/Abner/Website/typora.io/blog/img/test.png)` in Typora.

You can find more details [here](https://support.typora.io/Images/).

### Emphasis

Markdown treats asterisks (`*`) and underscores (`_`) as indicators of emphasis. Text wrapped with one `*` or `_` will be wrapped with an HTML `<em>` tag. E.g:

``` markdown
*single asterisks*

_single underscores_
```

output:

*single asterisks*

_single underscores_

GFM will ignore underscores in words, which is commonly used in code and names, like this:

> wow_great_stuff
>
> do_this_and_do_that_and_another_thing.

To produce a literal asterisk or underscore at a position where it would otherwise be used as an emphasis delimiter, you can backslash escape it:

``` markdown
\*this text is surrounded by literal asterisks\*
```

Typora recommends using the `*` symbol.

### Strong

A double `*` or `_` will cause its enclosed contents to be wrapped with an HTML `<strong>` tag, e.g:

``` markdown
**double asterisks**

__double underscores__
```

output:

**double asterisks**

__double underscores__

Typora recommends using the `**` symbol.

### Code

To indicate an inline span of code, wrap it with backtick quotes (`). Unlike a pre-formatted code block, a code span indicates code within a normal paragraph. For example:

``` markdown
Use the `printf()` function.
```

will produce:

Use the `printf()` function.

### Strikethrough

GFM adds syntax to create strikethrough text, which is missing from standard Markdown.

`~~Mistaken text.~~` becomes ~~Mistaken text.~~

### Underlines

Underline is powered by raw HTML.

`<u>Underline</u>` becomes <u>Underline</u>.

### Emoji :smile:

Input emoji with syntax `:smile:`.

User can trigger auto-complete suggestions for emoji by pressing `ESC` key, or trigger it automatically after enabling it on preference panel. Also, inputting UTF-8 emoji characters directly is also supported by going to `Edit` -> `Emoji & Symbols` in the menu bar (macOS).

### Inline Math

To use this feature, please enable it first in the `Preference` Panel -> `Markdown` Tab. Then, use `$` to wrap a TeX command. For example: `$\lim_{x \to \infty} \exp(-x) = 0$` will be rendered as LaTeX command.

To trigger inline preview for inline math: input “$”, then press the `ESC` key, then input a TeX command.

You can find more details [here](http://support.typora.io/Math/).

### Subscript

To use this feature, please enable it first in the `Preference` Panel -> `Markdown` Tab. Then, use `~` to wrap subscript content. For example: `H~2~O`, `X~long\ text~`/

### Superscript

To use this feature, please enable it first in the `Preference` Panel -> `Markdown` Tab. Then, use `^` to wrap superscript content. For example: `X^2^`.

### Highlight

To use this feature, please enable it first in the `Preference` Panel -> `Markdown` Tab. Then, use `==` to wrap highlight content. For example: `==highlight==`.

## HTML

You can use HTML to style content what pure Markdown does not support. For example, use `<span style="color:red">this text is red</span>` to add text with red color.

### Embed Contents

Some websites provide iframe-based embed code which you can also paste into Typora. For example:

```Markdown
<iframe height='265' scrolling='no' title='Fancy Animated SVG Menu' src='http://codepen.io/jeangontijo/embed/OxVywj/?height=265&theme-id=0&default-tab=css,result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>
```

### Video

You can use the `<video>` HTML tag to embed videos. For example:

```Markdown
<video src="xxx.mp4" />
```

### Other HTML Support

You can find more details [here](http://support.typora.io/HTML/).

[GFM]: https://help.github.com/articles/github-flavored-markdown/



[^elements]: block elements：块级元素，块级元素是可以单独成一行，可以自立门户的独立元素。像主语。<br/>span elements：行级元素，行级元素是修饰字型，是依附于其他文字的元素。像形容词。


















