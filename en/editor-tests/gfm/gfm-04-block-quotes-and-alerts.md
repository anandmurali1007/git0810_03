---
guid: e0ae636d-6cbe-479a-8f29-8850aca6af0d
title: GFM 04 · Block quotes and alerts
seo:
  title: GFM 04 · Block quotes and alerts
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests block quotes and GitHub alerts. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

Alerts (Q-10 to Q-13) are a GitHub.com feature, not part of the GFM specification. Where alerts are not supported, they render as ordinary block quotes that show the `[!NOTE]` text.

## Block quotes

### Q-01 · Basic quote

**Source**

````markdown
> A quoted paragraph.
````

**Renders as**

> A quoted paragraph.

**Expect:** a block quote with one paragraph.

<!-- end Q-01 -->

### Q-02 · Space after the marker is optional

**Source**

````markdown
>No space after the marker.
````

**Renders as**

>No space after the marker.

**Expect:** the same appearance as Q-01.

<!-- end Q-02 -->

### Q-03 · Several paragraphs

**Source**

````markdown
> First paragraph.
>
> Second paragraph.
````

**Renders as**

> First paragraph.
>
> Second paragraph.

**Expect:** one block quote containing two paragraphs.

<!-- end Q-03 -->

### Q-04 · A blank line splits the quote

**Source**

````markdown
> First quote.

> Second quote.
````

**Renders as**

> First quote.

> Second quote.

**Expect:** two separate block quotes.

<!-- end Q-04 -->

### Q-05 · Lazy continuation

**Source**

````markdown
> This line is quoted
and so is this one, with no marker.
````

**Renders as**

> This line is quoted
and so is this one, with no marker.

**Expect:** one quoted paragraph containing both lines.

<!-- end Q-05 -->

### Q-06 · Nested quotes

**Source**

````markdown
> Level 1
>> Level 2
>>> Level 3
````

**Renders as**

> Level 1
>> Level 2
>>> Level 3

**Expect:** three nested quotes.

<!-- end Q-06 -->

### Q-07 · Headings, lists and code inside a quote

**Source**

````markdown
> ### Quoted heading
>
> - item one
> - item two
>
> ```
> quoted code
> ```
````

**Renders as**

> ### Quoted heading
>
> - item one
> - item two
>
> ```
> quoted code
> ```

**Expect:** a heading, a list and a code block, all inside one quote.

<!-- end Q-07 -->

### Q-08 · Inline formatting inside a quote

**Source**

````markdown
> **Strong**, *emphasis*, ~~strikethrough~~, `code` and a [link](https://example.com).
````

**Renders as**

> **Strong**, *emphasis*, ~~strikethrough~~, `code` and a [link](https://example.com).

**Expect:** all five styles inside the quote.

<!-- end Q-08 -->

### Q-09 · Empty quote

**Source**

````markdown
>
````

**Renders as**

>

**Expect:** an empty block quote, or nothing. No `>` shown.

<!-- end Q-09 -->

## Alerts

### Q-10 · Note and tip

**Source**

````markdown
> [!NOTE]
> Useful information that users should know.

> [!TIP]
> Helpful advice for doing things better.
````

**Renders as**

> [!NOTE]
> Useful information that users should know.

> [!TIP]
> Helpful advice for doing things better.

**Expect:** a styled *Note* callout and a styled *Tip* callout. The `[!NOTE]` and `[!TIP]` text is not shown.

<!-- end Q-10 -->

### Q-11 · Important, warning and caution

**Source**

````markdown
> [!IMPORTANT]
> Key information users need to know.

> [!WARNING]
> Urgent information that needs attention.

> [!CAUTION]
> Advice about risks or negative outcomes.
````

**Renders as**

> [!IMPORTANT]
> Key information users need to know.

> [!WARNING]
> Urgent information that needs attention.

> [!CAUTION]
> Advice about risks or negative outcomes.

**Expect:** three styled callouts, each with a different colour and icon.

<!-- end Q-11 -->

### Q-12 · Alert with several paragraphs and a list

**Source**

````markdown
> [!NOTE]
> First paragraph of the note.
>
> - a list item
> - another item
````

**Renders as**

> [!NOTE]
> First paragraph of the note.
>
> - a list item
> - another item

**Expect:** one *Note* callout containing a paragraph and a list.

<!-- end Q-12 -->

### Q-13 · Not alerts

**Source**

````markdown
> [!note]
> Lowercase type.

> [!UNKNOWN]
> Unknown type.

> Text before [!NOTE] the marker.
````

**Renders as**

> [!note]
> Lowercase type.

> [!UNKNOWN]
> Unknown type.

> Text before [!NOTE] the marker.

**Expect:** on GitHub, `[!note]` in lowercase is still a *Note* callout. `[!UNKNOWN]` and the marker in the middle of text render as ordinary quotes that show the text.

<!-- end Q-13 -->
