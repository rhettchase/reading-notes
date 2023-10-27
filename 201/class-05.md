# Class-05 Reading Notes: Images, Color, Text

## HTML Media

*sources*: [HTML Media](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding), [Using Images In HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML),  [Common Image Types](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types), [Choosing Image Formats](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types#choosing_an_image_format), chatGPT

### What is a real world use case for the `alt` attribute being used in a website?

- `alt` value is supposed to be a textual description of the image, for use in situations where the image cannot be seen/displayed

*Use cases include:*

- accessibility (e.g., user visually impaired and using screen reader)
- spelling of the file or path name might be wrong
- The browser doesn't support the image type
- You may want to provide text for search engines to utilize

### How can you improve accessibility of images in an HTML document?

- use descriptive `alt` text
- use descriptive file names (avoid generic file names like 'image.jpg')
- use descriptions of the image - For complex images, graphs, or charts, consider providing a longer description of the image using the `longdesc` attribute or in the surrounding text. You can link to a separate page or include the description directly on the page
- When using images as links, ensure that the purpose of the link is clear by including text within the `<a>` element, and use alt text to describe the function of the link
- **Use Appropriate Image Elements**: Use the `<img>` element for images that are part of the content. Use other HTML elements like `<figure>` and `<figcaption>` for images with captions.
- From an accessibility viewpoint, captions and [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#alt) text have distinct roles. Captions benefit even people who can see the image, whereas [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#alt) text provides the same functionality as an absent image. Therefore, captions and `alt` text shouldn't just say the same thing, because they both appear when the image is gone. Try turning images off in your browser and see how it looks.

### Provide an example of when the `figure` element would be useful in an HTML document

- `<figure>` represents self-contained content, potentially with an optional caption, which is specified using the `<figcaption>` element. 
- The figure, its caption, and its contents are referenced as a single unit.
- A `figure` doesn't have to be an image. It is an independent unit of content that:
  - Expresses your meaning in a compact, easy-to-grasp way.
  - Could go in several places in the page's linear flow.
  - Provides essential information supporting the main text.

```js
<figure>
  <img src="/media/cc0-images/elephant-660-480.jpg" alt="Elephant at sunset" />
  <figcaption>An elephant at sunset</figcaption>
</figure>
```

### Describe the difference between a `gif` image and an `svg` image, pretend you are explaining to an elder in your community

- `GIF` images are like simple, moving pictures, while `SVG` images are like instructions for drawing, and they're super flexible and clear.
- A `GIF` image is like a *digital flipbook*. Imagine a series of pictures drawn on different pages, and when you flip through them quickly, you see a little animation. GIFs are like that - they can show simple animations, like a waving flag or a jumping character. They are good for fun and simple moving pictures. You've probably seen GIFs on the internet – they can be funny or cute, and they repeat over and over.
- `SVG` is a different type of image. It's more like a *recipe for drawing a picture*. Imagine you have a coloring book with lines, and you can paint it with any colors you like. SVG images are like that coloring book. They are made of instructions on how to draw shapes and lines. SVG images can be simple or very detailed, and they stay sharp no matter how big or small you make them. They're great for things like logos, icons, and even maps on websites.

### What image type would you use to display a screenshot on your website and why?

- Best choice: Lossless WebP or PNG;  JPEG if compression artifacts aren't a concern
- Alternatives: PNG or JPEG;  GIF for screenshots with low color counts
- use a *lossless format* for screenshots. This is particularly important if there's any text in your screenshot, as text easily becomes fuzzy and unclear under lossy compression.

## Learn CSS

*sources:* [Using Color in CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Colors/Applying_color). [Styling HTML Text Elements](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals), chatGPT

### Describe the difference between foreground and background colors of an HTML element, pretend you are talking to someone with no technical knowledge

- think of *foreground* as the ink or pencil you use to write on a piece of paper, and the *background* as the color of that paper. By changing these colors in HTML, you can control how the content on a webpage looks, making it more attractive and easier to read.
- the `color` property defines the *foreground* color of an HTML element's content and the `background-color` property defines the element's *background* color.

### Your friend asks you to give his colorless blog website a touch up. How would you use color to give his blog some character?

- choose a color palette - Start by selecting a color palette that reflects the theme and tone of the blog
- header and logo
- background color
  - Give the website a solid background color or texture that complements the color palette. White or light gray backgrounds are often used for readability, but you can use other subtle colors to create a unique atmosphere.
- Text and typography
  - Use contrasting colors for text and background to ensure readability. Dark text on a light background or vice versa is a common choice.
  - Consider using a consistent text color scheme for headings, body text, links, and other elements. This enhances readability and visual consistency.

### What should you consider when choosing fonts for an HTML document?

- when choosing fonts for an HTML document, prioritize readability and consider factors like font size, style, weight, web-safe options, accessibility, and brand alignment.
- Consistency, cross-browser compatibility, and responsive design are also important for a well-rounded font selection.

### What do `font-size`, `font-weight`, and `font-style` do to HTML text elements?

- `font-size` adjusts the size of text.
  - You can specify the font size using various units like pixels (`px`), ems (`em`), percentages (%), or keywords (e.g., `small`, `medium`, `large`).
- `font-weight` modifies the thickness or boldness of text.
  - You can set it to various numeric values (e.g., 100, 200, 300, ..., 900) or use keywords like `normal` and `bold`.
  - A value of `400` or `normal` typically represents the regular font weight, while `700` or `bold` makes the text bold.
- `font-style` changes the style to italic or oblique.
  - you can set it to keywords like `normal`, `italic`, or `oblique`.

```css
  p {
  font-size: 16px;
  font-weight: bold;
}

em {
  font-style: italic;
}
```

- You can use these properties to customize the appearance of text elements on your webpages, making them visually appealing and readable. These properties can be applied to various HTML elements such as headings (`<h1>`, `<h2>`, etc.), paragraphs (`<p>`), and more.

### Describe two ways you could add spacing around the characters displayed in an `h1` element

- The first method, `letter-spacing`, adjusts the space between characters, while the second method, `padding` or `margin,` adjusts the space around the entire element.
- `letter spacing`
  - To add spacing between the characters in the `h1` element, you can use the `letter-spacing` property.
- adjust the `padding `or `margin`.
  - Padding adds space inside the element, while margin adds space outside the element.

```css
h1 {
  letter-spacing: 2px; /* Increase the spacing between characters by 2 pixels */
}

h1 {
  padding: 10px; /* Add 10 pixels of padding around the h1 element */
}

h1 {
  margin: 10px; /* Add 10 pixels of margin around the h1 element */
}
```
