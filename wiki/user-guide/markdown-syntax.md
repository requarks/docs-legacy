<!-- TITLE: Markdown Syntax -->
<!-- SUBTITLE: Cheatsheet for the markdown syntax -->

# What is Markdown
Markdown is a lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML and many other formats using a tool by the same name. Markdown is often used to format readme files, for writing messages in online discussion forums, and to create rich text using a plain text editor.

# Basics
## Bold
To make a text in bold, simply put double asterisks `**` before and after the desired text:

`To **boldly** go` :arrow_right: To **boldly** go

## Italic

To make a text in italic, simply put a single asterisk `*` before and after the desired text:

`Some *italic* text` :arrow_right: Some *italic* text

## Strikethrough

To make a text in strikethrough, simply put double tildes `~~` before and after the desired text:

`Something ~~not cool~~` :arrow_right: Something ~~not cool~~

# Headers
Headers are useful to break a long page into sections. For example, the page you are currently reading has multiple headers and sub-headers:

- What is Markdown
- Basics
	- Bold
	- Italic
	- Strikethrough
- Headers
- etc...

To define a line as a header, simply put a hash sign **#** at the beginning. The amount of consecutive # you insert defines the level of the header.

```
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

Example:

```
# Section A

## Sub-section A.1

### Sub-sub-section A.1.1

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed at sapien at odio fringilla lobortis.

# Section B

Etc...
```

In the above example, Section A and B are top level headers and Section A has a sub-header (A.1), which contains a sub-header (A.1.1).

# Lists
Unordered lists can be defined using a dash at the beginning of every line:
```markdown
- Item 1
- Item 2
- Item 3
```

Ordered lists can be defined using numbers:
```markdown
1. Item
2. Item
3. Item
```

Note that ordered lists are automatically incremented. You can therefore use `1.` for all items.
# Links
Links to other page or external webpages are defined using the following syntax:

```markdown
[Internal Link Title](/path/to/page)
[External Link Title](https://www.google.com/)
```

A special icon is automatically displayed next to external links to denote the user will leave the site if clicked.
# Images
Images can be inserted in almost the same way as links. They simply require an extra `!` at the beginning:

```
![Image Caption](http://link.to/image.jpg)
```
# Code
## Inline
Inline code provide a quick way to insert `code / commands` without creating a standalone code block. They are enclosed by a single back-tick:

```
`This is an inline code`
```
## Block
If your code requires multiple lines or you need syntax highlighting, it is preferrable to use code blocks. They are enclosed by triple backticks:

````markdown
```
var sample = 'code';

on.multiple(lines) {
	cool();
}
```
````

To add syntax highlighting, simply add the language name right after the opening triple backticks:
````markdown
```js
var sample = 'code';

on.multiple(lines) {
	cool();
}
```
````

# Tables
*Coming soon*
# Blockquotes
Blockquotes are explained in details in the [Editor Blockquotes](https://docs.wiki.requarks.io/user-guide/blockquotes) page.

# Horizontal Rule
Simply put **three (3)** of the following characters to create an horizontal rule: `***` (asterisks) or `---` (hyphens)

Which results in:

---

Always put an empty line above the horizontal rule. Otherwise, Markdown will consider the above line as an header (this is an alternate behavior of Markdown).

# Footnotes
You can easily add footnote references using the `[^x]` syntax (where `x` is a number or name):

```markdown
Here is a footnote reference,[^1] and another.[^longnote]

[^1]: Here is the footnote.

[^longnote]: Here's one with multiple blocks.

    Subsequent paragraphs are indented to show that they
belong to the previous footnote.
```

You can also inline footnotes directly:

```markdown
Here is an inline note.^[Inlines notes are easier to write, since
you don't have to pick an identifier and move down to type the
note.]
```
# Line breaks
Markdown does not handle line breaks the same way most editors do. There're a few differences to be aware of:

**A single line break will not produce a line break once displayed.**

*For example, the following content:*

```markdown
First line here
Second line here
```

*will be displayed as:*

First line hereSecond line here

---

**A line break can be forced by adding 2 spaces at the end of the line.**  
This will indicate to Markdown that the next line should be a new line.

To create a new paragrah, simply press **Enter** twice.

# Icons (emojis)
An extensive list of emojis can be easily inserted into your content. Simply type the emoji code corresponding to the icon you want to use. E.g:

`:apple:` :apple:  
`:date:` :date:

All emoji codes begins and ends with a colon `:`

You can see the full list of available emojis: [http://www.webpagefx.com/tools/emoji-cheat-sheet/](http://www.webpagefx.com/tools/emoji-cheat-sheet/)

Note that the emojis will not display exactly as shown in the above link. This is only a reference page.
