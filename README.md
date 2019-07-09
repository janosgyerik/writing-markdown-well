Writing Markdown well
=====================

A guide to writing readable, semantically correct, portable Markdown.

Why Markdown?
-------------

Markdown is a popular format for writing README files and simple technical
documents. It's meant to be [simple, easy to write, easy to read, in plain
text][philosophy].

A well-written README file can make a project more attractive to potential
users and contributors.

Why this document?
------------------

I often see markdown documents that are very hard to read, for example:

- Documents that only look good when viewed on GitHub.com or similar,
  and look very messy when reading in plain text in a shell console.

- Documents that violate semantic rules, for example skipping heading levels,
  or not using inline styles for their intended purpose.

- Documents using deeply nested or complicated structures, which are not
  rendered the same way in different markdown rendering engines, and hard to
  read in plain text form.

- Documents using extensions that don't work consistently in different
  rendering engines, and don't look good in plain text form.

I believe the cause of these issues is simply a lack of awareness. The general
markdown syntax is too permissive: even poorly written documents can pass for
technically valid markdown. It's difficult to catch and act on poor writing
style, because it doesn't have such grave consequences as programming errors.

The goal of this document is to help you write markdown that is:

- easy to read in plain text form
- semantically correct
- portable: renders consistently in common rendering engines

I aim to achieve that mainly by narrowing down your choices: when there are
many ways to achieve the same thing, I pick the one that is better than the
others, and explain why. With fewer choices to make about syntax, hopefully you
will have more time and energy to focus on what really matters: your content.

Some of the suggested techniques will be more tedious to write than some
alternatives.  This is not unexpected, because the goal is to optimize for
reading, not for writing.  This goal is based on the expectation that
documentation is read far more than it is written.  (Without that expectation
there's probably no point writing it.)

Why care about the plain text form anyway?
------------------------------------------

Markdown was designed to be [nicely readable as plain text][philosophy].

Even if you don't normally read markdown documents in their plain text form,
other consumers may want to do that, and they be dismayed by the project if you
didn't put enough care into writing it well. You may need to read in plain text
too, at least in the text editor when you make changes to the document later.

Therefore, it's good to write a document in a way that's easy to read. If
documentation is read far more than it is written, then the care you put into
writing well is worth the investment. (If you're reading this text in
a rendered form, take a look at the [plain text form here][source-code].)

High-level structures
---------------------

Headings drive the structure of a document. Therefore it's important to make
them stand out clearly.

### The title

Start a document with a top-level heading (h1) like this:

    Writing Markdown well
    =====================

Use as many `=` as letters in the title, for an "underline" effect. This
writing style is admittedly more tedious than others, but I think it stands out
the most clearly as a top-level title. I agree it's a pain in the ass that when
you modify the title you may have to delete or add `=` to fix the underlining,
but for the sake of readability, it's a fair price to pay.

A document should have one and only one title, therefore this formatting style
should only appear once.

Add a blank line after the title, to make it stand out even more, and to mimic
the padding added around titles in rich text formats.

Add a tagline or a short descriptive paragraph after the title.

### Section headings

Write a section heading (h2) like this:

    High-level structures
    ---------------------

The reasoning for this writing style is basically the same as for the top-level
title in the previous section.

### Sub-section headings

Write a sub-section heading (h3) like this:

    ### Heading levels should follow logical order

There is only one alternative writing style:

    ### Heading levels should follow logical order ###

That is, by adding `###` at the end of the line to match the beginning. Since
human eyes read from left to write, I think the trailing `###` don't add much
value for the reader, so I find that style redundant. Also kind of ugly.

Add a blank line before and after the sub-section heading, to make it stand out
a bit more, and to mimic the vertical padding added around sub-section headings
in rich text formats.

### Avoid deeper sub-sections

Some markdown rendering engines allow deeply nested sub-sections using `####`,
`#####` and `######`, but many don't (such as Stack Overflow).  Even when
a rendering engine allows such deep levels, the styling of these headings may
look surprising, and sometimes even ugly.

For a consistent reading experience in all rendering engines, I suggest to
avoid these deeper levels altogether.  Another good reason to avoid deep
hierarchies is to keep the document simple, which tends to be easier to read
and understand, therefore more enjoyable.

When you feel the need for deeper sub-sections, I suggest to either simplify
the overall structure, or to split the document to multiple files.

### Heading levels should follow logical order

A document should be structured as:

- the title
  - a section
    - optional: a sub-section
    - optional: another sub-section
    - ....
  - another section
  - ...

That is, there should not be a sub-section directly after the title.

Block structures
----------------

Block structures span entire lines, and usually consist of mulitple lines.
In Markdown they are:

- lists
- code blocks
- quoted text

### Lists

Lists can be unordered or numbered.

Unordered lists:

- Prefix items with `-`, `*` or `+`
- Use the same symbol consistently on the same level
  - Most rendering engines completely disregard whichever symbol you use, but
    consistency helps a lot when reading in plain text form

Numbered lists:

- Prefix items with numbers and a dot: `1.`, `2.`, ...
- Don't use all the same numbers: it will confuse readers of the plain text form
- Don't skip numbers: it will confuse readers of the plain text form

Common tips:

- Add a descriptive paragraph before the list.
  For example *this list you're reading* is introduced with "Common tips:".

- Add a blank line before and after the list: the vertical space creates
  a clear visual separation between distinct structural elements, which
  improves readability.

- If it improves readability, then add a blank line between list items
  - Do it consistently: either add a blank line between all items or not at all

When a list item is too long, break the line, and continue writing from the
begining of the text on the previous line, like this:

    - When a list item is too long, break the line, and continue writing from
      the begining of the text on the previous line, ...

To add a nested list, I indent by 2 spaces, like this:

    - top-level item
      - sub item
        - sub-sub item

Note that the ["spec"][syntax] doesn't actually mention anything about nesting
lists. I recommend 2 spaces to indent nested items because I find it better
than other alternatives:

- 1 space may not stand out enough as a nested item, it may look like a typo
- More than 2 spaces may be tedious to type
- I dislike tabs, because they are basically invisible characters, and the
  reading experience may depend on the viewer tool

Lists with deep hierarchy are not handled well by common rendering engines,
therefore I suggest to avoid them completely, keeping to maximum 3 levels.

The same goes for embedding code blocks or quoted text inside lists. They are
not handled consistently or sometimes not at all.

### Code blocks

To format as a code block, indent code snippets with 4 spaces, for example:

    View status with:

        git status -sb

An alternative syntax is to use so-called *fenced code blocks*, like this:

    Example code:

    ```
    ...
    # lots of code ...
    ...
    ```

However, this syntax is not standard, and using it reduces the portability of
the document.  Also, I find very often that this syntax hurts readability.
I prefer indenting with spaces to make the code block stand out within the
text, even if it's tedious to type.  (Again, keep in mind the goal to optimize
for reading, not for writing.)

