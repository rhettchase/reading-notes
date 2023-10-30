# Class-06 Reading Notes: Problem Domain, Objects, and the DOM

## JavaScript Object Basics

*sources:* [JavaScript Object Basics](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics), chatGPT

### How would you describe an object to a non-technical friend you grew up with?

Hey, you know how in real life, we often have things that have different properties and characteristics? Like a car has a color, a brand, and a model, and a person has a name, age, and a job. Well, in the world of JavaScript, we use something called an 'object' to represent these things.

An object in JavaScript is like a container that can hold information about something. Think of it as a virtual box where you can put labels on different parts of the box to describe what's inside. These labels are like the 'properties' of the object. For example, if we have an object that represents a car, we can have properties like 'color,' 'brand,' and 'model,' and we can fill in values for each property, just like you'd describe a real car.

### What are some advantages to creating object literals?

- An object like this is referred to as an **object literal** — we've literally written out the object contents as we've come to create it
- common to create an object using an object literal when you want to transfer a series of structured, related data items in some manner, for example sending a request to the server to be put into a database. Sending a single object is much more efficient than sending several items individually, and it is easier to work with than an array, when you want to identify individual items by name.

```js
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio() {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf() {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};
```

### How do objects differ from arrays?

- objects are suitable for representing structured data with named properties, while arrays are ideal for ordered lists of values where you need to perform operations on the elements. Both data structures have their unique use cases in JavaScript.

1. **Data Structure:**
    - **Objects:** Objects are a collection of key-value pairs, where keys (property names) are unique strings or symbols, and values can be of any data type. Objects are typically used to represent and manipulate data with named properties.
    - **Arrays:** Arrays are ordered lists of values, typically indexed by numbers. They are used to store and access multiple values, often of the same data type.
2. **Key Access:**
    - **Objects:** You access values in objects using the property names (keys).
    - **Arrays:** You access values in arrays using numeric indices (0-based).
3. **Order:**
    - **Objects:** Property order is not guaranteed, and properties are not necessarily stored in a specific sequence.
    - **Arrays:** Arrays maintain the order of elements, and you can rely on the order of elements based on their index.
4. **Usage:**
    - **Objects:** Objects are used when you have named properties and want to represent structured data with meaningful keys. For example, representing a person's information with properties like `name`, `age`, and `address`.
    - **Arrays:** Arrays are used when you have a list of values and need to perform operations like iteration, sorting, filtering, or mapping.
5. **Methods:**
    - **Objects:** Objects can have methods, which are functions associated with a property. Methods are useful for performing actions related to the object.
    - **Arrays:** Arrays have built-in methods like `push`, `pop`, `shift`, `unshift`, `forEach`, and others for performing common operations on lists of data.
6. **Length:**
    - **Objects:** Objects do not have a `length` property, as they don't have a specific number of properties.
    - **Arrays:** Arrays have a `length` property that represents the number of elements in the array.

```js
// Object
const person = {
  name: "John",
  age: 30,
  address: "123 Main St"
};

// Array
const fruits = ["apple", "banana", "cherry"];

```

### Give an example for when you would need to use bracket notation to access an object’s property instead of dot notation

- Dot notation is generally preferred over bracket notation because it is more succinct and easier to read. However there are some cases where you have to use square brackets. 
  - For example, if an object property name is held in a variable, then you can't use dot notation to access the value, but you can access the value using bracket notation.
- In the example below, the `logProperty()` function can use `person[propertyName]` to retrieve the value of the property named in `propertyName`.

```js
const person = {
  name: ["Bob", "Smith"],
  age: 32,
};

function logProperty(propertyName) {
  console.log(person[propertyName]);
}

logProperty("name");
// ["Bob", "Smith"]
logProperty("age");
// 32

```

### Evaluate the code below. What does the term `this` refer to and what is the advantage to using `this`?

- The `this` keyword refers to the current object the code is being written inside — so in this case `this` is equivalent to `dog` object
- The `humanAge` method calculates the human age of the dog by multiplying its age by 7 and then logs a message using the `this` keyword to access properties of the `dog` object. 
- The advantage of using `this` in this context is that it allows you to access and reference the properties of the current object within a method. In this case, it makes the code more flexible and reusable. If you were to create multiple dog objects, each with its own `name` and `age`, you could call the `humanAge` method on each of them, and it would correctly reference the properties of the specific object it's called on.

```js
const dog = {
  name: 'Spot',
  age: 2,
  color: 'white with black spots',
  humanAge: function (){
    console.log(`${this.name} is ${this.age*7} in human years`);
  }
}
```

## DOM

*sources:* [Introduction To The DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction), chatGPT

### What is the DOM?

- In simple terms, the DOM, or Document Object Model, is like a tree-like structure that represents a web page in your web browser. It allows web developers to interact with and manipulate the content and elements on a webpage using programming languages like JavaScript.
- Imagine a webpage as a book, and the DOM as an interactive table of contents for that book. You can use the table of contents (the DOM) to find and change specific pages or sections of the book (webpage). It's a way for your code to understand and work with the elements, text, images, and other content on a web page, making it possible to create dynamic and interactive websites.
- The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects; that way, programming languages can interact with the page

### Briefly describe the relationship between the DOM and JavaScript

- The Document Object Model (DOM) and JavaScript have a close and interactive relationship in web development. JavaScript is often used to manipulate and interact with the DOM.
- The DOM is not a programming language, but without it, the JavaScript language wouldn't have any model or notion of web pages, HTML documents, SVG documents, and their component parts.
- The DOM is not part of the JavaScript language, but is instead a Web API used to build websites.

1. **DOM as a Representation:** The DOM represents the structure and content of a web page in a hierarchical tree-like structure, where each element (like paragraphs, headings, and images) is a node in the tree.
2. **JavaScript's Role:** JavaScript is a programming language that web developers use to add interactivity and functionality to web pages. It can access, modify, and manipulate the DOM.
3. **Interactivity:** JavaScript allows you to respond to user actions (e.g., clicks, input) and change the content, structure, and style of a web page in real-time. You can use JavaScript to locate and modify specific DOM elements, update text and attributes, add or remove elements, and more.
4. **Dynamic Web Pages:** By combining JavaScript with the DOM, web developers can create dynamic and responsive websites, such as interactive forms, dynamic content updates, animations, and more.

In essence, JavaScript and the DOM work together to make web pages come to life, enabling a rich and interactive user experience on the web.