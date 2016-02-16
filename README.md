Writing markdown well
=====================

*Note: work in progress, heavily...*

---

Markdown is important because it's used everywhere.

TODO: 3 images of sites that use it, side by side, with some sample markdown + rendered, easily identifiable

Every decent project should have at least a `README.md` file.

TODO: 2 images from GitHub create new project screen 1 and 2

It's also a great format for documentation.

Common mistakes when writing Markdown:

TODO: the coding-horror image; + acknowledgement at the bottom

- Looks good when rendered as HTML, but looks crap as plain text

- Semantic violations of headings and inline formatting styles

- Overly complicated nested structures

- Using not well-supported features, lock-in to specific renderers

- Other minor writing style issues

Philosophy
----------

Markdown was designed to be [nicely readable as plain text][philosophy].

You may not normally read it in plain text form, but sometimes you might still need to.

Other readers might read your documents in plain text.
Naturally: the format was designed for that!

When you update the document later, you typically have to work with the plain text form.

Which of these documents would you rather work with?

TODO: 2 examples side by side, in plain-text form, first crap second pretty

Headings
--------

Headings drive the structure of a document.
Therefore it's crucial that they are loud and clear.

### Top-level headings

These are multiple equivalent ways to write a top-level heading:

    Document    Document    Document    # Document  #Document
    =           ===         ========

All these are normally rendered as H1 headings (`<h1>` in HTML).

Which writing style should you prefer?

Which writing style is the most readable?

I recommend this one:

    Document
    ========

It stands out loud and clear, easily visible.

### Section headings (right below top-level)

These are multiple equivalent ways to write a level-2 heading:

    Section     Section     Section     ## Section  ##Section
    -           ---         --------

All these are normally rendered as H2 headings (`<h2>` in HTML).

Which writing style should you prefer?

Which writing style is the most readable?

You guessed it: I recommend this one:

    Section
    -------

It stands out loud and clear, easily visible.

### Level-3 headings

These are equivalent ways to write a level-3 heading:

    ### Sub-section     ###Sub-section     

All these are normally rendered as H3 headings (`<h3>` in HTML).

Which writing style should you prefer?

Which writing style is the most readable?

I recommend this one:

    ### Sub-section

This is more readable than when the symbols and text are stuck together.
The same way that code is more readable when you put spaces around operator symbols.

### Below level-3 headings

The original "spec" allows level 4-6 headers like this:

    #### sub-sub-section, rendered as <h4>
    ##### sub-sub-sub-oh-who-cares, rendered as <h5>
    ###### whatever, rendered as <h6>

Don't do this. Level 4-6 headers are often not well-supported.
Many renderers use normal paragraph style for such headers.

![headings-on-stackoverflow](screenshots/headings-on-stackoverflow.png)

I suggest the following workarounds:

- Move the section with deeply nested sub-sections to a separate document

- Reorganize the document to eliminate deep nesting

- If the sub-sections are small enough, consider replacing them with bullet lists

The bottom line is: deeply nested documents are hard to read,
and therefore not very useful. One way or another,
eliminate deeply nested headings by simplifying the document.

### Semantic correctness

It makes sense that the title of a document is special,
and it should be marked distinctively from other parts.

It makes sense that there should be only one such heading.
Avoid multiple H1 headings within the same document.

There can be multiple H2 headings within the top-level H1,
and there can be multiple H3 headings within H2 headings.

The document structure should have headings ordered by their levels,
with no gaps in between. For example:

- H1 followed by H2 followed by H3 is correct
- H1 followed by H3, skipping H2 is incorrect
- H3 followed by H2 is incorrect

Order headings correctly and don't skip levels.

Inline styles
-------------

Use inline styles for:

- *emphasis*: surround with single asterisks
- **strong emphasis**: surround with double asterisks
- `inline code`: surround with backticks

### Emphasis

What to use emphasis?

- Anything you want to emphasize
- Keywords, when defined for the first time within the text
- Key phrases, for example *single responsibility principle*

Don't use emphasis for code, commands (see inline code section below).

### Strong emphasis

When to use strong emphasis?

I use them to highlight GUI elements, such as:

- Window names
- Menu item names
- Button labels

Don't use strong emphasis for code, commands (see inline code section below).

### Inline code

Use inline code style for:

- Class names
- Function names
- Variable names
- Very short inline example code
- Executable names
- Filenames

Code blocks
-----------

The spec allows indenting with a single tab or 4 spaces.
Indent with 4 spaces. For the usual reason: it will look the same everywhere.

Here's one way to format code blocks:

    View status with:

        git status -sb

Here's an equivalent way to format code blocks:

    View status with:
    ```
    git status -sb
    ```

What's wrong with fenced code blocks?

- Not as well supported as indented code blocks
- In plain text they look strange, cryptic

What's good with fenced code blocks?

It's possible to specify the language used, and get syntax highlighting.
It's OK to use fenced code blocks when syntax highlighting is important and supported by the intended renderer.

Do add a blank line before and after fenced code blocks.

Other things to avoid
---------------------

- simplicity
  - don't use deeply nested, tricky structures
  - don't use html
  - don't use `&amp;` etc
  - don't use line breaks (two space at end of line)

- readability
  - horizontal spacing
    + space before starting `*` and after closing `*`
  - vertical spacing
    + empty line between heading and body
    + empty line between paragraph and list
    + empty line around horizontal rule
  - prefer `====` and `----` for headings
  - prefer indented code blocks over fenced code blocks
  - number properly in numbered lists
  - break lines between list items if too long
  - align list items
  - use different symbol at different levels // matter of taste
  - use horizontal rules in consistent format
  - prefer `*` over `_`
  - don't use `_` for horizontal rule

- compatibility
  - prefer indented code blocks over fenced code blocks
  - don't use below `###`

- links
  - prefer `[title][name]` + reference over inline `[title](link)`

- summary of recommendations against daring fireball
  - don't use HTML
  - don't bother escaping HTML entities such as `&amp;` etc
  - don't use line breaks (two space at end of line)
  - don't use below `###`
  - don't use fenced code blocks
  - number properly in numbered lists
  - don't be lazy
  - don't put code blocks inside lists
  - indent with 4 spaces instead of tabs

- publisher rules
  - paragraph between heading and sub-heading or list
  - `*` for keywords, key terms, on first occurrence only

- semantics
  - use headings right
  - forget italic and bold, think emphasis and important
  - use `*` and `**` and backticks right

- lazyness
  - don't bother closing `###` headers
  - `---` seems perfectly reasonable for horizontal rules
  - `-` easiest to write as bullet

Links
-----

http://commonmark.org/

http://blog.codinghorror.com/standard-flavored-markdown/

[spec]: http://commonmark.org/
[standard-flavored-markdown]: http://blog.codinghorror.com/standard-flavored-markdown/
[syntax]: https://daringfireball.net/projects/markdown/syntax
[philosophy]: https://daringfireball.net/projects/markdown/syntax#philosophy
[comparable]: https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html
