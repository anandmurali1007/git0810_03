---
guid: 814a279b-f6b5-4af1-8a97-d0752e5f94d1
title: "GFM 03 · Lists and task lists"
seo:
  title: "GFM 03 · Lists and task lists"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests bullet lists, numbered lists and GFM task lists. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**.

## Bullet lists

### L-01 · The three bullet markers

**Source**

````markdown
- hyphen

+ plus

* asterisk
````

**Renders as**

- hyphen

+ plus

* asterisk

**Expect:** three separate one-item lists. Changing the marker starts a new list.

<!-- end L-01 -->

### L-02 · Changing the marker without a blank line

**Source**

````markdown
- one
- two
+ three
````

**Renders as**

- one
- two
+ three

**Expect:** two lists: the first has "one" and "two", the second has "three".

<!-- end L-02 -->

### L-03 · Nested bullets, three levels

**Source**

````markdown
- Level 1
  - Level 2
    - Level 3
  - Back to level 2
- Back to level 1
````

**Renders as**

- Level 1
  - Level 2
    - Level 3
  - Back to level 2
- Back to level 1

**Expect:** three levels of nesting, with each level indented further.

<!-- end L-03 -->

## Numbered lists

### L-04 · The two number delimiters

**Source**

````markdown
1. dot one
2. dot two

1) parenthesis one
2) parenthesis two
````

**Renders as**

1. dot one
2. dot two

1) parenthesis one
2) parenthesis two

**Expect:** two numbered lists, each numbered 1 and 2.

<!-- end L-04 -->

### L-05 · The start number is kept

**Source**

````markdown
7. seven
8. eight
````

**Renders as**

7. seven
8. eight

**Expect:** a list numbered 7 and 8, not 1 and 2.

<!-- end L-05 -->

### L-06 · Only the first number matters

**Source**

````markdown
1. one
1. two
1. three

3. three
1. four
5. five
````

**Renders as**

1. one
1. two
1. three

3. three
1. four
5. five

**Expect:** the first list is numbered 1, 2, 3. The second is numbered 3, 4, 5.

<!-- end L-06 -->

### L-07 · Only a list starting at 1 can interrupt a paragraph

**Source**

````markdown
The year was
1986. What a great season.

Steps:
1. first
2. second
````

**Renders as**

The year was
1986. What a great season.

Steps:
1. first
2. second

**Expect:** "1986." stays in the first paragraph. After "Steps:", a numbered list starts.

<!-- end L-07 -->

### L-08 · Nested numbered and bullet lists

**Source**

````markdown
1. Prepare
   - Gather the files
   - Check the names
2. Upload
   1. Open the portal
   2. Drop the files
````

**Renders as**

1. Prepare
   - Gather the files
   - Check the names
2. Upload
   1. Open the portal
   2. Drop the files

**Expect:** a numbered list with a bullet list under item 1 and a numbered list under item 2.

<!-- end L-08 -->

## List content and spacing

### L-09 · Tight and loose lists

**Source**

````markdown
- tight one
- tight two

- loose one

- loose two
````

**Renders as**

- tight one
- tight two

- loose one

- loose two

**Expect:** one list of four items. Because there is a blank line between items, it is a loose list: every item is a paragraph with extra spacing.

<!-- end L-09 -->

### L-10 · Several paragraphs in one item

**Source**

````markdown
1. First paragraph of the item.

   Second paragraph of the same item.
2. Next item.
````

**Renders as**

1. First paragraph of the item.

   Second paragraph of the same item.
2. Next item.

**Expect:** item 1 contains two paragraphs, and numbering continues with item 2.

<!-- end L-10 -->

### L-11 · Lazy continuation line

**Source**

````markdown
- This item continues
on a line with no indent.
````

**Renders as**

- This item continues
on a line with no indent.

**Expect:** one item containing both lines.

<!-- end L-11 -->

### L-12 · Code, quote and heading inside an item

**Source**

````markdown
- Item with code:

  ```bash
  echo "inside a list"
  ```

- Item with a quote:

  > Quoted inside the list.

- ### Heading inside an item
````

**Renders as**

- Item with code:

  ```bash
  echo "inside a list"
  ```

- Item with a quote:

  > Quoted inside the list.

- ### Heading inside an item

**Expect:** a code block, a block quote and a heading, each inside its own list item.

<!-- end L-12 -->

### L-13 · Empty list item

**Source**

````markdown
- one
-
- three
````

**Renders as**

- one
-
- three

**Expect:** a three-item list whose middle item is empty.

<!-- end L-13 -->

### L-14 · Ending a list before a code block

**Source**

````markdown
- first
- second

<!-- -->

    code, not part of the list
````

**Renders as**

- first
- second

<!-- -->

    code, not part of the list

**Expect:** a two-item list, then a separate code block. The empty comment stops the list.

<!-- end L-14 -->

## Task lists

### L-15 · Unchecked and checked

**Source**

````markdown
- [ ] to do
- [x] done
- [X] done with a capital X
````

**Renders as**

- [ ] to do
- [x] done
- [X] done with a capital X

**Expect:** three checkboxes: one empty and two ticked. No `[ ]` or `[x]` text shown.

<!-- end L-15 -->

### L-16 · Nested task list

**Source**

````markdown
- [x] Release
  - [x] Build
  - [ ] Publish notes
    - [ ] Draft
- [ ] Announce
````

**Renders as**

- [x] Release
  - [x] Build
  - [ ] Publish notes
    - [ ] Draft
- [ ] Announce

**Expect:** checkboxes at three levels, with the ticks exactly as in the source.

<!-- end L-16 -->

### L-17 · Tasks in a numbered list and mixed with plain items

**Source**

````markdown
1. [ ] numbered task
2. [x] numbered task, done
3. plain numbered item
````

**Renders as**

1. [ ] numbered task
2. [x] numbered task, done
3. plain numbered item

**Expect:** a numbered list where the first two items have checkboxes and the third does not.

<!-- end L-17 -->

### L-18 · Not task lists

**Source**

````markdown
- [] no space inside the brackets
- [ ]no space after the brackets
- text before [ ] the brackets

[ ] not in a list
````

**Renders as**

- [] no space inside the brackets
- [ ]no space after the brackets
- text before [ ] the brackets

[ ] not in a list

**Expect:** no checkboxes. All the brackets show as text.

<!-- end L-18 -->

### L-19 · Formatting after a checkbox

**Source**

````markdown
- [ ] **Bold**, *italic*, `code` and a [link](https://example.com)
````

**Renders as**

- [ ] **Bold**, *italic*, `code` and a [link](https://example.com)

**Expect:** a checkbox followed by all four styles.

<!-- end L-19 -->
