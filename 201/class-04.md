# Class-04 Reading Notes: HTML Links, JS Functions, and Intro to CSS Layout

## Learn HTML

*source:* [Creating Hyperlinks](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)

### To create a basic link, we wrap text or other content inside what element?

- use the anchor element `<a>`
- A basic link is created by wrapping the text or other content inside an `<a>` element and using the `href` attribute

```html
 <a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
 ```

### The `href` attribute contains what information?

- The URL that the hyperlink points to. Links are not restricted to HTTP-based URLs — they can use any URL scheme supported by browsers

### What are some ways we can ensure links on our pages are accessible to all readers?

- Use descriptive text for link text - The content inside a link should indicate where the link goes, even out of context.
- Avoid using URLs as link text
- use semantic HTML for links
- Use appropriate HTML elements like `<a>` (anchor) tags for links. Avoid using non-semantic elements like `<div>` or `<span>` for links
- Use Alt Text for Linked Images

## CSS Layout

*sources:* [CSS Layout: Normal Flow](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow), [CSS Layout: Positioning](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning), ChatGPT

### What is meant by “normal flow”?

- Elements on webpages lay themselves out according to normal flow - until we do something to change that.
- Starting with a solid, well-structured document that's readable in normal flow is the best way to begin any webpage.
- Ensures that your content is readable even if the user's using a very limited browser or a device such as a screen reader that reads out the content of the page.

```html
<h1>Basic document flow</h1>

<p>
  I am a basic block level element. My adjacent block level elements sit on new
  lines below me.
</p>

<p>
  By default we span 100% of the width of our parent element, and we are as tall
  as our child content. Our total width and height is our content + padding +
  border width/height.
</p>

<p>
  We are separated by our margins. Because of margin collapsing, we are
  separated by the width of one of our margins, not both.
</p>

<p>
  Inline elements <span>like this one</span> and <span>this one</span> sit on
  the same line along with adjacent text nodes, if there is space on the same
  line. Overflowing inline elements will
  <span>wrap onto a new line if possible (like this one containing text)</span>,
  or just go on to a new line if not, much like this image will do:
  <img src="long.jpg" alt="snippet of cloth" />
</p>

```

### What are a few differences between `block-level` and `inline` elements? 

#### `block-level` elements

- In a block layout, boxes are laid out one after the other, vertically, beginning at the top of a containing block. Each box's left outer edge touches the left edge of the containing block.
- A block-level element always starts on a new line
- The paragraph(`<p>`) elements are block-level by default. That is why they are displayed in block layout

#### `inline` elements

- In inline layout, a mixed stream of text, [replaced elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element), and other inline boxes are laid out by fragmenting them into a stack of line boxes.
- Within each line box, inline-level boxes are aligned to each other vertically or horizontally, depending on the writing mode. Typically, they are aligned by the baselines of their text. This can be changed with CSS.

**Some differences between `block-level` and `inline` elements include**
**Display and layout:**

- Block-level elements start on a new line and typically expand to the full width of their containing element. They create a "block" of content. Examples include `<div>`, `<p>`, and headings like `<h1>`, `<h2>`.
- Inline elements flow within the content and do not start on a new line. They only take up as much width as necessary for their content. Examples include `<span>`, `<a>`, and text elements.
- **Line breaks:**
  - Block-level elements create line breaks before and after them, pushing content above and below.
  - Inline elements do not create line breaks. They flow within the current line of text or content.
- **Width and Height**:
  - Block-level elements can have their width and height set explicitly and can be controlled with CSS properties like `width`, `height`, `margin`, and `padding`.
  - Inline elements have limited control over their width and height. Margins and padding may apply, but their width and height are generally determined by the content they contain.
- **Nesting**:
  - Block-level elements can contain other block-level and inline elements, making them suitable for structuring page layouts.
  - Inline elements can be nested within block-level elements and other inline elements but generally should not contain block-level elements.
- **Default Styling**:
  - Block-level elements often have default styling that begins on a new line with a margin and padding, making them more suitable for creating distinct sections in a page layout.
  - Inline elements often inherit their styling from the surrounding text or content and do not disrupt the flow of text.
- **Examples**:
  - Common block-level elements include headings (`<h1>` to `<h6>`), paragraphs (`<p>`), divs (`<div>`), lists (`<ul>`, `<ol>`), and most structural and container elements.
  - Common inline elements include links (`<a>`), spans (`<span>`), emphasized text (`<em>`), strong text (`<strong>`), and elements used for text-level styling.

### **__**_ positioning is the default for every html element

