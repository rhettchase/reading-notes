# Class-05 Reading Notes: Design web pages with CSS

## What is the purpose of CSS?

- **CSS** (**C**ascading **S**tyle **S**heets) enables website styling
- Language for specifying how documents are presented to users — how they are styled, laid out, etc.
- CSS can be used for:
  - Basic document text styling (e.g., color and size of headings and links)
  - Layout creation - (e.g., turning a single column of text with a main content area and a side bar)
  - Effects such as animation
  - and *more*!

## What are the three ways to insert CSS into your project?

### External CSS

- Allows you to change the look of an entire website by updating one file
- Each HTML page must include a reference to the external style sheet file inside the `<link>` element, inside the head section
- File is saved with a `.css` extension and shouldn't contain any HTML tags

### Internal CSS

- Defined within the `<style>` element, inside the `<head>` section of an HTML page:

```html
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
} 
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

### Inline CSS

- Used to apply a unique style for a single element
- To use `inline CSS` add the style attribute to the relevant element
- The style attribute can contain any CSS property

```html
<!DOCTYPE html>  
<html>  
<body>  
  
<h1 style="color:blue;text-align:center;">This is a heading</h1>  
<p style="color:red;">This is a paragraph.</p>  
  
</body>  
</html>
```

## Write an example of a CSS rule that would give all `<p>` elements red text

```html
<!DOCTYPE html>  
<html>
<body>

<h1>This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>
```
