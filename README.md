Writing Markdown well
=====================

An opinionated guide to writing readable, semantically correct, portable Markdown.

Why Markdown?
-------------

Markdown is a popular format for writing README files and documentation.
It's simple, easy to read and to write, in plain text.

Nicely readable documentation is crucial to make your project look attractive to users and contributors.

What's wrong with Markdown?
---------------------------

There is no standard implementation, no standard style guide, no linters.
As a result, people adopt different, inconsistent, incorrect, and non-portable writing styles.

Examples of common mistakes:

- "It doesn't matter that the plain text is hard to read,
  as long as its rendered nicely in my viewer."
  
  Wrong. Markdown is designed to be easy to read in plain text format.
  It's very annoying when you are working in a shell terminal
  and the README is hard to read.

- "My viewer supports advanced formatting syntax, let's use it."
  
  Wrong. Don't limit your users to specific viewers. For example
  GitHub Flavored Markdown supports "fenced code blocks". These
  won't be rendered nicely in all viewers, and they look ugly in plain text.
  Markdown should be nicely readable as plain text. Avoid custom extensions,
  especially when they don't look good in plain text, and
  especially when better alternatives exist. In this example,
  indent with 4 spaces instead of using fenced code blocks.

- "In our viewer, H1 looks too big, so we use H3 instead."
  
  Wrong. The title of a document should be H1. Period. If you don't like
  how it's rendered in your viewer, fix the stylesheet in your viewer,
  or learn to live with it. Don't break the document's semantics for the sake of a viewer.
  
- "It's ok to write H3 after H1, skipping H2, because it looks good that way."
  
  Wrong. The heading levels in a document should be structured as
  H1 containing H2, H2 containing H3, without skipping levels in the middle.
  Don't let a crappy stylesheet used by the viewer force you to break the
  logical structure of your documents.

- "I prefer to use `**...**` instead of `*...*` because it looks better."
  
  Wrong. `*...*` means emphasis, `**...**` means stronger emphasis.
  Don't choose formatting styles depending on how they look in your viewer.
  Use the formatting styles for their intended purpose.

- "I don't know what `***...***` means but I like the way it looks in my viewer."
  
  Wrong. Learn what it means, and use it only if it's appropriate for the purpose.

- "I know this looks strange in plain text, but I have to write it this way
  to make it look good."

  Wrong. If you have to write something complicated, like nested elements
  of various styles, such as nested bullet point and ordered lists,
  or code blocks nested in bullet point lists, then look for ways to simplify
  your document. Reorganize the content to eliminate complex structures.

What is this guide?
-------------------

This is a collection of tips and recommendations when using Markdown.
It is based on my experience of writing and reading a lot in this format.
This is highly opinionated stuff, and you might not agree with everything.
My goal is to prevent the most common issues mentioned above.

Why care about the plain text form?
-----------------------------------

Markdown was designed to be [nicely readable as plain text][philosophy].

You may not normally read it in plain text form, but sometimes you might still need to.

Your readers may want to read your documents in plain text.
And that's perfectly reasonable, since the format was designed for that.

And let's not forget, when you make changes to a Markdown document,
most probably you will work with the plain text form.
If the plain text form is nicely readable, you will have an easier job updating it.

Headings
--------

Headings drive the structure of a document.
Therefore it's important that they follow a logical order.

### Top-level headings

These are multiple equivalent ways to write a top-level heading:

    Document    Document    Document    # Document  #Document
    =           ===         ========

All of these are normally rendered as H1 headings (`<h1>` in HTML).

This writing stye is loud and clear, easily visible:

    Document
    ========

### Section headings (right below top-level)

These are multiple equivalent ways to write a level-2 heading:

    Section     Section     Section     ## Section  ##Section
    -           ---         -------

All of these are normally rendered as H2 headings (`<h2>` in HTML).

This writing stye is loud and clear, easily visible:

    Section
    -------

### Level-3 headings

These are equivalent ways to write a level-3 heading:

    ### Sub-section     ###Sub-section     ### Sub-section ###

All of these are normally rendered as H3 headings (`<h3>` in HTML).

The heading text stands out a bit more when separated from the markers.
The closing `###` is also unnecessary, and noisy.
So I recommend this writing style:

    ### Sub-section

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

The bottom line is: deeply nested documents are hard to read, and therefore not very useful. Simplify the document to eliminate deeply nested headings.

### Semantic correctness

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

### Other style tips

Put a blank line before and after headings.

Don't nest headings without a paragraph in between.

