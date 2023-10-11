# Class-04 Reading Notes: Structure web pages with HTML

## What is HTML and why do we use it?

HTML (**H**yper**T**ext **M**arkup **L**anguage) is the code that is used to *structure* a web page and its content

- Consists of a series of [elements](https://developer.mozilla.org/en-US/docs/Glossary/Element), used to enclose (wrap) content to make it appear or act a certain way
- A [tag](https://developer.mozilla.org/en-US/docs/Glossary/Tag) is used for creating an element
- The name of an HTML element is the name that appears at the beginning of the element's start tag and at the end of the element's end tag (if the element has an end tag)
  - Example: The `p` in the `<p>` start tag and `</p>` end tag is the name of the HTML paragraph element.

## What are the 3 main parts of an HTML element?

![Anatomy of HTML Element](html-element.png)

A typical HTML element includes:

- Opening tag with some attributes:
  - `Opening tag` consists of the name of the element, wrapped in opening and closing **angle brackets** and states where the elment begins or starts to take effect
  - `Attributes` contain extra information about the element
- `Enclosed text content`: in this case, is just text
- `Closing tag`: States where the element ends — in this case where the paragraph ends.

## What is it called when you give an element extra information?

- `Attributes` contain extra information about the element that you don't want to appear in the actual content
- Example below:

```html
<p class ="editor-note">My cat is very grumpy</p>
```

- The `class` is the attribute *name* and `editor-note` is the attribute *value*
- The `class` attribute allows you to give the element a non-unique identifier that can be used to target it (and other elements with the same `class` value) with style information and other things

## What is a semantic element?

- Semantic elements give the text it wraps around its role (or meaning)
- When deciding which markup to use, ask *"What element(s) best describe/represent the data that I'm going to populate?"* then select the semantic element most appropriate for the job

- Example: `h1` element gives the text instruction of "a top level heading on your page"

```html
<h1>This is a top level heading</h1>
```

- By adding semantic HTML tags to your pages, you provide additional information that helps define the roles and relative importance of the different parts of your page

### Examples of semantic elements

```html
<article>
<aside>
<details>
<figcaption>
<figure>
<footer>
<form>
<header>
<main>
<mark>
<nav>
<section>
<summary>
<time>
  ```

### Examples of elements that are *not* semantic

```html
<head>
<b>
<span>
<div>
```

### Benefits from writing semantic markup

- Search engines will consider its contents as important keywords to influence the page's search rankings (see [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO))
- Enables accessibility (e.g., screen readers can use it as a signpost to help visually impaired users navigate a page)
- Finding blocks of meaningful code is significantly easier
- Suggests to the developer the type of data that will be populated
- Semantic naming mirrors proper custom element/component naming