If you really want to use fenced code blocks, for example because your typical
renderer will use nice syntax highlighting for it, then make sure to specify
the language of the source code. This may be necessary for the syntax
highlighting, and at the same time, it's probably a good thing to signal to the
reader explicitly the language of the source code, for example:

    ```python
    s = "Python syntax highlighting"
    print s
    ```

Add a blank line before and after fenced code blocks, to make it easy to
distinguish from other texts around it.

Don't try to nest code blocks inside lists, because it's not supported
consistently across rendering engines.

For example, in step by step guides I often feel natural to use bullet point
lists with some items containing code blocks of shell command instructions.
Although in some rendering engines code blocks can be embedded by indenting
with the correct number of spaces, the behavior is not consistent in all
rendering engines.  Therefore, reluctantly, I replace such bullet point lists
with paragraphs, which are handled consistently everywhere.

### Use blank lines generously

I think it's good to add a blank line before and after:

- headings
- lists
- code blocks

The generous vertical spacing creates a clear visual separation between
distinct structural elements, which in my opinion improves readability.

No need to use blank lines excessively. One blank line between block
elements is enough.

### Use introductory paragraphs before block elements

Publishers recommend to have an introductory paragraph in between:

- headings
- lists
- code blocks

Using inline styles correctly
-----------------------------

A document is easier to read when the inline styles are used correctly for
their intended purpose.

### Emphasis

Use `*emphasis*` for:

- Keywords, *when defined for the first time* within the text
- Key phrases, for example *single responsibility principle*

Don't use emphasis for code, `` `code style` `` is appropriate for that.

Both `*emphasis*` and `_emphasis_` are usually rendered as italic.
I prefer `*emphasis*` because:

- I think the pair of `*` stand out more than `_` when reading in plain text.
  I find that `_` is less visible, because it's too similar to a simple space.

- I think that text enclosed in `_` may give the impression of rendering as
  underlined text, which is not the case, and therefore misleading.

### Strong emphasis

I use `**strong emphasis**` to highlight GUI elements, such as:

- Window names
- Menu item names
- Button labels

Don't use strong emphasis for code, `` `code style` `` is appropriate for that.

I apply the same reasoning for `**strong emphasis**` over `__strong emphasis__`
as in the previous section about emphasis.

I don't have a deep reason to use **strong emphasis** for GUI elements.  It
seems the most appropriate style, I've been doing this for a long time, and I'm
still happy with it.

### Inline code

Use `` `inline code` `` for:

- Class, function, variable names
- Very short inline example code
- Names of executables, programs
- Filenames, filesystem paths
- Anything "code-like"

### Avoid combining inline styles

I think that nesting inline styles can be hard to read in plain text form,
because of visual overload of symbols.

Similarly, having multiple terms on a single line with some inline style can
make the text hard to read in plain text form.

### Embedding links

The embedded URL in this format disrupts the flow of the text in plain text form:

    The [syntax](https://daringfireball.net/projects/markdown/syntax) is too permissive.

In such cases it's better to use reference links, like this:

    The [syntax] is too permissive.

    ...

    [syntax]: https://daringfireball.net/projects/markdown/syntax

Other things to avoid
---------------------

Some other techniques and writing styles I recommend to avoid.

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
[source-code]: https://raw.githubusercontent.com/janosgyerik/writing-markdown-well/master/README.md
