---
guid: 41d925fb-d02e-4fa8-9d6f-e4e1a644d588
title: "GFM 05 · Inline formatting and escapes"
seo:
  title: "GFM 05 · Inline formatting and escapes"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests emphasis, strong text, strikethrough, backslash escapes and HTML entities. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

## Emphasis and strong

### I-01 · Emphasis with asterisks and underscores

**Source**

````markdown
*asterisk emphasis* and _underscore emphasis_
````

**Renders as**

*asterisk emphasis* and _underscore emphasis_

**Expect:** both phrases in italics.

<!-- end I-01 -->

### I-02 · Strong with asterisks and underscores

**Source**

````markdown
**asterisk strong** and __underscore strong__
````

**Renders as**

**asterisk strong** and __underscore strong__

**Expect:** both phrases in bold.

<!-- end I-02 -->

### I-03 · Strong and emphasis together

**Source**

````markdown
***three asterisks*** · ___three underscores___ · **_strong outside_** · *__emphasis outside__*
````

**Renders as**

***three asterisks*** · ___three underscores___ · **_strong outside_** · *__emphasis outside__*

**Expect:** all four phrases in bold italics.

<!-- end I-03 -->

### I-04 · Nested emphasis inside strong

**Source**

````markdown
**bold with *italic* inside** and *italic with **bold** inside*
````

**Renders as**

**bold with *italic* inside** and *italic with **bold** inside*

**Expect:** only the inner word changes style in each phrase.

<!-- end I-04 -->

### I-05 · Inside a word

**Source**

````markdown
un*frigging*believable · un**frigging**believable · snake_case_name · __init__ · foo__bar__baz
````

**Renders as**

un*frigging*believable · un**frigging**believable · snake_case_name · __init__ · foo__bar__baz

**Expect:** asterisks work inside a word, so "frigging" is italic, then bold. Underscores do not, so `snake_case_name` and `foo__bar__baz` are plain. `__init__` is a whole word, so "init" is bold.

<!-- end I-05 -->

### I-06 · Spaces stop emphasis

**Source**

````markdown
a * b * c

** not strong **
````

**Renders as**

a * b * c

** not strong **

**Expect:** plain text with the asterisks showing.

<!-- end I-06 -->

### I-07 · Unmatched markers

**Source**

````markdown
**unclosed strong

*unclosed emphasis

__mixed markers**
````

**Renders as**

**unclosed strong

*unclosed emphasis

__mixed markers**

**Expect:** plain text with the markers showing. No bold or italics.

<!-- end I-07 -->

## Strikethrough

### I-08 · One and two tildes

**Source**

````markdown
~one tilde~ and ~~two tildes~~
````

**Renders as**

~one tilde~ and ~~two tildes~~

**Expect:** both phrases struck through.

<!-- end I-08 -->

### I-09 · Three tildes is not strikethrough

**Source**

````markdown
This will ~~~not~~~ strike.
````

**Renders as**

This will ~~~not~~~ strike.

**Expect:** plain text with the tildes showing.

<!-- end I-09 -->

### I-10 · Strikethrough with other styles

**Source**

````markdown
~~struck **bold** and *italic* and `code`~~ · **~~bold struck~~**
````

**Renders as**

~~struck **bold** and *italic* and `code`~~ · **~~bold struck~~**

**Expect:** the first phrase is struck through with bold, italic and code inside it. The second is bold and struck through.

<!-- end I-10 -->

### I-11 · Strikethrough across a line break

**Source**

````markdown
~~struck text
over two lines~~
````

**Renders as**

~~struck text
over two lines~~

**Expect:** both lines struck through.

<!-- end I-11 -->

## Backslash escapes

### I-12 · Every escapable punctuation character

**Source**

````markdown
\! \" \# \$ \% \& \' \( \) \* \+ \, \- \. \/ \: \; \< \= \> \? \@ \[ \\ \] \^ \_ \` \{ \| \} \~
````

**Renders as**

\! \" \# \$ \% \& \' \( \) \* \+ \, \- \. \/ \: \; \< \= \> \? \@ \[ \\ \] \^ \_ \` \{ \| \} \~

**Expect:** each character once, with no backslashes except one `\` in the middle for `\\`.

<!-- end I-12 -->

### I-13 · Escaping Markdown syntax

**Source**

````markdown
\*not emphasis\* · \**not strong\** · \~~not struck\~~ · \[not a link\](https://example.com) · \`not code\`
````

**Renders as**

\*not emphasis\* · \**not strong\** · \~~not struck\~~ · \[not a link\](https://example.com) · \`not code\`

**Expect:** plain text showing the syntax characters. No formatting and no link.

<!-- end I-13 -->

### I-14 · Escaping at the start of a line

**Source**

````markdown
\- not a list item

\+ not a list item

1\. not a numbered item

\> not a quote

\# not a heading
````

**Renders as**

\- not a list item

\+ not a list item

1\. not a numbered item

\> not a quote

\# not a heading

**Expect:** five plain paragraphs.

<!-- end I-14 -->

### I-15 · A backslash before other characters stays

**Source**

````markdown
\a \B \3 \→ C:\Users\docs
````

**Renders as**

\a \B \3 \→ C:\Users\docs

**Expect:** every backslash shows, because none of these characters can be escaped.

<!-- end I-15 -->

## HTML entities

### I-16 · Named entities

**Source**

````markdown
&copy; &reg; &trade; &amp; &lt; &gt; &quot; &nbsp;| &ndash; &mdash; &hellip; &frac34; &AElig; &Dcaron;
````

**Renders as**

&copy; &reg; &trade; &amp; &lt; &gt; &quot; &nbsp;| &ndash; &mdash; &hellip; &frac34; &AElig; &Dcaron;

**Expect:** © ® ™ & < > " (a non-breaking space before the bar) – — … ¾ Æ Ď

<!-- end I-16 -->

### I-17 · Numeric entities

**Source**

````markdown
&#35; &#1234; &#992; &#X22; &#XD06; &#xcab; &#0;
````

**Renders as**

&#35; &#1234; &#992; &#X22; &#XD06; &#xcab; &#0;

**Expect:** # Ӓ Ϡ " ആ ಫ, then the replacement character � for `&#0;`.

<!-- end I-17 -->

### I-18 · Not entities

**Source**

````markdown
&nbsp &x; &#; &#x; &ThisIsNotDefined; &hi?;
````

**Renders as**

&nbsp &x; &#; &#x; &ThisIsNotDefined; &hi?;

**Expect:** all six show exactly as typed.

<!-- end I-18 -->

### I-19 · Escaping an entity

**Source**

````markdown
\&copy; shows the entity name.
````

**Renders as**

\&copy; shows the entity name.

**Expect:** the text `&copy;`, not ©.

<!-- end I-19 -->
