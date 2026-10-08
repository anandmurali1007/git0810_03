---
guid: aee4919f-375b-4f6d-851c-ef342ff6eb34
title: "GFM 07 · Tables"
seo:
  title: "GFM 07 · Tables"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests GFM tables. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

## Structure

### T-01 · Basic table

**Source**

````markdown
| Name | Role |
| --- | --- |
| Asha | Writer |
| Ben | Reviewer |
````

**Renders as**

| Name | Role |
| --- | --- |
| Asha | Writer |
| Ben | Reviewer |

**Expect:** a table with a header row and two body rows.

<!-- end T-01 -->

### T-02 · Without outer pipes

**Source**

````markdown
Name | Role
--- | ---
Asha | Writer
````

**Renders as**

Name | Role
--- | ---
Asha | Writer

**Expect:** the same kind of table as T-01, with one body row.

<!-- end T-02 -->

### T-03 · Uneven spacing and a one-hyphen delimiter

**Source**

````markdown
|Name|Role|
|-|-|
|   Asha   |Writer|
````

**Renders as**

|Name|Role|
|-|-|
|   Asha   |Writer|

**Expect:** a normal table. Spaces around cell text are trimmed.

<!-- end T-03 -->

### T-04 · Header row only

**Source**

````markdown
| Only | A | Header |
| --- | --- | --- |
````

**Renders as**

| Only | A | Header |
| --- | --- | --- |

**Expect:** a table with a header row and no body rows.

<!-- end T-04 -->

### T-05 · One column

**Source**

````markdown
| Single |
| --- |
| one |
| two |
````

**Renders as**

| Single |
| --- |
| one |
| two |

**Expect:** a one-column table with two body rows.

<!-- end T-05 -->

## Alignment

### T-06 · Left, centre, right and default

**Source**

````markdown
| Left | Centre | Right | Default |
| :--- | :---: | ---: | --- |
| a | b | c | d |
| longer text | longer text | longer text | longer text |
````

**Renders as**

| Left | Centre | Right | Default |
| :--- | :---: | ---: | --- |
| a | b | c | d |
| longer text | longer text | longer text | longer text |

**Expect:** the single letters are aligned left, centre, right and left (default) in each column.

<!-- end T-06 -->

## Cell content

### T-07 · Inline formatting in cells

**Source**

````markdown
| Style | Example |
| --- | --- |
| Strong | **bold** |
| Emphasis | *italic* |
| Strikethrough | ~~struck~~ |
| Code | `npm test` |
| Link | [example](https://example.com) |
| Autolink | www.example.com |
| Image | ![tiny](https://placehold.co/40x20/png) |
| Line break | first<br>second |
````

**Renders as**

| Style | Example |
| --- | --- |
| Strong | **bold** |
| Emphasis | *italic* |
| Strikethrough | ~~struck~~ |
| Code | `npm test` |
| Link | [example](https://example.com) |
| Autolink | www.example.com |
| Image | ![tiny](https://placehold.co/40x20/png) |
| Line break | first<br>second |

**Expect:** every row shows its style. The last cell shows two lines.

<!-- end T-07 -->

### T-08 · Escaped pipes

**Source**

````markdown
| Expression | Meaning |
| --- | --- |
| `a \| b` | a or b, in code |
| x \| y | a pipe in plain text |
````

**Renders as**

| Expression | Meaning |
| --- | --- |
| `a \| b` | a or b, in code |
| x \| y | a pipe in plain text |

**Expect:** two columns. The first column shows `a | b` in code and x | y as text, with no backslashes.

<!-- end T-08 -->

### T-09 · Empty cells

**Source**

````markdown
| A | B | C |
| --- | --- | --- |
| 1 |  | 3 |
|  | 2 |  |
````

**Renders as**

| A | B | C |
| --- | --- | --- |
| 1 |  | 3 |
|  | 2 |  |

**Expect:** a three-column table with the empty cells kept in place.

<!-- end T-09 -->

## Irregular rows

### T-10 · Missing and extra cells

**Source**

````markdown
| A | B | C |
| --- | --- | --- |
| only one |
| one | two | three | four |
````

**Renders as**

| A | B | C |
| --- | --- | --- |
| only one |
| one | two | three | four |

**Expect:** three columns throughout. The first body row gets two empty cells. In the second, "four" is dropped.

<!-- end T-10 -->

### T-11 · Mismatched delimiter row is not a table

**Source**

````markdown
| A | B |
| --- |
| 1 | 2 |
````

**Renders as**

| A | B |
| --- |
| 1 | 2 |

**Expect:** plain text, not a table, because the delimiter row has fewer columns than the header.

<!-- end T-11 -->

### T-12 · Where a table ends

**Source**

````markdown
| A | B |
| --- | --- |
| in the table | yes |
Also in the table
> A quote ends the table
````

**Renders as**

| A | B |
| --- | --- |
| in the table | yes |
Also in the table
> A quote ends the table

**Expect:** "Also in the table" becomes a row with one filled cell. The quote is outside the table.

<!-- end T-12 -->

### T-13 · A table right after a paragraph

**Source**

````markdown
Paragraph text directly above the table.
| A | B |
| --- | --- |
| 1 | 2 |
````

**Renders as**

Paragraph text directly above the table.
| A | B |
| --- | --- |
| 1 | 2 |

**Expect:** GitHub shows a paragraph followed by a table. Some editors show all four lines as one paragraph instead, so match GitHub.

<!-- end T-13 -->

## Size

### T-14 · Wide table

**Source**

````markdown
| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 | Column 6 | Column 7 | Column 8 | Column 9 | Column 10 | Column 11 | Column 12 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text |
````

**Renders as**

| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 | Column 6 | Column 7 | Column 8 | Column 9 | Column 10 | Column 11 | Column 12 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text | A fairly long piece of text |

**Expect:** a 12-column table that scrolls sideways or wraps, without breaking the page layout.

<!-- end T-14 -->
