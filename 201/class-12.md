# Class-12 Reading Notes: Chart.js & Canvas

## Canvas

*sources:* [JavaScript Canvas](https://www.javascripttutorial.net/web-apis/javascript-canvas/), chatGPT

### What does the `<canvas>` allow a developer to achieve?

- Use the HTML5 canvas element for drawing 2D graphics.
- Use the `getContext('2d')` to get the 2D drawing context for drawing 2D graphics on canvas.
- Use the `fillStyle` and `StrokeStyle` properties to set the styles for the 2D drawing context.

The HTML `<canvas>` element in JavaScript provides a powerful and flexible way for developers to create and manipulate graphics and animations directly within a web page. It allows developers to achieve the following:

1. Drawing and rendering: Developers can use the `<canvas>` element to draw shapes, text, images, and complex graphics on a web page. This enables the creation of interactive data visualizations, charts, diagrams, games, and more.
2. Animation: JavaScript can be used to create animations by manipulating the content within the `<canvas>`. This is particularly useful for creating dynamic and engaging user interfaces, games, and other interactive web applications.
3. Interactivity: Developers can add interactivity to the graphics and animations drawn on the `<canvas>`. This includes handling user input, such as mouse clicks and keyboard events, to respond to user actions and create interactive experiences.
4. Custom graphics: With `<canvas>`, developers have full control over the pixel-level rendering, allowing them to create custom graphics and effects not easily achievable with other HTML elements. This makes it suitable for tasks like image processing and 2D rendering.
5. Real-time data visualization: Developers can use the `<canvas>` element to display real-time data in a visually appealing way. This is valuable for applications that need to show live updates, such as stock market charts, weather maps, or live data feeds.

### What is the importance of the closing `</canvas> tag?

the closing `</canvas>` tag is important for maintaining valid HTML structure, providing fallback content, ensuring accessibility, and avoiding rendering issues. It's a fundamental part of creating well-structured and reliable web pages.

### Explain what the `getContext()` method does

- The `getContext()` method is used in HTML5's `<canvas>` element to obtain a rendering context for drawing and manipulating graphics. It returns a JavaScript object representing the drawing context for the canvas, which allows you to interact with the canvas's 2D or 3D rendering capabilities.
- You can use this context object to draw shapes, text, images, and perform various operations on the canvas, such as filling, stroking, and transforming objects. It's a fundamental function for creating interactive graphics and animations in web applications.

### Chart.js

*sources:* [Chart.js Documentation](http://www.chartjs.org/docs/), chatGPT

### What is Chart.js and how it can be brought into your project?

Chart.js is a popular JavaScript library for creating interactive and visually appealing charts and graphs in web applications.

- **Download or include Chart.js:** You can obtain Chart.js in multiple ways. You can download the library from the [Chart.js website](https://www.chartjs.org/), or you can include it directly from a Content Delivery Network (CDN) in your HTML document. Here's an example of including it from a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
```

- **Create a Canvas Element:** In your HTML file, create a `<canvas>` element where you want to render your chart. Give it an `id` attribute so you can reference it in your JavaScript code.

```html
<canvas id="myChart"></canvas>
```

- **Write JavaScript Code:** In your JavaScript code, you can use the `<canvas>` element's `getContext()` method to get the 2D drawing context and then use Chart.js to create and configure your chart. Here's a simple example of creating a line chart:

```js
// Get the canvas element and its 2D context
var ctx = document.getElementById('myChart').getContext('2d');

// Create a new chart using Chart.js
var myChart = new Chart(ctx, {
    type: 'line', // Specify the chart type
    data: {
        labels: ['Label 1', 'Label 2', 'Label 3'], // X-axis labels
        datasets: [{
            label: 'My Dataset',
            data: [1, 2, 3], // Y-axis data
        }]
    }
});
```

- customize and style
- integrate with data

### List 3 different Chart types you can create using Chart.js

1. **Line Chart:**
    - A line chart is used to display data as a series of data points connected by straight lines. It is suitable for showing trends over time, data changes, and continuous data sets. Line charts are commonly used for time series data, stock prices, and scientific data.
2. **Bar Chart:**
    - A bar chart represents data with rectangular bars of varying lengths, where the length of each bar corresponds to the value of a data point. Bar charts are effective for comparing and contrasting data across categories. They are often used for displaying data like sales figures by product category, survey results, and ranking data.
3. **Pie Chart:**
    - A pie chart is a circular graph divided into slices, with each slice representing a portion of the whole data set. It is useful for showing the distribution or composition of a data set, highlighting the relative proportions of different categories. Pie charts are commonly used for visualizing market share, budget allocations, and survey responses with multiple-choice options.

Chart.js provides many other chart types, including scatter plots, radar charts, polar area charts, and more, making it a versatile library for creating a wide range of data visualizations.

*sources:* [Easily Create Stunning Animated Charts with Chart.js](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/), chatGPT

### What are some advantages to displaying data via a chart over a table?

1. Charts offer a visual and intuitive way to convey complex data, making it easier for users to grasp patterns, trends, and relationships at a glance, compared to dense tables of numbers.
2. They enhance data engagement and storytelling by providing a clear and memorable representation, allowing for effective communication of insights, which may not be as evident in tabular data.
3. Charts enable quick data interpretation, facilitating better decision-making, while tables can be overwhelming and require more effort to extract meaningful information, especially with large datasets.

### How could Chart.js aid your previously created applications visually?

In the Lab 11 vote count, it could display the votes in a bar chart as a percentage of views to visually represent which products had the highest proportion of votes
