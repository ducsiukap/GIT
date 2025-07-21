# Contents

- [Headings](#heading)
- [Text styling](#text-styling)
- [Lists](#list)
- [Links](#link)
- [Images](#image)
- [Highlight / Embedded Code](#highlight)
- [Tables](#table)
- [Horizontals](#horizontal)
- [Footnotes](#footnote)

<a id="heading"></a>

# Heading

`#` - for `<h1>`  
`##` - for `<h2>`  
`###` - for `<h3>`  
`####` - for `<h4>`  
`#####` - for `<h5>`  
`######` - for `<h6>`

<a id="text-styling"></a>

# Text styling

`*Italic Text*` or `_Italic Text_` for _italic text_  
`**Bold Text**` or `__Bold Text__` for **bold text**  
`***Bold & Italic***` or `___Bold & Italic___` for **_Bold and Italic Text_**  
`~~Text~~` for ~~Strikethrough text~~

<a id="list"></a>

# Lists

### unodered lists

`- item`, `* item` or `+ item`  
ex:

- item1
  - sub-item1

### ordered lists

`1.`, `2.`, `1.1`, ...
ex:

1. item1
2. item2  
   2.1 item2.1  
   2.2 item2.2
3. item3

### task list

`[x] completed task` and `[] incompleted task`

- [x] Completed task
- [ ] Incomplete task

<a id="link"></a>

# Links for navigation

### for external link

`[title](link)`  
ex: Profile:  
[Github](https://github.com/ducsiukap)  
[Instagram](https://www.instagram.com/vduczz/)

### for internal link (anchor link)

1. first, create an id `<a id="my-section"></a>`
2. then, link to it:  
   `[Go to My Section](#my-section)`

<a id="image"></a>

# Images for Visuals

`![Alt text for the image](image_url "Optional title for the image")`  
ex:  
![alt text](https://www.pngkit.com/png/full/755-7556561_small.png "Title text")  
or:
![build](https://img.shields.io/badge/build-passing-brightgreen)
![version](https://img.shields.io/badge/version-1.0-blue)  
read more [shields.io](https://shields.io/badges).

<a id="highlight"></a>

# Highlight / Embedded code

### inline code with ``

ex: `inline code`

### block of code ``````

ex:

```
a block
of code
```

<a id="table"></a>

# Tables

```
| Header 1 | Header 2 | Header 3 |
|----------|:--------:|---------:|
| Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 |
| Row 2 Col 1 | Row 2 Col 2 | Row 2 Col 3 |

--- or :---  default (left aligned)
:---: center aligned
---: right aligned
```

ex:
| A| B |
|---|:---:|
| 1 | 2 |
| 3 | 4 |

<a id="horizontal"></a>

# Horizontal Rules for Section Breaks

`---` for

---

<a id="footnote"></a>

# Footnotes

Here is some text with a footnote. [^1]  
[^1]: This is the content of the footnote.
