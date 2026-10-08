---
guid: 76e2ac25-1ff5-41a9-8bce-299862d8f5f9
title: "GFM 08 · Raw HTML and the tag filter"
seo:
  title: "GFM 08 · Raw HTML and the tag filter"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests HTML written directly in Markdown and the GFM tag filter. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

GitHub also removes many tags and attributes for safety, such as `style` attributes. Where GitHub and this editor differ on an allowed tag, record the difference rather than a failure.

> The filtered-tag cases contain harmless content only: a `console.log` call, a style rule for a class nothing uses, and an empty frame. The last case, R-18, uses `<plaintext>`. An editor without the tag filter shows the rest of the page as text, so it must stay at the end.

## HTML blocks

### R-01 · A div with and without blank lines

**Source**

````markdown
<div>
*Not emphasis: Markdown is not processed right after the tag.*
</div>

<div>

*Emphasis: a blank line after the tag switches Markdown back on.*

</div>
````

**Renders as**

<div>
*Not emphasis: Markdown is not processed right after the tag.*
</div>

<div>

*Emphasis: a blank line after the tag switches Markdown back on.*

</div>

**Expect:** the first sentence shows the asterisks. The second is in italics.

<!-- end R-01 -->

### R-02 · HTML table

**Source**

````markdown
<table>
  <tr><th>Header</th><th>Cell</th></tr>
  <tr><td>row</td><td><b>bold</b></td></tr>
</table>
````

**Renders as**

<table>
  <tr><th>Header</th><th>Cell</th></tr>
  <tr><td>row</td><td><b>bold</b></td></tr>
</table>

**Expect:** a two-row table with a bold cell.

<!-- end R-02 -->

### R-03 · Preformatted block

**Source**

````markdown
<pre>
Keeps    spacing
and **ignores** Markdown
</pre>
````

**Renders as**

<pre>
Keeps    spacing
and **ignores** Markdown
</pre>

**Expect:** monospaced text with the four spaces and the asterisks kept.

<!-- end R-03 -->

### R-04 · Collapsible section

**Source**

````markdown
<details>
<summary>Click to expand</summary>

Hidden content with **Markdown** and a list:

- one
- two

</details>
````

**Renders as**

<details>
<summary>Click to expand</summary>

Hidden content with **Markdown** and a list:

- one
- two

</details>

**Expect:** a collapsed section titled *Click to expand*. When opened, it shows the paragraph and the list.

<!-- end R-04 -->

### R-05 · Open by default

**Source**

````markdown
<details open>
<summary>Already open</summary>

Visible without clicking.

</details>
````

**Renders as**

<details open>
<summary>Already open</summary>

Visible without clicking.

</details>

**Expect:** the section starts open.

<!-- end R-05 -->

### R-06 · Comments

**Source**

````markdown
<!-- A block comment that must not show -->

Visible text <!-- with a hidden inline comment --> continues.

<!--
A multi-line comment
that must not show.
-->
````

**Renders as**

<!-- A block comment that must not show -->

Visible text <!-- with a hidden inline comment --> continues.

<!--
A multi-line comment
that must not show.
-->

**Expect:** only "Visible text continues." is shown.

<!-- end R-06 -->

### R-07 · Attributes

**Source**

````markdown
<p align="center">Centred paragraph</p>

