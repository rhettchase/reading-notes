# Class-01 Reading Notes: Setup Developer Toolbelt

## Getting Started

### Compose a short poem describing how HTTP sends data between computers.

```ai
In cyberspace, where connections gleam,
HTTP's the language for a digital dream,
It bridges gaps 'twixt client and server,
In packets of data, it's quite the observer.

A lingua franca, for devices to converse,
Defining the way, they share and disperse,
With headers and bodies, it conveys the art,
Linking worlds, from heart to heart.
```

*source:* ChatGPT

- HTTP is an application-level protocol on top of TCP/IP, a communication protocol
- HTTP has been defined to communicate information between two pieces of software via HTTP messages. The way we shape and design these messages has consequences on the client (the browser for example), the server (web site) and their intermediaries (the proxy).

*source*: [dev.opera.com](https://dev.opera.com/articles/http-basic-introduction/)

### Describe how HTML, CSS, and JS files are “parsed” in the browser.

- browser parses the HTML file first
  - browser recognizing any `<link>` element references to external CSS stylesheets and any `<script>` element references to scripts.
- As the browser parses the HTML, it sends requests back to the server for any CSS files it has found from `<link>` elements, and any JavaScript files it has found from `<script>` elements, and from those, then parses the CSS and JavaScript.
- The browser generates an in-memory [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) tree from the parsed HTML, generates an in-memory [CSSOM](https://developer.mozilla.org/en-US/docs/Glossary/CSSOM) structure from the parsed CSS, and [compiles and executes](https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work#javascript_compilation) the parsed JavaScript.
- As the browser builds the DOM tree and applies the styles from the CSSOM tree and executes the JavaScript, a visual representation of the page is painted to the screen, and the user sees the page content and can begin to interact with it.

*source*: [How the Web Works (MDN)](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works)

### How can you find images to add to a Website?

- search on Google Images
- To reduce copyright violations, use license filter (click on Tools > Usage rights option > Creative Commons licenses)

### How do you create a `String` vs a `Number` in JavaScript?

- To create a `string`, you must initialize it as a variable with a string value by surrounding it with quotes (single quotes `''`,  double quotes `""` or backticks (`` ` ``))

```js
const single = 'Single quotes';
const double = "Double quotes";
const backtick = `Backtick`;

console.log(single);
console.log(double);
console.log(backtick);
```

- to create a `number`, you initialize it by typing a number value without quote marks
- to convert a string to a number, you can pass the string value into the `Number()` constructor to return a number version of the value

```js
const myInt = 5;
const myFloat = 6.667;
console.log(myInt); // 5
console.log(myFloat); // 6.667
```

### What is a `Variable` and why are they important in JavaScript?

- variable is a container for a value (data), such as a number or a string
- They do not _contain_ values; they _grasp_ them—two variables can refer to the same value
- A program can access only the values that it still has a reference to
- Variables can also contain complex data and even entire functions

## Introduction to HTML

### What is an HTML attribute?

- `Attributes` contain extra information about the element that you don't want to appear in the actual content
- Example below:

```html
<p class ="editor-note">My cat is very grumpy</p>
```

- the `class` is the attribute *name* and `editor-note` is the attribute *value*
- The `class` attribute allows you to give the element a non-unique identifier that can be used to target it (and other elements with the same `class` value) with style information and other things

*source:* [Introduction to HTML (MDN)](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)

### Describe the Anatomy of an HTML element

A typical HTML element includes:

- Opening tag with some attributes:
  - `Opening tag` consists of the name of the element, wrapped in opening and closing **angle brackets** and states where the elment begins or starts to take effect
  - `Attributes` contain extra information about the element
- `Enclosed text content`: in this case, is just text
- `Closing tag`: States where the element ends — in this case where the paragraph ends.

### What is the Difference between `<article>` and `<section>` element tags?

- The `article` element represents a self-contained composition in a document, page, application, or site, which is intended to be independently distributable or reusable (e.g., in syndication).
- The `section` element represents a generic standalone section of a document, which doesn't have a more specific semantic element to represent it. Sections should always have a heading, with very few exceptions.
- The difference between the `article` and `section` elements is their intent
  - If the contents of the element represent a standalone, atomic unit of content that makes sense syndicated as a standalone piece (e.g. a blog post or blog comment, or a newspaper article), the `<article>` element would be the better choice
  - `<section>` is a generic sectioning element, and should only be used if there isn't a more specific element to represent it

*source*: [Document and website structure (MDN)](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)

### What Elements does a “typical” website include?

- `<!DOCTYPE html>`: The doctype needs to be included for everything else to work right.
- `<html></html>`: The `<html>` element. This element wraps all the content on the page. It is sometimes known as the root element.
- `<head></head>`: The `<head>` element. This element acts as a container for everything you want to include on the HTML page, that isn't the content the page will show to viewers. This includes keywords and a page description that would appear in search results, CSS to style content, character set declarations, and more.
- `<meta charset="utf-8">`: The `<meta>` element. This element represents metadata that cannot be represented by other HTML meta-related elements, like `<base>`, `<link>`, `<script>`, `<style>` or `<title>`. The charset attribute specifies the character encoding for your document as UTF-8, which includes most characters from the vast majority of human written languages. With this setting, the page can now handle any textual content it might contain. There is no reason not to set this, and it can help avoid some problems later.
- `<title></title>`: The `<title>` element. This sets the title of the page, which is the title that appears in the browser tab the page is loaded in. The page title is also used to describe the page when it is bookmarked.
- `<body></body>`: The `<body>` element. This contains all the content that displays on the page, including text, images, videos, games, playable audio tracks, or whatever else.

*source:* [Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)

### How does metadata influence Search Engine Optimization?

Specifying a description that includes keywords relating to the content of your page is useful as it has the potential to make your page appear higher in relevant searches performed in search engines

### How is the `<meta>` HTML tag used when specifying metadata?

Many `<meta>` elements include name and content attributes:

- `name` specifies the type of meta element it is; what type of information it contains.
- `content` specifies the actual meta content.

```html
<meta name="author" content="Chris Mills" />
<meta
  name="description"
  content="The MDN Web Docs Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing websites and applications." />

```

*source:* [What's in the Head? Metadata in HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML
)

## How to start to design a Website

### What is the first step to designing a Website?

First, you should be able to answer the questions:

- What do you want to accomplish?
- How will a website help reach these goals?
- What needs to be done (and in what order) to reach these goals?

### What is the most important question to answer when designing a Website?

>What exactly do you want to accomplish

This is the most important question to answer since it drives everything else

*source:* [How do I start to design my website?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Design_and_accessibility/Thinking_before_coding)

## Semantics

### Why should you use an `<h1>` element over a `<span>` element to display a top level heading?

- the `h1` element is a semantic element, which gives the text it wraps around the role(or meaning) of a "top level heading on your page."
- Using a `span` element can be used to render it to look like a top level heading, but since it has no semantic value, it will not get any extra benefits

*source:* [semantics](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

### What are the benefits of using semantic tags in our HTML?

Some of the benefits from writing semantic markup:

- Search engines will consider its contents as important keywords to influence the page's search rankings (see SEO)
- Screen readers can use it as a signpost to help visually impaired users navigate a page
- Finding blocks of meaningful code is significantly easier than searching through endless divs with or without semantic or namespaced classes
- Suggests to the developer the type of data that will be populated
- Semantic naming mirrors proper custom element/component naming

*source:* [semantics](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

## What is Javascript?

### Describe 2 things that *require* JavaScript in the Browser?

- Client-side form validation: When a user submits a form on a web page (e.g., a login form, a registration form, or a contact form), JavaScript can be employed to check that the data entered is in the correct format and meets certain criteria
- Dynamic Content and Interactivity: JavaScript allows developers to create dynamic and interactive elements on web pages. It enables features such as image sliders, dropdown menus, accordions, and interactive maps

*source:* ChatGPT

### How can you add JavaScript to an HTML document?

Yes, you can add JavaScript to an HTML document by using the `<script>` tag

- you can add **Internal JavaScript**, which is internal to the HTML document:

```js
<script>
  // JavaScript goes here
</script>
```

- you can add **External JavaScript**, which is external to the HTML document by referencing an external `.js` file in the HTML document using the `<script>` tag:

```js
<script src="script.js" defer></script>
```

- you can use **Inline JavaScript handlers** that is bits of actual Javascript code living inside HTML. However, this is considered bad practice and it is recommended to use `addEventListener` instead, which is a pure JavaScript construct

```html
<script src="script.js" defer></script>
```

```js
function createParagraph() {
  const para = document.createElement("p");
  para.textContent = "You clicked the button!";
  document.body.appendChild(para);
}
```

- **Event Attributes** are used in HTML to let events trigger actions in a browser, like starting a JavaScript when a user clicks on an element.

## Things I want to know more about

- What are other common features that require JavaScript in the browser?