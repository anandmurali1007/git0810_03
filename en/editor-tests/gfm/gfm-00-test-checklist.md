---
guid: b05535f4-fa5b-49dc-8e3b-e0f8eadfd001
title: "GFM test checklist"
seo:
  title: "GFM test checklist"
display:
  toc: true
  outline: true
feedback:
  comments: true
---

These articles test every GitHub Flavored Markdown (GFM) construct in the editor, grouped so each article can be checked in a few minutes.

## How to check an article

1. **Render:** open the article in Document360 and the same file on GitHub, and compare each case. GitHub's rendering is the reference.
2. **Round-trip:** open the article in the Document360 editor and publish it without changing anything. Then check the commit Document360 pushes to Git. Any change to the case sources means the editor rewrote the syntax.
3. **Record:** tick the case below when both checks pass. For a failure, add a short note after the case.

Cases whose *Expect* line says "match GitHub" depend on GitHub's behaviour rather than a fixed rule.

## Results

### [GFM 01 · Headings, paragraphs and breaks](gfm-01-headings-paragraphs-and-breaks.md)

- [ ] H-01 · ATX headings, levels 1 to 6
- [ ] H-02 · Seven hashes is not a heading
- [ ] H-03 · A space is required after the hashes
- [ ] H-04 · Closing hashes
- [ ] H-05 · Escaped hash and leading spaces
- [ ] H-06 · Empty headings
- [ ] H-07 · Setext headings
- [ ] H-08 · Multi-line Setext heading
- [ ] H-09 · Inline formatting in headings
- [ ] H-10 · Three characters
- [ ] H-11 · Spaced and long rules
- [ ] H-12 · Not a rule
- [ ] H-13 · Hyphens under a paragraph make a heading, not a rule
- [ ] H-14 · Paragraphs are separated by blank lines
- [ ] H-15 · Soft line break
- [ ] H-16 · Hard line break with two trailing spaces
- [ ] H-17 · Hard line break with a backslash
- [ ] H-18 · No hard break at the end of a paragraph
- [ ] H-19 · Leading spaces in a paragraph

### [GFM 02 · Code blocks and code spans](gfm-02-code.md)

- [ ] C-01 · Four-space indent
- [ ] C-02 · Blank lines inside an indented block
- [ ] C-03 · An indented block cannot interrupt a paragraph
- [ ] C-04 · Backtick fence
- [ ] C-05 · Tilde fence
- [ ] C-06 · Language info string
- [ ] C-07 · Info string with extra words
- [ ] C-08 · A longer fence can contain a shorter one
- [ ] C-09 · A tilde fence can contain backticks
- [ ] C-10 · The closing fence can be longer
- [ ] C-11 · Indented fence
- [ ] C-12 · Empty fenced block
- [ ] C-13 · HTML and Markdown inside code are not rendered
- [ ] C-14 · Single backticks
- [ ] C-15 · A backtick inside a code span
- [ ] C-16 · Spaces around a code span
- [ ] C-17 · No escapes or entities inside a code span
- [ ] C-18 · An unclosed fence runs to the end of the article

### [GFM 03 · Lists and task lists](gfm-03-lists-and-task-lists.md)

- [ ] L-01 · The three bullet markers
- [ ] L-02 · Changing the marker without a blank line
- [ ] L-03 · Nested bullets, three levels
- [ ] L-04 · The two number delimiters
- [ ] L-05 · The start number is kept
- [ ] L-06 · Only the first number matters
- [ ] L-07 · Only a list starting at 1 can interrupt a paragraph
- [ ] L-08 · Nested numbered and bullet lists
- [ ] L-09 · Tight and loose lists
- [ ] L-10 · Several paragraphs in one item
- [ ] L-11 · Lazy continuation line
- [ ] L-12 · Code, quote and heading inside an item
- [ ] L-13 · Empty list item
- [ ] L-14 · Ending a list before a code block
- [ ] L-15 · Unchecked and checked
- [ ] L-16 · Nested task list
- [ ] L-17 · Tasks in a numbered list and mixed with plain items
- [ ] L-18 · Not task lists
- [ ] L-19 · Formatting after a checkbox

### [GFM 04 · Block quotes and alerts](gfm-04-block-quotes-and-alerts.md)