<span style="color: red">Red text</span> and <a id="r07-anchor"></a>an anchor. [Jump to it](#r07-anchor)
````

**Renders as**

<p align="center">Centred paragraph</p>

<span style="color: red">Red text</span> and <a id="r07-anchor"></a>an anchor. [Jump to it](#r07-anchor)

**Expect:** a centred paragraph. GitHub removes the `style` attribute, so "Red text" is black there. Note what this editor does.

<!-- end R-07 -->

## Inline HTML

### R-08 · Formatting tags

**Source**

````markdown
Press <kbd>Ctrl</kbd> + <kbd>C</kbd> · H<sub>2</sub>O · x<sup>2</sup> · <ins>inserted</ins> · <del>deleted</del> · <mark>highlighted</mark> · <abbr title="GitHub Flavored Markdown">GFM</abbr> · <b>b</b> <i>i</i> <u>u</u> <s>s</s>
````

**Renders as**

Press <kbd>Ctrl</kbd> + <kbd>C</kbd> · H<sub>2</sub>O · x<sup>2</sup> · <ins>inserted</ins> · <del>deleted</del> · <mark>highlighted</mark> · <abbr title="GitHub Flavored Markdown">GFM</abbr> · <b>b</b> <i>i</i> <u>u</u> <s>s</s>

**Expect:** keyboard keys, subscript, superscript, underline, strikethrough, a highlight, an abbreviation with a hover title, and bold, italic, underline and struck letters.

<!-- end R-08 -->

### R-09 · Line break tag

**Source**

````markdown
First line<br>second line<br/>third line
````

**Renders as**

First line<br>second line<br/>third line

**Expect:** three lines in one paragraph.

<!-- end R-09 -->

### R-10 · Link and image tags

**Source**

````markdown
<a href="https://example.com" title="HTML link">HTML link</a> · <img src="https://placehold.co/80x30/png" alt="HTML image" width="80" height="30">
````

**Renders as**

<a href="https://example.com" title="HTML link">HTML link</a> · <img src="https://placehold.co/80x30/png" alt="HTML image" width="80" height="30">

**Expect:** a link and an 80 × 30 image.

<!-- end R-10 -->

### R-11 · Markdown inside inline HTML

**Source**

````markdown
<span>**strong** inside a span</span>
````

**Renders as**

<span>**strong** inside a span</span>

**Expect:** the word "strong" is bold, because Markdown still works inside inline tags.

<!-- end R-11 -->

### R-12 · Text that looks like HTML but is not

**Source**

````markdown
a < b > c · 5 <= 6 · <not a tag> · <3 · x <y
````

**Renders as**

a < b > c · 5 <= 6 · <not a tag> · <3 · x <y

**Expect:** all the text shows, including every `<` and `>`. `<not a tag>` may be treated as an unknown tag and hidden. Match GitHub.

<!-- end R-12 -->

## Tag filter (GFM)

GFM replaces the `<` of nine tags with `&lt;`, so the tag shows as text and does nothing.

### R-13 · Script

**Source**

````markdown
<script>console.log("GFM test R-13: this script ran")</script>
````

**Renders as**

<script>console.log("GFM test R-13: this script ran")</script>

**Expect:** the tag shows as text or is removed. Nothing is logged in the browser console.

<!-- end R-13 -->

### R-14 · Style

**Source**

````markdown
<style>.gfm-r14-unused { color: red; }</style>
````

**Renders as**

<style>.gfm-r14-unused { color: red; }</style>

**Expect:** the tag shows as text or is removed. No styles change.

<!-- end R-14 -->

### R-15 · Iframe

**Source**

````markdown
<iframe src="about:blank" width="200" height="40"></iframe>
````

**Renders as**

<iframe src="about:blank" width="200" height="40"></iframe>

**Expect:** no frame. The tag shows as text or is removed.

<!-- end R-15 -->

### R-16 · Title, textarea and xmp

**Source**

````markdown
<title>GFM test R-16 title</title>

<textarea>GFM test R-16 textarea</textarea>

<xmp>GFM test R-16 xmp</xmp>
````

**Renders as**

<title>GFM test R-16 title</title>

<textarea>GFM test R-16 textarea</textarea>

<xmp>GFM test R-16 xmp</xmp>

**Expect:** no page title change, no text box and no special block. The tags show as text or are removed.

<!-- end R-16 -->

### R-17 · Noembed and noframes

**Source**

````markdown
<noembed>GFM test R-17 noembed</noembed>

<noframes>GFM test R-17 noframes</noframes>
````

**Renders as**

<noembed>GFM test R-17 noembed</noembed>

<noframes>GFM test R-17 noframes</noframes>

**Expect:** the tags show as text or are removed.

<!-- end R-17 -->

### R-18 · Plaintext (keep last)

**Source**

````markdown
<plaintext>GFM test R-18
````

**Renders as**

<plaintext>GFM test R-18

**Expect:** the tag shows as text or is removed, and the line below renders normally. If everything below shows as raw text, the editor has no tag filter.

The end of the article.

<!-- end R-18 -->