Inline styles
-------------

Use inline styles for:

- `*emphasis*`: enclose with single asterisks
  - Don't use `_emphasis_`, it's less readable
- `**strong emphasis**`: enclose with double asterisks
  - Don't use `__strong emphasis__`, it's less readable
- `` `inline code` ``: enclose with backticks

### Emphasis

When to use *emphasis*?

- Anything you want to emphasize
- Keywords, when defined for the first time within the text
- Key phrases, for example *single responsibility principle*

Don't use emphasis for code, commands (see inline code section below).

### Strong emphasis

When to use **strong emphasis**?

I use them to highlight GUI elements, such as:

- Window names
- Menu item names
- Button labels

Don't use strong emphasis for code, commands (see inline code section below).

### Inline code

When to use `inline code`?

- Class names
- Function names
- Variable names
- Very short inline example code
- Executable names
- Filenames

### Mixing inline styles on the same line

Is this easy to read?

    The quick *brown fox* **jumps** *over* the lazy **dog**

Not really.

- Avoid nesting inline styles
- Avoid using too many inline styles on the same line

Code blocks
-----------

The spec allows indenting with 4 spaces or a single tab.
I suggest to use 4 spaces. For the usual reason: 4 spaces will look the same everywhere, while the display width of tabs may depend on the viewer.

Here's one way to format code blocks:

    View status with:

        git status -sb

Here's an equivalent way to format code blocks:

    View status with:
    ```
    git status -sb
    ```

What's wrong with fenced code blocks?

- Not supported so well as indented code blocks
- Doesn't look as clean and obvious in plain text

What's good about fenced code blocks?

They can allow language-specific syntax highlighting.
It's OK to use fenced code blocks when syntax highlighting is important and supported by the intended renderer.

Do add a blank line before and after fenced code blocks.

Lists
-----

Unordered lists:

- Prefix items with `-`, `*` or `+`
- Whichever symbol is fine, just use consistently, don't mix them
- I prefer `-` because it's easiest to write on a querty keyboard
- Tip: sometimes nested lists are easier to read if using a different symbol

Numbered lists:

- Prefix items with numbers and a dot, like `1.`, `2.`, ...
- The spec allows skipping numbers, or even `1.`, `1.`, `1.` but don't do that, as it will only look good in HTML, not in plain text

Other style tips:

- Avoid complicated/sophisticated structure, for example:
  - Don't try to put code blocks inside lists: it's complicated and poorly supported
  - Avoid deep nesting

- Add or omit empty lines between list items to improve readability
  - Do it consistently: either put an empty line between all items or none

Links
-----

Instead of embedded links like this:

    The [syntax](https://daringfireball.net/projects/markdown/syntax) is too permissive.

Prefer reference links like this:

    The [syntax][syntax] is too permissive.

    ...

    [syntax]: https://daringfireball.net/projects/markdown/syntax

Vertical spacing
----------------

Use blank lines generously. Add a blank line before and after:

- headings
- lists
- code blocks

Don't use blank lines excessively. One blank line in between sections should be enough.

Introductory paragraphs
-----------------------

Publishers recommend to have an introductory paragraph in between:

- headings
- lists
- code blocks

Things to avoid
---------------

Don't do this:

- Don't embed HTML. Try to use strictly plain text format
- Don't use line breaks (two spaces at end of line)
- Don't use tables. The plain text formatting rules are not portable
- Don't use complicated features. Try to simplify the document instead
- Don't use a WYSIWYG editor to edit Markdown. Such editors tend to generate poor Markdown
- If format is really so important, use HTML or some other rich text format.

Not concluded
-------------

Here's a summary of features I don't have a strong opinion (and recommendation) about, yet:

- Horizontal rules
  - https://daringfireball.net/projects/markdown/syntax#hr
  - I use `---` because it's easy to type and easy enough to see
  - Definitely don't use underscores (not aligned in the middle of the line)
  - Definitely use consistent format

- Use different symbols at different nesting levels of lists?

- How to indent multi-line numbered lists and bullet lists?

See also
--------

Related links:

- http://commonmark.org/
- http://blog.codinghorror.com/standard-flavored-markdown/
- http://www.adamhyde.net/whats-wrong-with-markdown/

[spec]: http://commonmark.org/
[standard-flavored-markdown]: http://blog.codinghorror.com/standard-flavored-markdown/
[syntax]: https://daringfireball.net/projects/markdown/syntax
[philosophy]: https://daringfireball.net/projects/markdown/syntax#philosophy
[comparable]: https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html
