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

I often see markdown documents that miss some of the important guiding principles,
leading to common mistakes such as:

- Documents that only look good when rendered on GitHub.com or similar,
  and look cryptic and crowded when reading in plain text in a shell console.

- Documents that violate semantic rules, for example skipping heading levels,
  or not using inline styles for their intended purpose,
  such as *emphasis* for `code statements` or vice versa.

- Documents using deeply nested or complicated structures, pushing the limits of
  the format, and very often not rendered consistently in different markdown
  viewers.

- Documents using extensions that don't work consistently in different viewers,
  sometimes for no benefit at all.

I believe the cause of these issues is simply a lack of awareness.  The general
markdown syntax is permissive, which allows poorly written documents to pass for
technically valid markdown.  It's difficult to catch and act on poor writing
style, because it doesn't have so apparent consequences as for example
programming errors.

The purpose of this document is to serve as a style guide,
in order to help you write markdown that is:

- easy to read in plain text format
- semantically correct
- portable: rendered consistently in common viewers

The ideas in this guide come from years of practice writing and reading in this
format.

The guidelines, TL;DR version
-----------------------------

For the impatient, a compact list of recommendations.  If you're interested in
the underlying reasoning, see the later sections.

### High-level structure

Start a document with a top-level (h1) heading like this:

    The title of the project
    ========================

Use as many `=` as letters in the title, for an "underline" effect.

There should be only one title.

Add a blank line after the title.

Add a description paragraph.

---

If sections are needed, add an h2 heading like this:

    The title of the section
    ------------------------

Use as many `-` as letters in the heading, for an "underline" effect.

Add a blank line before and after the heading.

---

If sub-sections are needed, add an h3 heading like this:

    ### The title of the sub-section

Add a blank line before and after the heading.

---

Avoid deeper sub-sections, even if your markdown reader allows `####`, `#####`
and more.

---

Heading levels should follow in logical order:
h1 -> h2 -> h3.
Do not skip heading levels.

---

As much as possible,
avoid sub-headings directly under a heading like this:

    Section
    -------

    ### Sub-section

That is, the "Section" should have some description before starting
"Sub-section".

### Lists

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

### Inline styles

Use `*emphasis*` for:

- Keywords, *when defined for the first time* within the text
- Key phrases, for example *single responsibility principle*

Don't use emphasis for code.

---

Use `**strong emphasis**` for:

I use them to highlight GUI elements, such as:

- Window names
- Menu item names
- Button labels

Don't use strong emphasis for code.

---

Use `` `inline code` `` for:

- Class names
- Function names
- Variable names
- Very short inline example code
- Executable names
- Filenames

---

Be mindful of the readability of the plain text form:

- Avoid nesting inline styles
- Avoid using too many inline styles on the same line

### Code blocks

Indent simple code blocks with 4 spaces, for example:

    View status with:

        git status -sb

If the code snippet is long and it's difficult to prepend 4 spaces to each line,
then using fenced code blocks can be acceptable, for example:

    Example code:

    ```
    ...
    # lots of code ...
    ...
    ```

However, keep in mind that the document is likely to be read more often than written.

Another acceptable case for fenced code blocks is when you can declare the language
to get nice syntax highlighting in typical viewers, for example:

    ```python
    s = "Python syntax highlighting"
    print s
    ```

Add a blank line before and after fenced code blocks.

### Links

