# Class 07 Reading Notes: Object-Oriented Programming, HTML Tables

## Domain Modeling

*sources*: [Domain Modeling](https://github.com/codefellows/domain_modeling#domain-modeling), chatGPT

### Explain why we need domain modeling.

Domain modeling is a crucial step in software development that involves creating a representation of the essential concepts and their relationships within a specific problem domain. It's the process of understanding, abstracting, and structuring the real-world problem that your software will address. The reference you provided from GitHub's "domain_modeling" repository is a valuable resource that provides insights into why domain modeling is essential in software development. Let's break down the reasons why we need domain modeling using the information from the reference:

1. **Shared Understanding:** Domain modeling helps create a shared understanding of the problem domain among all stakeholders, including developers, product managers, and users. By visually representing the key concepts and their relationships, it becomes easier for everyone to discuss and align on the problem space.
2. **Better Communication:** Through diagrams, sketches, and notations, domain modeling enables effective communication. It provides a common language for discussing the problem, which reduces miscommunication and ensures that everyone involved has a clear mental model of the domain.
3. **Problem Abstraction:** Domain modeling allows you to abstract the complex and often messy real-world problem into a simplified, structured form. This abstraction makes it easier to focus on the most relevant aspects and discard unnecessary details, leading to more efficient software design and development.
4. **Identifying Key Entities and Relationships:** It helps in identifying the essential entities (objects or concepts) within the domain and their relationships. This understanding is vital for designing software that accurately represents and manipulates these entities.
5. **Guidance for Development:** Domain models provide a blueprint for software development. They guide developers in creating code and data structures that align with the problem domain, making the code more intuitive, maintainable, and extensible.
6. **Reducing Ambiguity:** Domain modeling clarifies ambiguous or poorly defined aspects of the problem domain. It forces you to explicitly define terms and concepts, leaving no room for vague or contradictory interpretations.
7. **Improved Decision-Making:** A well-constructed domain model helps in making informed decisions during software development. It provides a visual representation of the domain's intricacies, aiding in choosing the right architectural patterns, data storage methods, and overall system design.
8. **Scalability and Flexibility:** When the domain is well-modeled, it becomes easier to adapt to changes and evolve the software as the problem domain evolves. This flexibility is essential for long-term software sustainability.
9. **Documentation:** Domain models serve as valuable documentation for your software project. They provide insights into the problem domain's structure and can help onboard new team members or facilitate discussions with external partners.

*sources:* [HTML Table Basics](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics), chatGPT

## HTML Tables

### Why should tables not be used for page layouts?

1. **Layout tables reduce accessibility for visually impaired users**: [screen readers](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#screen_readers), used by blind people, interpret the tags that exist in an HTML page and read out the contents to the user. Because tables are not the right tool for layout, and the markup is more complex than with CSS layout techniques, the screen readers' output will be confusing to their users.
2. **Tables produce tag soup**: As mentioned above, table layouts generally involve more complex markup structures than proper layout techniques. This can result in the code being harder to write, maintain, and debug.
3. **Tables are not automatically responsive**: When you use proper layout containers (such as [`<header>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header), [`<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section), [`<article>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article), or [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)), their width defaults to 100% of their parent element. Tables on the other hand are sized according to their content by default, so extra measures are needed to get table layout styling to effectively work across a variety of devices.

### List and describe 3 different semantic HTML elements used in an HTML `<table>`

- The `<caption>` element is used to provide a title or caption for the entire table. It should be placed immediately after the opening `<table>` tag. The caption summarizes the purpose or content of the table.
- `<thead>`, `<tbody>`, and `<tfoot>`:
  - Description: These elements are used to group the table's rows into different sections - the header, body, and footer of the table, respectively.
  - `<thead>`: Contains header information, typically column labels or titles.
  - `<tbody>`: Contains the main content of the table.
  - `<tfoot>`: Contains the footer information, such as summary rows or totals.

```html
<table>
    <thead>
        <tr>
            <th>Column 1</th>
            <th>Column 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data 1</td>
            <td>Data 2</td>
        </tr>
        <!-- More rows -->
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>Sum</td>
        </tr>
    </tfoot>
</table>

```

- `<th>`:
  - Description: The `<th>` element is used to define header cells within the table. Header cells are typically used in the table's header (inside `<thead>`), and they provide labels for columns or rows. They are semantically different from regular data cells, making screen readers and other assistive technologies identify them as headers.

*sources:* [Introducing Constructors](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics#introducing_constructors), chat GPT

## Object-Oriented Programming

### What is a constructor and what are some advantages to using it?

A constructor is just a function called using the [`new`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new) keyword. When you call a constructor, it will:

- create a new object
- bind `this` to the new object, so you can refer to `this` in your constructor code
- run the code in the constructor
- return the new object.

Some advantages:

- object creation
- code reusability
- **Initialization**: Constructors can take arguments and set initial values or properties for the objects they create. This simplifies the process of creating new objects with the correct initial state.
Constructors, by convention, start with a capital letter and are named for the type of object they create. So we could rewrite our example like this:

```js
function Person(name) {
  this.name = name;
  this.introduceSelf = function () {
    console.log(`Hi! I'm ${this.name}.`);
  };
}

```

to call Person() as a constructor, we use `new`:

```js
const salva = new Person("Salva");
salva.name;
salva.introduceSelf();
// "Hi! I'm Salva."

const frankie = new Person("Frankie");
frankie.name;
frankie.introduceSelf();
// "Hi! I'm Frankie."

```

### How does the term `this` differ when used in an object literal versus when used in a constructor?

The key distinction is in how `this` is bound or refers to different objects.

**Object Literal (Object Initializer)**: When you use `this` within an object literal, `this` refers to the object that encloses the object literal. In this context, `this` points to the object itself.
Example:
- In this example, `this` within the `greet` method refers to the `person` object, and it can access the `name` property of that object.
```js
const person = {
    name: 'Alice',
    greet: function() {
        console.log(`Hello, my name is ${this.name}`);
    }
};

person.greet(); // Output: Hello, my name is Alice

```

**Constructor Function**: When you use `this` within a constructor function, `this` refers to the newly created object instance that is being constructed using that constructor. It represents the instance being created and initialized.

- In this example, when you create a new `Person` object using the `new` keyword, `this` within the `Person` constructor refers to the specific instance being created (in this case, `person1`). Each instance has its own `name` property and a separate `greet` method.

```js
function Person(name) {
    this.name = name;
    this.greet = function() {
        console.log(`Hello, my name is ${this.name}`);
    };
}

const person1 = new Person('Bob');
person1.greet(); // Output: Hello, my name is Bob

```

*sources:* [Object Prototypes Using A Constructor](https://ui.dev/beginners-guide-to-javascript-prototype), chatGPT

### Explain prototypes and inheritance via an analogy from your previous work experience.

- **Prototype Chain**: In JavaScript, objects have a prototype chain. Much like our consulting firm hierarchy, where junior consultants learn from senior consultants and senior consultants learn from managing partners, JavaScript objects can inherit properties and methods from their prototypes.
- **Inheritance**: In the consulting firm, as junior consultants learn from senior consultants, JavaScript objects inherit properties and methods from their prototypes. This is similar to how a new object can inherit behaviors and attributes from its prototype, making code more efficient and reusable.
- **Adding Expertise**: In the consulting firm, as senior consultants develop expertise and knowledge, they can also share it with junior consultants. Similarly, in JavaScript, you can add new methods or properties to the prototype, and all objects that inherit from that prototype will have access to these new behaviors.
- **Customization**: Just as each consultant in the consulting firm has a unique set of skills, JavaScript objects can have their own properties and methods in addition to those they inherit from their prototypes. This allows for customization and specialization.

So, in this analogy, think of objects in JavaScript as consultants in a consulting firm, their prototypes as the hierarchy of expertise, and inheritance as the process of gaining and sharing knowledge and skills. This way, you can better understand how prototypes and inheritance work in JavaScript, making your code more efficient and maintainable.