- [ ] Q-01 · Basic quote
- [ ] Q-02 · Space after the marker is optional
- [ ] Q-03 · Several paragraphs
- [ ] Q-04 · A blank line splits the quote
- [ ] Q-05 · Lazy continuation
- [ ] Q-06 · Nested quotes
- [ ] Q-07 · Headings, lists and code inside a quote
- [ ] Q-08 · Inline formatting inside a quote
- [ ] Q-09 · Empty quote
- [ ] Q-10 · Note and tip
- [ ] Q-11 · Important, warning and caution
- [ ] Q-12 · Alert with several paragraphs and a list
- [ ] Q-13 · Not alerts

### [GFM 05 · Inline formatting and escapes](gfm-05-inline-formatting-and-escapes.md)

- [ ] I-01 · Emphasis with asterisks and underscores
- [ ] I-02 · Strong with asterisks and underscores
- [ ] I-03 · Strong and emphasis together
- [ ] I-04 · Nested emphasis inside strong
- [ ] I-05 · Inside a word
- [ ] I-06 · Spaces stop emphasis
- [ ] I-07 · Unmatched markers
- [ ] I-08 · One and two tildes
- [ ] I-09 · Three tildes is not strikethrough
- [ ] I-10 · Strikethrough with other styles
- [ ] I-11 · Strikethrough across a line break
- [ ] I-12 · Every escapable punctuation character
- [ ] I-13 · Escaping Markdown syntax
- [ ] I-14 · Escaping at the start of a line
- [ ] I-15 · A backslash before other characters stays
- [ ] I-16 · Named entities
- [ ] I-17 · Numeric entities
- [ ] I-18 · Not entities
- [ ] I-19 · Escaping an entity

### [GFM 06 · Links, images and autolinks](gfm-06-links-images-and-autolinks.md)

- [ ] K-01 · Link with and without a title
- [ ] K-02 · Destination in angle brackets
- [ ] K-03 · Balanced parentheses and an empty destination
- [ ] K-04 · Formatting inside link text
- [ ] K-05 · Brackets inside link text
- [ ] K-06 · Link to a heading in this article
- [ ] K-07 · Relative link to another article
- [ ] K-08 · Full, collapsed and shortcut references
- [ ] K-09 · Labels ignore case and spacing
- [ ] K-10 · Definition before use, and with angle brackets
- [ ] K-11 · Undefined reference
- [ ] K-12 · Angle-bracket autolinks
- [ ] K-13 · Not autolinks
- [ ] K-14 · www and http links
- [ ] K-15 · Trailing punctuation and parentheses
- [ ] K-16 · Bare email addresses and protocols
- [ ] K-17 · Not extended autolinks
- [ ] K-18 · Inline image with alt text and title
- [ ] K-19 · Reference image and empty alt text
- [ ] K-20 · Image as a link
- [ ] K-21 · Formatting in alt text
- [ ] K-22 · Repository image, two path styles

### [GFM 07 · Tables](gfm-07-tables.md)

- [ ] T-01 · Basic table
- [ ] T-02 · Without outer pipes
- [ ] T-03 · Uneven spacing and a one-hyphen delimiter
- [ ] T-04 · Header row only
- [ ] T-05 · One column
- [ ] T-06 · Left, centre, right and default
- [ ] T-07 · Inline formatting in cells
- [ ] T-08 · Escaped pipes
- [ ] T-09 · Empty cells
- [ ] T-10 · Missing and extra cells
- [ ] T-11 · Mismatched delimiter row is not a table
- [ ] T-12 · Where a table ends
- [ ] T-13 · A table right after a paragraph
- [ ] T-14 · Wide table

### [GFM 08 · Raw HTML and the tag filter](gfm-08-raw-html-and-tag-filter.md)

- [ ] R-01 · A div with and without blank lines
- [ ] R-02 · HTML table
- [ ] R-03 · Preformatted block
- [ ] R-04 · Collapsible section
- [ ] R-05 · Open by default
- [ ] R-06 · Comments
- [ ] R-07 · Attributes
- [ ] R-08 · Formatting tags
- [ ] R-09 · Line break tag
- [ ] R-10 · Link and image tags
- [ ] R-11 · Markdown inside inline HTML
- [ ] R-12 · Text that looks like HTML but is not
- [ ] R-13 · Script
- [ ] R-14 · Style
- [ ] R-15 · Iframe
- [ ] R-16 · Title, textarea and xmp
- [ ] R-17 · Noembed and noframes
- [ ] R-18 · Plaintext (keep last)
