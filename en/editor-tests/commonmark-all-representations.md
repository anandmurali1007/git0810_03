---
guid: a6ee3671-af6d-41cd-9c52-8ece08d9b10c
title: "CommonMark — Every Way to Write Each Construct"
seo:
  title: "CommonMark — Every Way to Write Each Construct"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

# CommonMark — Every Way to Write Each Construct

CommonMark 0.31.2. Most constructs have more than one valid spelling. This file lists
them all, one construct at a time, and — more importantly — flags which alternatives
are **truly interchangeable** and which only look interchangeable.

Each section gives a table of forms, then the **source**, then the **rendered result**
below it so you can see it live.

---

## Index

| Construct | Distinct forms | All equivalent? |
|---|:--:|---|
| [Thematic break](#thematic-break) | 3 characters × many spacings | Yes |
| [Heading H1](#heading-level-1) | 2 (ATX, Setext `=`) | Yes |
| [Heading H2](#heading-level-2) | 2 (ATX, Setext `-`) | Yes |
| [Headings H3–H6](#headings-level-3-to-6) | 1 (ATX only) | — |
| [ATX closing sequence](#atx-closing-sequences) | 2 (open, closed) | Yes |
| [Code block](#code-blocks) | 3 (indented, ``` fence, ~~~ fence) | **No** |
| [Block quote marker](#block-quotes) | 2 (`>`, `> `) | Yes |
| [Bullet list marker](#bullet-lists) | 3 (`-`, `+`, `*`) | **No** |
| [Ordered list delimiter](#ordered-lists) | 2 (`.`, `)`) | **No** |
| [Emphasis](#emphasis) | 2 (`*`, `_`) | **No** |
| [Strong](#strong-emphasis) | 2 (`**`, `__`) | **No** |
| [Strong + emphasis](#strong-plus-emphasis) | 6+ combinations | Yes |
| [Code span](#code-spans) | Any backtick count | Yes |
| [Link](#links) | 5 (inline + 3 reference + autolink) | Mostly |
| [Link destination](#link-destinations) | 2 (bare, `<>`-wrapped) | Yes |
| [Link title](#link-titles) | 3 (`"`, `'`, `()`) | Yes |
| [Image](#images) | Same 4 as links | Mostly |
| [Hard line break](#hard-line-breaks) | 2 (2 spaces, `\`) | Yes |
| [Escaping a character](#escaping-a-character) | 3 (`\`, named entity, numeric) | Yes |
| [A character reference](#character-references) | 3 (named, decimal, hex) | Yes |
| [Raw HTML](#raw-html) | 7 block conditions + inline | — |

---

## Thematic break

Three or more `-`, `_`, or `*`. Any amount of internal spacing. Up to 3 leading
spaces. All produce the same `<hr />`.

| Form | Example |
|---|---|
| Hyphens | `---` |
| Asterisks | `***` |
| Underscores | `___` |
| More than three | `--------` |
| Internal spaces | `- - -` |
| Leading indent (≤3) | `   ***` |

**Source**

```text
---

***

___

- - -

_____________________________________

   * * *
```

**Renders as**

---

***

___

- - -

_____________________________________

   * * *

⚠️ `---` directly under a paragraph line is a **Setext H2**, not a break. Use `***`
when you need an unambiguous rule.

---

## Heading level 1

Two forms. Identical output.

| Form | Syntax |
|---|---|
| ATX | `# Text` |
| Setext | `Text` then a line of `=` |

**Source**

```text
# ATX style heading one

Setext style heading one
========================

Setext with a single equals
=
```

**Renders as**

# ATX style heading one

Setext style heading one
========================

Setext with a single equals
=

The underline can be any length from 1 character up.

---

## Heading level 2

Two forms. Identical output.

| Form | Syntax |
|---|---|
| ATX | `## Text` |
| Setext | `Text` then a line of `-` |

**Source**

```text
## ATX style heading two

Setext style heading two
------------------------
```

**Renders as**

## ATX style heading two

Setext style heading two
------------------------

---

## Setext headings span multiple lines

A capability ATX does not have — the heading content can wrap.

**Source**

```text
Foo *bar*
and baz
=========
```

**Renders as**

Foo *bar*
and baz
=========

---

## Headings level 3 to 6

**Only one form.** Setext has no equivalent beyond level 2.

**Source**

```text
### Level three
#### Level four
##### Level five
###### Level six
```

**Renders as**

### Level three
#### Level four
##### Level five
###### Level six

Seven hashes is not a heading — `####### foo` stays a paragraph.

---

## ATX closing sequences

Optional and cosmetic. The closing run may be any length and does not have to match
the opening.

**Source**

```text
## Open form

## Closed form ##

## Mismatched lengths ##########

##
```

**Renders as**

## Open form

## Closed form ##

## Mismatched lengths ##########

##

The last one is an empty heading, which is legal.

---

## ATX leading indentation

Up to 3 spaces. The fourth space makes it a code block instead.

**Source**

```text
# no indent
 # one space
  # two spaces
   # three spaces
    # four spaces — this is a code block
```

**Renders as**

# no indent
 # one space
  # two spaces
   # three spaces
    # four spaces — this is a code block

---

## Code blocks

Three forms, and they are **not** interchangeable.

| Form | Syntax | Language tag? | Blank lines inside? | Can hold other fences? |
|---|---|:--:|:--:|:--:|
| Indented | 4 spaces or 1 tab | No | Yes, if still indented | Yes |
| Backtick fence | ` ``` ` | Yes | Yes | Only tilde fences |
| Tilde fence | `~~~` | Yes | Yes | Yes, including backticks |

### Indented

**Source**

```text
    a simple
      indented code block
```

**Renders as**

    a simple
      indented code block

An indented block cannot interrupt a paragraph, and has no place for a language tag.

### Backtick fenced

**Source**

`````text
```
plain fence
```

```ruby
def foo(x)
  return 3
end
```

````
Four backticks, so three backticks can appear inside:
```
````
`````

**Renders as**

```
plain fence
```

```ruby
def foo(x)
  return 3
end
```

````
Four backticks, so three backticks can appear inside:
```
````

### Tilde fenced

**Source**

``````text
~~~
plain tilde fence
~~~

~~~python
print("with a language tag")
~~~

~~~
This holds a backtick fence:
```
no problem
~~~
``````

**Renders as**

~~~
plain tilde fence
~~~

~~~python
print("with a language tag")
~~~

~~~
This holds a backtick fence:
```
no problem
~~~

The rule that separates them: **a backtick info string may not contain backticks; a
tilde info string may.** The closing fence must use the same character and be at
least as long as the opening one.

---

## Block quotes

Two marker forms, identical output, plus lazy continuation.

| Form | Syntax |
|---|---|
| Marker + space | `> text` |
| Marker alone | `>text` |
| Lazy | marker on first line only |

**Source**

```text
> with a space
>without a space

> lazy continuation means
this line joins the quote

>> nested
>>> deeper
```

**Renders as**

> with a space
>without a space

> lazy continuation means
this line joins the quote

>> nested
>>> deeper

One optional space after `>` is stripped. Laziness applies to **paragraph
continuation only** — a heading or list on an unmarked line leaves the quote.

---

## Bullet lists

Three markers. **Not interchangeable within one list** — changing the character
starts a new list.

| Form | Syntax |
|---|---|
| Hyphen | `- item` |
| Plus | `+ item` |
| Asterisk | `* item` |

**Source**

```text
- one
- two

+ three
+ four

* five
* six
```

**Renders as**

- one
- two

+ three
+ four

* five
* six

That is three separate `<ul>` elements, not one list of six items.

---

## Ordered lists

Two delimiters, and any start number. **Changing the delimiter starts a new list.**

| Form | Syntax |
|---|---|
| Period | `1. item` |
| Parenthesis | `1) item` |

**Source**

```text
1. period delimiter
2. second

1) paren delimiter
2) second

57. a custom start
58. renumbered from 57

1. five
7. hundred
3. numbers after the first are ignored
```

**Renders as**

1. period delimiter
2. second

1) paren delimiter
2) second

57. a custom start
58. renumbered from 57

1. five
7. hundred
3. numbers after the first are ignored

Start numbers 0 to 999999999 are honoured. Only the **first** item's number matters.
An ordered list can only interrupt a paragraph if it starts at `1`.

---

## Tight vs loose lists

Same markers, different blank lines, genuinely different output.

**Source**

```text
- tight
- list

* loose

* list
```

**Renders as**

- tight
- list

* loose

* list

**HTML output**

```html
<ul><li>tight</li><li>list</li></ul>
<ul><li><p>loose</p></li><li><p>list</p></li></ul>
```

---

## Emphasis

Two markers. **Not interchangeable** — they differ inside words.

| Form | Syntax | Works intraword? |
|---|---|:--:|
| Asterisk | `*text*` | Yes |
| Underscore | `_text_` | No |

**Source**

```text
*asterisk emphasis* and _underscore emphasis_

intraword*works*fine

intraword_does_not_work
```

**Renders as**

*asterisk emphasis* and _underscore emphasis_

intraword*works*fine

intraword_does_not_work

This falls out of the left/right-flanking delimiter-run rules, which treat a
letter on both sides as disqualifying for `_`.

---

## Strong emphasis

Same split as above.

**Source**

```text
**asterisk strong** and __underscore strong__

intraword**works** but intraword__does__not
```

**Renders as**

**asterisk strong** and __underscore strong__

intraword**works** but intraword__does__not

---

## Strong plus emphasis

Many spellings, all producing `<em><strong>` or `<strong><em>`.

**Source**

```text
***triple asterisk***

___triple underscore___

**_mixed one_**

*__mixed two__*

**bold with *nested italic* inside**

*italic with **nested bold** inside*
```

**Renders as**

***triple asterisk***

___triple underscore___

**_mixed one_**

*__mixed two__*

**bold with *nested italic* inside**

*italic with **nested bold** inside*

---

## Code spans

Any number of backticks, as long as the opening and closing runs are equal. The count
never changes the output — it only changes what you can put inside.

**Source**

````text
`one backtick`

``two backticks``

``holds a ` literal backtick``

` `` `

`  padded — one space each side is stripped  `
````

**Renders as**

`one backtick`

``two backticks``

``holds a ` literal backtick``

` `` `

`  padded — one space each side is stripped  `

One leading and one trailing space is stripped when **both** are present and the
content is not entirely spaces.

---

## Links

Five forms. The three reference forms differ only in what you type; the output is
identical.

| Form | Syntax | Needs a definition? |
|---|---|:--:|
| Inline | `[text](/url)` | No |
| Full reference | `[text][label]` | Yes |
| Collapsed reference | `[text][]` | Yes |
| Shortcut reference | `[text]` | Yes |
| Autolink | `<https://url>` | No |

**Source**

```text
[inline](https://example.com)

[full reference][label]

[collapsed][]

[shortcut]

<https://example.com>

[label]: https://example.com
[collapsed]: https://example.com
[shortcut]: https://example.com
```

**Renders as**

[inline](https://example.com)

[full reference][label]

[collapsed][]

[shortcut]

<https://example.com>

[label]: https://example.com
[collapsed]: https://example.com
[shortcut]: https://example.com

Labels match case-insensitively after Unicode case-folding and whitespace
normalisation, so `[Foo Bar]`, `[foo bar]`, and `[FOO   BAR]` are the same label.
Links may not nest inside links. **Bare URLs are not autolinked in CommonMark** —
that is a GFM extension.

---

## Link destinations

Two forms, identical output. The `<>` form is needed for destinations with spaces.

**Source**

```text
[bare destination](/my-url)

[angle-wrapped](</my url with spaces>)

[empty]()

[empty, angle form](<>)
```

**Renders as**

[bare destination](/my-url)

[angle-wrapped](</my url with spaces>)

[empty]()

[empty, angle form](<>)

---

## Link titles

Three delimiters, identical output.

**Source**

```text
[double quotes](/url "the title")

[single quotes](/url 'the title')

[parentheses](/url (the title))
```

**Renders as**

[double quotes](/url "the title")

[single quotes](/url 'the title')

[parentheses](/url (the title))

The same three work in reference definitions, where the title may also sit on the
following line:

**Source**

```text
[multiline def]

[multiline def]:
      /url
      'title on its own line'
```

**Renders as**

[multiline def]

[multiline def]:
      /url
      'title on its own line'

---

## Images

Identical to links with a leading `!`. Autolink has no image equivalent.

**Source**

```text
![inline](https://placehold.co/100x30/png "title")

![full reference][img]

![collapsed][]

![shortcut]

![](https://placehold.co/60x30/png)

[img]: https://placehold.co/100x30/png
[collapsed]: https://placehold.co/100x30/png
[shortcut]: https://placehold.co/100x30/png
```

**Renders as**

![inline](https://placehold.co/100x30/png "title")

![full reference][img]

![collapsed][]

![shortcut]

![](https://placehold.co/60x30/png)

[img]: https://placehold.co/100x30/png
[collapsed]: https://placehold.co/100x30/png
[shortcut]: https://placehold.co/100x30/png

Alt text is the plain-text flattening of the description, so markup inside is dropped.

---

## Hard line breaks

Two forms, identical `<br />` output. One is visible in your editor, one is not.

| Form | Syntax | Visible in source? |
|---|---|:--:|
| Trailing spaces | two or more, then newline | No |
| Backslash | `\` then newline | Yes |

**Source**

```text
backslash form\
second line

two-space form··
second line
```

**Renders as**

backslash form\
second line

two-space form  
second line

Prefer the backslash — trailing whitespace is invisible, and many editors, linters,
and `git` hooks strip it silently.

---

## Soft vs hard breaks

**Source**

```text
soft break
between these lines

hard break\
between these lines
```

**Renders as**

soft break
between these lines

hard break\
between these lines

---

## Escaping a character

Three routes to a literal `*`.

| Form | Syntax |
|---|---|
| Backslash escape | `\*` |
| Named entity | `&ast;` |
| Numeric entity | `&#42;` |

**Source**

```text
backslash: \*not emphasis\*

named entity: &ast;not emphasis&ast;

numeric entity: &#42;not emphasis&#42;
```

**Renders as**

backslash: \*not emphasis\*

named entity: &ast;not emphasis&ast;

numeric entity: &#42;not emphasis&#42;

Backslash escapes work on any ASCII punctuation character. None of the three work
inside a code span or code block, where the characters are already literal.

---

## Character references

Three spellings of the same character.

**Source**

```text
named:   &copy; &nbsp; &amp; &ouml; &hellip;
decimal: &#169; &#160; &#38;  &#246; &#8230;
hex:     &#x00A9; &#xA0; &#x26; &#xF6; &#x2026;
```

**Renders as**

named:   &copy; &nbsp; &amp; &ouml; &hellip;

decimal: &#169; &#160; &#38;  &#246; &#8230;

hex:     &#x00A9; &#xA0; &#x26; &#xF6; &#x2026;

All ~2,000 HTML5 named entities are recognised. You can also just type the character
directly — © — which is usually clearer.

---

## Raw HTML

Inline HTML has one form. Block HTML has seven start conditions, each with its own
end rule.

| # | Starts with | Ends at |
|---|---|---|
| 1 | `<pre>`, `<script>`, `<style>`, `<textarea>` | matching closing tag |
| 2 | `<!--` | `-->` |
| 3 | `<?` | `?>` |
| 4 | `<!` + letter | `>` |
| 5 | `<![CDATA[` | `]]>` |
| 6 | a known block-level tag name | blank line |
| 7 | any other complete tag alone on a line | blank line |

**Source**

```text
Inline: <em>emphasis</em> and <a href="/x">a link</a>.

<div class="note">
*Markdown is not parsed inside an HTML block.*
</div>

<!-- a comment block -->
```

**Renders as**

Inline: <em>emphasis</em> and <a href="/x">a link</a>.

<div class="note">
*Markdown is not parsed inside an HTML block.*
</div>

<!-- a comment block -->

Condition 7 cannot interrupt a paragraph.

---

## Comments — the two idioms

CommonMark has no comment syntax. Two constructs are conventionally used instead.

**Source**

```text
<!-- An HTML comment. Present in the HTML output but invisible on screen. -->

[//]: # (A link reference definition nobody references. Absent from the output.)

[comment]: <> (Same trick with an empty angle destination.)
```

**Renders as**

<!-- An HTML comment. Present in the HTML output but invisible on screen. -->

[//]: # (A link reference definition nobody references. Absent from the output.)

[comment]: <> (Same trick with an empty angle destination.)

Neither appears on screen. The HTML comment survives into the output where a reader
can view-source it; the definition form disappears entirely, which is why tooling
pipelines use it to smuggle directives.

---

## Not in CommonMark at all

No tables, footnotes, definition lists, strikethrough, task lists, heading IDs,
abbreviations, or metadata. Every one of those is an extension — see the GFM, Extra,
MultiMarkdown, and Pandoc files.