- `default positioning` property determines how elements are placed within the document flow
- `Static positioning` is the default that every element gets. It just means "put the element into its normal position in the document flow — nothing special to see here."
- **Static Positioning (default)**:
  - By default, most HTML elements have a "static" positioning property. This means that they are positioned in the normal document flow according to the order in which they appear in the HTML code.
  - Elements with static positioning are not affected by the `top`, `right`, `bottom`, or `left` properties in CSS
- **Inline Positioning (default for inline elements)**:
  - Inline-level elements (e.g., `<span>`, `<a>`, `<strong>`, `<em>`) are typically displayed "inline" by default. This means they flow with the surrounding text or content and do not create line breaks.
  - Inline elements are affected by the `top`, `right`, `bottom`, or `left` properties in CSS. However, they may not be affected by properties like `width` or `height.
- To change the default positioning, you would use the `position` property in CSS.

### Name a few advantages to using `absolute positioning` on an element

- An absolutely positioned element no longer exists in the normal document flow. Instead, it sits on its own layer separate from everything else.
- This is very useful: it means that we can create isolated UI features that don't interfere with the layout of other elements on the page. For example, popup information boxes, control menus, rollover panels, UI features that can be dragged and dropped anywhere on the page, and so on.

#### `absolute position` Notes:

- [`top`](https://developer.mozilla.org/en-US/docs/Web/CSS/top), [`bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom), [`left`](https://developer.mozilla.org/en-US/docs/Web/CSS/left), and [`right`](https://developer.mozilla.org/en-US/docs/Web/CSS/right) behave in a different way with absolute positioning. Rather than positioning the element based on its relative position within the normal document flow, they specify the distance the element should be from each of the containing element's sides
- move with their nearest positioned ancestor. If none exists, they behave like fixed-positioned elements, remaining in the same position even when the page is scrolled.
- often used for creating layered elements within a container or for fine-grained control over the positioning of elements within a layout.

```css
position: absolute;
```

### What is a key difference between `fixed positioning` and `absolute positioning`?

- `Fixed-positioned` elements do not move as the user scrolls the page. They stay "fixed" in their specified location on the screen - commonly used for elements like navigation menus or headers that should remain visible as users scroll through the content
- **Key difference:** whereas `absolute positioning` fixes an element in place relative to its nearest positioned ancestor (the initial containing block if there isn't one), **`fixed positioning`** _usually_ fixes an element in place relative to the visible portion of the viewport.
  - An exception to this occurs if one of the element's ancestors is a fixed containing block because its [transform property](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) has a value other than _none_.

```css
h1 {
  position: fixed;
  top: 0;
  width: 500px;
  margin-top: 0;
  background: white;
  padding: 10px;
}
```

- The `top: 0;` is required to make it stick to the top of the screen. We give the heading the same width as the content column and then a white background and some padding and margin so the content won't be visible underneath it.

## Learn JS

*source*: [Functions – Reusable Blocks of Code](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions), [Eloquent JavaScript](https://eloquentjavascript.net/03_functions.html), ChatGPT

### Describe the difference between a function declaration and a function invocation.

- A function declaration is the process of creating a named function with a defined set of statements that can be executed later.
- When the `function` keyword is used at the start of a statement, this is a function *declaration*

```js
function square(x) {
  return x * x;
}
```

- Executing a function is called `invoking`, _calling_, or _applying_ it. You can call a function by putting parentheses after an expression that produces a function value. Usually you’ll directly use the name of the binding/variable that holds the function
- Function invocations are executed at the point in your code where you call the function. When a function is invoked, the code within the function declaration is executed.

### What is the difference between a parameter and an argument?

**Parameters**

- A parameter is a variable or placeholder name listed in the function declaration. It serves as a placeholder for the values that will be passed to the function when it's invoked.
- Parameters define the inputs that the function expects to receive, and they are used within the function to perform operations or computations. They act as local variables that store the values passed as arguments when the function is called
- Found in the function's *parameter list* within the `function declaration`

```js
function myFunction(parameter1, parameter2) {
    // ...
}
```

**Arguments**

- An argument is the actual value or expression that is passed to a function when it's invoked. Arguments are the concrete data that you provide to the function for it to work with.
- Found in a *function call*, within the parentheses

```js
myFunction(argument1, argument2);
```

## Pair Programming

[6 Reasons for Pair Programming](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)

## Pick 2 benefits to pair programming and reflect on how these benefits could help you on your coding journey

- **Greater efficiency** - while pair programming may take slightly longer, it produces higher-quality code that requires less troubleshooting and debugging. I think this makes sense, since the code must be clear from multiple perspectives and you have another person working through bugs and creative problem solving together
- **work environment readiness** - since many companies utilize pair programming for building a project or feature, or debugging an existing code base, learning pair programming in training is good practice
