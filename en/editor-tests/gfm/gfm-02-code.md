---
guid: 3dccd9a7-41c7-4417-a642-29ec911e372a
title: GFM 02 · Code blocks and code spans
seo:
  title: GFM 02 · Code blocks and code spans
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests indented code blocks, fenced code blocks and inline code spans. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

> The last case, C-18, leaves a fence unclosed on purpose. Everything after it becomes code, so it must stay at the end of the article.

## Indented code blocks

### C-01 · Four-space indent

**Source**

````markdown
Paragraph before.

    const a = 1;
    const b = 2;
````

**Renders as**

Paragraph before.

    const a = 1;
    const b = 2;

**Expect:** a code block with two lines, and no leading spaces inside it.

<!-- end C-01 -->

### C-02 · Blank lines inside an indented block

**Source**

````markdown
    first chunk

    second chunk
````

**Renders as**

    first chunk

    second chunk

**Expect:** one code block containing both chunks and the blank line between them.

<!-- end C-02 -->

### C-03 · An indented block cannot interrupt a paragraph

**Source**

````markdown
A paragraph
    with an indented continuation line
````

**Renders as**

A paragraph
    with an indented continuation line

**Expect:** one paragraph. No code block.

<!-- end C-03 -->

## Fenced code blocks

### C-04 · Backtick fence

**Source**

````markdown
```
plain fenced code
```
````

**Renders as**

```
plain fenced code
```

**Expect:** a code block with no syntax highlighting.

<!-- end C-04 -->

### C-05 · Tilde fence

**Source**

````markdown
~~~
tilde fenced code
~~~
````

**Renders as**

~~~
tilde fenced code
~~~

**Expect:** the same result as C-04.

<!-- end C-05 -->

### C-06 · Language info string

**Source**

````markdown
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```

~~~python
def greet(name):
    return f"Hello, {name}!"
~~~
````

**Renders as**

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```

~~~python
def greet(name):
    return f"Hello, {name}!"
~~~

**Expect:** two code blocks, highlighted as JavaScript and Python if the editor supports highlighting. Indentation is kept.

<!-- end C-06 -->

### C-07 · Info string with extra words

**Source**

````markdown
```json title="config.json"
{ "enabled": true }
```
````

**Renders as**

```json title="config.json"
{ "enabled": true }
```

**Expect:** a JSON code block. Only the first word, `json`, sets the language, and the rest is not shown as code.

<!-- end C-07 -->

### C-08 · A longer fence can contain a shorter one

**Source**

`````markdown
````markdown
```
inner fence
```
````
`````

**Renders as**

````markdown
```
inner fence
```
````

**Expect:** one code block that shows the inner ```` ``` ```` lines as text.

<!-- end C-08 -->

### C-09 · A tilde fence can contain backticks

**Source**

````markdown
~~~
```
backticks inside tildes
```
~~~
````

**Renders as**

~~~
```
backticks inside tildes
```
~~~

**Expect:** one code block that shows the ```` ``` ```` lines as text.

<!-- end C-09 -->

### C-10 · The closing fence can be longer

**Source**

````markdown
```
closed by five backticks
`````
````

**Renders as**

```
closed by five backticks
`````

**Expect:** one code block. Nothing after it is swallowed.

<!-- end C-10 -->

### C-11 · Indented fence

**Source** (the fence is indented 2 spaces, and so is the first code line)

````markdown
  ```
  indented by two
    indented by four
  ```
````

**Renders as**

  ```
  indented by two
    indented by four
  ```

**Expect:** a code block where the first line has no indent and the second has two spaces.

<!-- end C-11 -->

### C-12 · Empty fenced block

**Source**

````markdown
```
```
````

**Renders as**

```
```

**Expect:** an empty code block, or nothing. No stray backticks.

<!-- end C-12 -->

### C-13 · HTML and Markdown inside code are not rendered

**Source**

````markdown
```
<b>not bold</b> and **not strong**
```
````

**Renders as**

```
<b>not bold</b> and **not strong**
```

**Expect:** the tags and asterisks show as plain text.

<!-- end C-13 -->

## Code spans

### C-14 · Single backticks

**Source**

````markdown
Run `npm install` first.
````

**Renders as**

Run `npm install` first.

**Expect:** `npm install` in a code font.

<!-- end C-14 -->

### C-15 · A backtick inside a code span

**Source**

````markdown
Use `` a`b `` or ``` two `` ticks ```.
````

**Renders as**

Use `` a`b `` or ``` two `` ticks ```.

**Expect:** two code spans that show a`b and two `` ticks.

<!-- end C-15 -->

### C-16 · Spaces around a code span

**Source**

````markdown
`` `leading and trailing backtick` ``

`  two spaces kept  `
````

**Renders as**

`` `leading and trailing backtick` ``

`  two spaces kept  `

**Expect:** the first shows the text with a backtick at each end. In the second, one space is stripped from each side, so one space remains at each end.

<!-- end C-16 -->

### C-17 · No escapes or entities inside a code span

**Source**

````markdown
`\*literal backslash\*` and `&amp;` stay as typed.
````

**Renders as**

`\*literal backslash\*` and `&amp;` stay as typed.

**Expect:** the code spans show `\*literal backslash\*` and `&amp;` exactly, including the backslashes.

<!-- end C-17 -->

## Unclosed fence (keep last)

### C-18 · An unclosed fence runs to the end of the article

**Source**

````markdown
```
this fence is never closed
````

**Renders as**

```
this fence is never closed

**Expect:** everything from here to the end of the article is code, including this line.

<!-- end C-18 -->
