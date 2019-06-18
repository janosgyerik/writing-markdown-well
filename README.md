Writing Markdown well
=====================

A guide to writing readable, semantically correct, portable Markdown.

Why Markdown?
-------------

Markdown is a popular format for writing README files and simple technical
documents.  It's *meant to be* simple, easy to write and to read, in plain text.

A well-written README file is crucial to making a project attractive to
potential contributors.

Why this document?
------------------

I often see markdown documents that are very hard to read, for example:

- Documents that only look good when viewed on GitHub.com or similar,
  and look very messy when reading in plain text in a shell console.

- Documents that violate semantic rules, for example skipping heading levels,
  or not using inline styles for their intended purpose, for example
  using *emphasis* for `code statements` or vice versa.

- Documents using deeply nested or complicated structures, which are not
  rendered the same way in different markdown viewers, and hard to read in
  plain text form.

- Documents using extensions that don't work consistently in different viewers,
  and don't look good in plain text form.

I believe the cause of these issues is simply a lack of awareness.  The general
markdown syntax is overly permissive: even poorly written documents pass for
technically valid markdown.  It's difficult to catch and act on poor writing
style, because it doesn't have such grave consequences as programming errors.

The goal of this document is to help you write markdown that is:

- easy to read in plain text form
- semantically correct
- portable: renders consistently in common viewers

I aim to achieve that mainly by reducing your choices: when there are many ways
to achive the same thing, I try to suggest the one that's in my opinion better
than the others, and explain why.  With fewer choices to make about syntax, as
a nice side effect, hopefully you will have more time and energy left to focus
on what really matters: your content.

Some of my suggestions may seem more typing, more work to do.  That's expected:
the ideas here are to optimize documents for reading.  I think minor
inconveniences in writing are acceptable.

Why care about the plain text form anyway?
------------------------------------------

Markdown was designed to be [nicely readable as plain text][philosophy].

You may not normally read it in plain text form, but sometimes you might still
need to.

Your readers may want to read your documents in plain text.
It's only natural, the format was designed for that!

When you need to make changes to a markdown document,
you will probably have to work with the plain text form.

For all the above reasons, it's good to write the document in a way to make it
easy to read.  Keep in mind that a typical document is read far more often than
it is written.  Therefore, the care you put into writing well is probably worth
the investment.

How to create high-level structures well
----------------------------------------

Headings drive the structure of a document.  Therefore it's crucial that they
are loud and clear.

### Give the document a title

Start a document with a top-level heading (h1) like this:

    The title of the project
    ========================

Use as many `=` as letters in the title, for an "underline" effect.  This way
is more typing than other writing styles, but I think this style stands out the
most clearly as a top-level title.

A document should have one and only one title, therefore it makes sense that
this formatting style should only appear once.

Add a blank line after the title, to make it stand out even more, and to mimic
the vertical padding added around titles in rich text formats.

Add a tagline or a descriptive paragraph before adding other formatting
elements.  For example a section title following a title directly is not
considered good form by book publishers.  Headings should not be "empty",
it's good if they have some content.

### How to add sections

Write a section heading (h2) like this:

    The title of the section
    ------------------------

Use as many `-` as letters in the heading, for an "underline" effect.  This way
is more typing than other writing styles, but I think this style stands out the
most clearly as a section title.

Add a blank line before and after the heading, to make it stand out even more,
and to mimic the vertical padding added around titles in rich text formats.

### How to add sub-sections

Write a sub-section heading (h3) like this:

    ### The title of the sub-section

The only alternative is similar to this style, with `###` added at the end.
Since human eyes read from left to write, the trailing `###` do not add new
information the eyes haven't seen already, so I find that style redundant, and
also kind of ugly.

Add a blank line before and after the heading, for the same reason as section
titles.

### How to add deeper sub-sections

I suggest to avoid deeper sub-sections. Some markdown viewers allow `####`,
`#####` and more, but not all. In viewers that don't allow the deeper levels,
the document will not look good. I take that as a hint to keep markdown
documents simple. When you feel the need for deeper sub-sections, I suggest to
either simplify the overall structure, or to split the document to multiple
files.

### Make sure heading levels follow logical order

Heading levels should follow in logical order: h1 -> h2 -> h3.
In other words, don't skip h2 between an h1 and an h3.

How to create block structures well
-----------------------------------

Some block structures can be written in many ways, some better than others.

### How to write lists

Unordered lists:

- Prefix items with `-`, `*` or `+`
- Use the same symbol consistently on the same level

Numbered lists:

- Prefix items with numbers and a dot, like `1.`, `2.`, ...
- Don't use all the same numbers: it will confuse readers of the plain text form
- Don't skip numbers: it will confuse readers of the plain text form

Common tips:

- Add a descriptive paragraph before the list
  (just like this one, prefixed with "Common tips:")

- Add a blank line before and after the list: the vertical space creates a clear
  visual separation between distinct structural elements, which in my opinion
  improves readability.

- If it improves readability, then add a blank line between list items
  - Do it consistently: either add a blank line between all items or not at all

If a list item is too long, break the line, and continue writing from the
begining of the text on the previous line, like this:

    - If it improves readability,
      then add a blank line between list items

To add a nested list, indent by 2 spaces, like this:

    - top-level item
      - sub item
        - sub-sub item

Avoid complicated structures:

