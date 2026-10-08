---
guid: fe941b0c-17e1-462f-bb45-b9375d1d209b
title: GFM 01 · Headings, paragraphs and breaks
seo:
  title: GFM 01 · Headings, paragraphs and breaks
display:
  toc: true
  outline: true
feedback:
  comments: true
---

This article tests headings, horizontal rules, paragraphs and line breaks. Each case shows the **Source**, how it **Renders as** in this editor, and what to **Expect**. Compare the result with GitHub's view of this file, then record it in the *GFM editor tests* checklist.

## Headings

### H-01 · ATX headings, levels 1 to 6

**Source**

````markdown
# Level 1
## Level 2
### Level 3
#### Level 4
##### Level 5
###### Level 6
````

**Renders as**

# Level 1
## Level 2
### Level 3
#### Level 4
##### Level 5
###### Level 6

**Expect:** six headings, each smaller than the one before.

<!-- end H-01 -->

### H-02 · Seven hashes is not a heading

**Source**

````markdown
####### Seven hashes
````

**Renders as**

####### Seven hashes

**Expect:** a plain paragraph that shows the seven `#` characters.

<!-- end H-02 -->

### H-03 · A space is required after the hashes

**Source**

````markdown
#5 bolt

#hashtag
````

**Renders as**

#5 bolt

#hashtag

**Expect:** two plain paragraphs, not headings.

<!-- end H-03 -->

### H-04 · Closing hashes

**Source**

````markdown
## Closed heading ##

### Closed with a different count #########

#### Hashes in the text # stay #
````

**Renders as**

## Closed heading ##

### Closed with a different count #########

#### Hashes in the text # stay #

**Expect:** the closing hashes are hidden. In the third heading only the last `#` is removed, so it reads "Hashes in the text # stay".

<!-- end H-04 -->

### H-05 · Escaped hash and leading spaces

**Source**

````markdown
\## Not a heading

   ### Up to three leading spaces is still a heading
````

**Renders as**

\## Not a heading

   ### Up to three leading spaces is still a heading

**Expect:** the first line is a paragraph that starts with `##`. The second is a level-3 heading.

<!-- end H-05 -->

### H-06 · Empty headings

**Source**

````markdown
##

#
````

**Renders as**

##

#

**Expect:** two empty headings, or nothing visible. No `#` characters shown.

<!-- end H-06 -->

### H-07 · Setext headings

**Source**

````markdown
Level 1 with equals signs
=========================

Level 2 with hyphens
---
````

**Renders as**

Level 1 with equals signs
=========================

Level 2 with hyphens
---

**Expect:** a level-1 heading, then a level-2 heading. The `===` and `---` lines are not shown.

<!-- end H-07 -->

### H-08 · Multi-line Setext heading

**Source**

````markdown
A heading that
spans two lines
===
````

**Renders as**

A heading that
spans two lines
===

**Expect:** one level-1 heading containing both lines.

<!-- end H-08 -->

### H-09 · Inline formatting in headings

**Source**

````markdown
### Heading with *emphasis*, **strong**, `code` and a [link](https://example.com)
````

**Renders as**

### Heading with *emphasis*, **strong**, `code` and a [link](https://example.com)

**Expect:** a level-3 heading with all four inline styles.

<!-- end H-09 -->

## Horizontal rules

### H-10 · Three characters

**Source**

````markdown
***

---

___
````

**Renders as**

***

---

___

**Expect:** three horizontal rules.

<!-- end H-10 -->

### H-11 · Spaced and long rules

**Source**

````markdown
- - -

 **  * ** * ** * **

_____________________
````

**Renders as**

- - -

 **  * ** * ** * **

_____________________

**Expect:** three horizontal rules. The first must not become a list.

<!-- end H-11 -->

### H-12 · Not a rule

**Source**

````markdown
--

**

+++

===
````

**Renders as**

--

**

+++

===

**Expect:** plain text: `--`, `**`, `+++` and `===`. No rules.

<!-- end H-12 -->

### H-13 · Hyphens under a paragraph make a heading, not a rule

**Source**

````markdown
Foo
---
bar
````

**Renders as**

Foo
---
bar

**Expect:** a level-2 heading "Foo", then a paragraph "bar". No rule.

<!-- end H-13 -->

## Paragraphs and line breaks

### H-14 · Paragraphs are separated by blank lines

**Source**

````markdown
First paragraph.

Second paragraph.



Third paragraph after three blank lines.
````

**Renders as**

First paragraph.

Second paragraph.



Third paragraph after three blank lines.

**Expect:** three paragraphs with the same spacing. Extra blank lines add no extra space.

<!-- end H-14 -->

### H-15 · Soft line break

**Source**

````markdown
This line and
this line join into one paragraph.
````

**Renders as**

This line and
this line join into one paragraph.

**Expect:** one line of text, joined with a space.

<!-- end H-15 -->

### H-16 · Hard line break with two trailing spaces

**Source** (the first line ends with two spaces)

````markdown
Line one  
Line two
````

**Renders as**

Line one  
Line two

**Expect:** two lines in one paragraph. In the round-trip diff, check that the two trailing spaces survived.

<!-- end H-16 -->

### H-17 · Hard line break with a backslash

**Source**

````markdown
Line one\
Line two
````

**Renders as**

Line one\
Line two

**Expect:** two lines in one paragraph. No backslash shown.

<!-- end H-17 -->

### H-18 · No hard break at the end of a paragraph

**Source** (the line ends with a backslash, then two spaces)

````markdown
Ends with a backslash\

Ends with two spaces  
````

**Renders as**

Ends with a backslash\

Ends with two spaces  

**Expect:** the first paragraph shows a literal `\`. The second shows no break and no extra space.

<!-- end H-18 -->

### H-19 · Leading spaces in a paragraph

**Source**

````markdown
  Two leading spaces
   and three on the next line
````

**Renders as**

  Two leading spaces
   and three on the next line

**Expect:** one normal paragraph. The leading spaces are removed, and it is not a code block.

<!-- end H-19 -->