Instead of embedded links like this:

    The [syntax](https://daringfireball.net/projects/markdown/syntax) is too permissive.

Prefer reference links like this:

    The [syntax][syntax] is too permissive.

    ...

    [syntax]: https://daringfireball.net/projects/markdown/syntax

Avoid bare URLs: better to give each URL a descriptive label.

### Vertical space

Use blank lines generously. Add a blank line before and after:

- headings
- lists
- code blocks

Don't use blank lines excessively. One blank line in between sections is enough.

### Introductory paragraphs

Publishers recommend to have an introductory paragraph in between:

- headings
- lists
- code blocks

### Other things to avoid

Don't do this:

- Don't embed HTML. Try to use strictly plain text format
- Don't use line breaks (two spaces at end of line)
- Don't use tables. The plain text formatting rules are not portable
- Don't use complicated features. Try to simplify the document instead
- If format is really so important, use HTML or some other rich text format.

### Tooling

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

    # line length
    MD013: false

    # trailing punctuation in heading
    MD026:
        punctuation: ".,;:!"

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

The guidelines, long version
----------------------------

More detailed than the TL;DR version above.
Only where necessary, I tried to avoid unnecessary duplication.

### Headings

Headings drive the structure of a document.
Therefore it's crucial that they are loud and clear.

---

These are multiple equivalent ways to write a top-level heading:

    Document    Document    Document    # Document  #Document
    =           ===         ========

All of these are normally rendered as H1 headings (`<h1>` in HTML).

I think this writing style looks unmistakably the top-level title,
loud and clear, easily visible:

    Document
    ========

---

These are multiple equivalent ways to write a level-2 section heading:

    Section     Section     Section     ## Section  ##Section
    -           ---         -------

All of these are normally rendered as H2 headings (`<h2>` in HTML).

I think this writing style looks unmistakably like a main section heading,
loud and clear, easily visible:

    Section
    -------

---

These are equivalent ways to write a level-3 heading:

    ### Sub-section     ###Sub-section     ### Sub-section ###

All of these are normally rendered as H3 headings (`<h3>` in HTML).

The heading text stands out a bit more when separated from the markers.
The closing `###` is also unnecessary, and noisy.
So I recommend this writing style:

    ### Sub-section

---

What about headings below level-3?
The original "spec" allows level 4-6 headers like this:

    #### sub-sub-section, rendered as <h4>
    ##### sub-sub-sub-oh-who-cares, rendered as <h5>
    ###### whatever, rendered as <h6>

Since level 4-6 headers are often not well-supported,
I think it's better to not use them.

I suggest the following workarounds:

- Move the section with deeply nested sub-sections to a separate document

- Reorganize the document to eliminate deep nesting

- If the sub-sections are small enough, consider replacing them with bullet lists

The bottom line is: deeply nested documents are hard to read, and therefore not
very useful.  Simplify the document to eliminate deeply nested headings.

---

The writing style should be semantically correct.

A document should have a title. And only one title.
The obvious formatting style for that is H1.
Avoid multiple H1 headings within the same document.

A document may have multiple sections.
The obvious formatting style for section headers is H2.

A document should have headings ordered by their levels,
with no gaps in between. For example:

- H1 followed by H2 followed by H3 is correct
- H1 followed by H3, skipping H2 is incorrect
- H3 followed by H2 is incorrect

Order headings correctly and don't skip levels.

---

A blank line before and after headings makes them stand out more.  The vertical
space creates a clear visual separation between distinct structural elements,
which in my opinion improves readability.

### Reasoning about lists

The reason I recommend to avoid complicated nested structures is because I've
seen wide variation in the output in different viewers.  It happened that
I spent precious time on getting the indentation right for my intended rendering
in my favorite viewer, and then discovered that a collaborator gets a different,
broken rendering in his favorite viewer.  By avoiding complex structures, I get
more predictable output, less time wasted on boring indentation tweaks, and
overall simpler documents that are actually easier to read.

### Reasoning about inline styles

Both `*emphasis*` and `_emphasis_` are usually rendered as italic.
I prefer `*emphasis*` because:

- I think the `*` stand out more than `_` when reading in plain text.  I find
  that `_` is less visible, because it's not too different from a space
  character.

- I think that text enclosed in `_` may give the impression of rendering as
  underlined text, which is not the case, and therefore would be misleading.

I apply the same reasoning for `**strong emphasis**` over `__strong emphasis__`.

I avoid `***doubly strong emphasis***` because I don't normally see a reason to
emphasize something excessively, and for the same reason that I avoid nesting
inline styles: I find that too many symbols on a line can clutter the content,
reducing readability.

I don't have a deep reason to use **strong emphasis** for GUI elements.  It
seems the most appropriate style, I've been doing this for a long time, and I'm
still happy with it.

### Reasoning about code blocks

The spec allows indenting with 4 spaces or a single tab.  I recommend to use
4 spaces, because they look the same everywhere, while the display width of tabs
may depend on the viewer.

I recommend to not use fenced code blocks, for two reasons:

- they are not supported by all viewers
- they make the plain text form look cryptic

Especially when a code snippet is just a few lines, and there are multiple code
snippets and paragraphs interleaved.

For example, I find this a lot easier to read in plain text:

    View the worktree status with:

        git status -sb

    See the details of what changed with:

        git diff --cached --check

Compared to this:

    View the worktree status with:
    ```
    git status -sb
    ```
    See the details of what changed with:
    ```
    git diff --cached --check
    ```

If you *must* use fenced code blocks, then the same as with other block
elements, I recommend a blank line before and after it, for a visual separation.

### Reasoning about other things to avoid

- The reason to avoid embedding HTML is because it's a sign that the document
  should probably not be written in markdown, but HTML or other rich format.

- The reason to not use trailing spaces a the end of lines is because
  2 or more trailing spaces have the special meaning of a linebreak in smart viewers,
  but they are invisible in plain text form, which is confusing.

- The reason to not use tables is because they are not a standard markdown feature,
  so you cannot count on consistent rendering. It's another sign that the document
  should probably not be written in markdown, but HTML or other rich format.

- The reason to not use complicated features is to keep the plain text form,
  and the document easy to read, and simple is usually easier to read than complex.

See also
--------

Related links:

- [A strongly defined, highly compatible specification of Markdown](http://commonmark.org/)
- [Standard Flavored Markdown](http://blog.codinghorror.com/standard-flavored-markdown/)
- [What’s Wrong with Markdown?](http://www.adamhyde.net/whats-wrong-with-markdown/)

[syntax]: https://daringfireball.net/projects/markdown/syntax
[philosophy]: https://daringfireball.net/projects/markdown/syntax#philosophy
[markdownlint]: https://github.com/DavidAnson/markdownlint