- Avoid deeply nested lists (3 levels max)
- Don't try to put code blocks or quoted text inside lists

To avoid complicated structures, you probably need to rethink the organization
of your content.  Don't try to fight it. Don't try to micro-optimize.

### How to write code blocks

Indent simple code snippets with 4 spaces, for example:

    View status with:

        git status -sb

If the code snippet is long and it's difficult to prepend 4 spaces to each
line, then using fenced code blocks can be acceptable, though not great, for
example:

    Example code:

    ```
    ...
    # lots of code ...
    ...
    ```

Another acceptable case for fenced code blocks is when you can declare the language
to get nice syntax highlighting in typical viewers, for example:

    ```python
    s = "Python syntax highlighting"
    print s
    ```

Add a blank line before and after fenced code blocks, to make it easy to
distinguish from other texts around it.

Don't try to nest code blocks inside other block elements.  Even if you get the
syntax right for one specific viewer, it's likely to look incorrect in another
common viewer.  I think it's not worth the effort.  It's better to rethink and
simplify the document structure so that nesting is not necessary.

### Use blank lines generously

I think it's good to add a blank line before and after:

- headings
- lists
- code blocks

The generous vertical spacing creates a clear visual separation between
distinct structural elements, which in my opinion improves readability.

No need to use blank lines excessively. One blank line in between block
elements is enough.

### Use introductory paragraphs before block elements

Publishers recommend to have an introductory paragraph in between:

- headings
- lists
- code blocks

How to use inline styles correctly
----------------------------------

A document is easier to read when the inline styles are used correctly for
their intended purpose.

### When to use *emphasis*

Use `*emphasis*` for:

- Keywords, *when defined for the first time* within the text
- Key phrases, for example *single responsibility principle*

Don't use emphasis for code, `` `code style` `` is appropriate for that.

Both `*emphasis*` and `_emphasis_` are usually rendered as italic.
I prefer `*emphasis*` because:

- I think the `*` stand out more than `_` when reading in plain text.  I find
  that `_` is less visible, because it's not too different from a space
  character.

- I think that text enclosed in `_` may give the impression of rendering as
  underlined text, which is not the case, and therefore would be misleading.

### When to use **strong emphasis**

I use `**strong emphasis**` to highlight GUI elements, such as:

- Window names
- Menu item names
- Button labels

Don't use strong emphasis for code, `` `code style` `` is appropriate for that.

I don't have a deep reason to use **strong emphasis** for GUI elements.  It
seems the most appropriate style, I've been doing this for a long time, and I'm
still happy with it.

I apply the same reasoning for `**strong emphasis**` over `__strong emphasis__`
as in the previous section about emphasis.

### When to use `` `inline code` ``

Use `` `inline code` `` for:

- Class names
- Function names
- Variable names
- Very short inline example code
- Executable names
- Filenames

### When to combine inline styles

I think almost never.

Nesting inline styles can be hard to read in plain text form.

Similarly, having multiple terms on a single line with some inline style can
make the text hard to read in plain text form.

### How to embed links

The embedded URL in this format disrupts the flow of the text in plain text form:

    The [syntax](https://daringfireball.net/projects/markdown/syntax) is too permissive.

In such cases it's better to use reference links, like this:

    The [syntax][syntax] is too permissive.

    ...

    [syntax]: https://daringfireball.net/projects/markdown/syntax

Other things to avoid
---------------------

Don't do this:

- Don't embed HTML. Try to use strictly plain text format.
  - Wanting to embed HTML is a sign that the document is becoming too complex
    for markdown. In this case I think it's better to restructure the document
    to simplify it, or to use a proper rich text format.

- Don't use line breaks (two spaces at end of line).
  - Trailing spaces are invisible in plain text form, and 2 spaces at the end
    of the line mean a line break (`<br/>`) in markdown. This can be confusing,
    so I think it's better not to use this feature at all.

- Don't use tables. The plain text formatting rules are not portable.
  - Just like wanting to use HTML, I think this is a sign that perhaps the
    document should not be written in markdown, but a full-blown rich text
    format instead.

- Don't use complicated features. Try to simplify the document instead.
  - A complex document is likely hard to read, especially in plain text form.

Tooling
-------

There is a [markdownlint][markdownlint] tool to enforce the markdown style rules
you want to enforce.

Create `package.json`:

    {
      "scripts": {
        "test": "markdownlint -i node_modules ."
      },
      "dependencies": {
        "markdownlint-cli": "^0.16.0"
      }
    }

Create `.markdownlint.yaml` file with custom configuration, for example:

    # heading style
    MD003:
        style: setext_with_atx

    # line length. In Vim, you can do :setl tw=80 and gq} at the beginning of paragraphs
    #MD013: false

    # trailing punctuation in heading
    MD026:
        punctuation: ".,;:!"

Related articles
----------------

Related articles you might be interested in:

- [A strongly defined, highly compatible specification of Markdown](http://commonmark.org/)
- [Standard Flavored Markdown](http://blog.codinghorror.com/standard-flavored-markdown/)
- [What’s Wrong with Markdown?](http://www.adamhyde.net/whats-wrong-with-markdown/)

[syntax]: https://daringfireball.net/projects/markdown/syntax
[philosophy]: https://daringfireball.net/projects/markdown/syntax#philosophy
[markdownlint]: https://github.com/DavidAnson/markdownlint
