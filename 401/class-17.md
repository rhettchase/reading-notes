# Class 17 Reading Notes: Web Scraping

sources: links below, chatGPT

## Reading

- [Scrape a Dynamic Website with Python](https://scrapingant.com/blog/scrape-dynamic-website-with-python)
- [What is Web Scraping?](https://en.wikipedia.org/wiki/Web_scraping)
- [How to scrape websites without getting blocked](https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/)

## Videos

- [Login and Scrape Data with Playwright and Python](https://www.youtube.com/watch?v=H2-5ecFwHHQ&t=60s)
- [Python Playwright Tutorial For Beginners](https://www.youtube.com/watch?v=yp1o9biMMWU)
- [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/)
- [Playwright XPath Selectors](https://www.programsbuzz.com/article/playwright-xpath-selectors)

## What are the key differences between scraping static and dynamic websites?

1. **Content Loading**:
    - **Static Websites**: All content is loaded on the initial page load. The HTML file delivered to your browser contains all the content you see on the page. This makes scraping straightforward because the data you want to scrape is already present in the HTML source code.
    - **Dynamic Websites**: Content can be loaded asynchronously after the initial page load, usually in response to user actions or other events. This means the HTML initially fetched might not contain all the data visible on the page. Dynamic websites often use AJAX (Asynchronous JavaScript and XML) or are Single-Page Applications (SPAs) where content is dynamically loaded.
2. **Scraping Tools**:
    - **Static Websites**: Simple HTTP requests and HTML parsing libraries like BeautifulSoup or lxml in Python are sufficient. These tools parse the static HTML content directly.
    - **Dynamic Websites**: Require tools that can execute JavaScript and handle asynchronous requests. This is because the data is often loaded via JavaScript after the initial HTML page has been loaded. Tools like Selenium, Puppeteer (and its Python port Pyppeteer), Playwright, or web scraping APIs that handle JavaScript rendering are necessary.
3. **Complexity and Overhead**:
    - **Static Websites**: Easier to scrape as the data is readily available in the HTML source. The scraping process is less resource-intensive and faster.
    - **Dynamic Websites**: More complex and resource-intensive. These require a browser or browser-like environment to execute JavaScript and render the page fully, which is more time-consuming and computationally expensive.
4. **Reliability and Accuracy**:
    - **Static Websites**: Scraping is generally more reliable and accurate as the data is static and consistent across page loads.
    - **Dynamic Websites**: The scraped data might vary due to JavaScript-driven changes, user interactions, and dynamic content loading. The timing of content rendering can also affect the scraping accuracy.
5. **Maintenance**:
    - **Static Websites**: Scrapers for static websites usually require less maintenance unless there are changes to the HTML structure.
    - **Dynamic Websites**: Scrapers may need more frequent updates to adapt to changes in the JavaScript logic, AJAX calls, or page structures.
    
## Explain at least three techniques or best practices that can be employed to avoid getting blocked while scraping websites

1. **Respect the Website's robots.txt File and Crawl Rate Limitations**:
    - The `robots.txt` file is a standard used by websites to communicate with web crawlers and other web robots. It tells the robot about which areas of the website should not be processed or scanned.
    - Before scraping, check the website’s `robots.txt` file (usually found at `http://example.com/robots.txt`) to see if the owner has specified any scraping rules or restrictions.
    - Even if scraping is allowed, it's important to respect the crawl-delay directive if present, which specifies how many seconds the crawler should wait between hits to the server.
2. **Rotate IP Addresses and User Agents**:
    - **IP Rotation**: Many websites track the IP addresses of their visitors. Making too many requests from the same IP address in a short period can lead to your IP being blocked. To avoid this, use a pool of different IP addresses and rotate them for your requests. This can be achieved using proxies, VPNs, or TOR.
        - **Types of Proxies**: You can use different types of proxies like Data Center Proxies, Residential Proxies, Free Proxies, or Shared Proxies. Each has its pros and cons in terms of cost, speed, and likelihood of being blocked.
    - **User-Agent Rotation**: Websites also track the user agent. A user agent is a string that the browser sends to the website, which indicates the type of device and browser being used. If all requests come from the same user agent, it can signal to the website that they're coming from a bot. Rotate between different user-agent strings to mimic different browsers and devices.
3. **Mimic Human Behavior and Avoid Detection Triggers**:
    - **Avoiding Patterns**: Do not follow the same crawling pattern in every session. Humans generally don't browse a website in predictable, repetitive patterns. Randomize the order in which you access pages.
    - **Rate Limiting and Delays**: Make requests at a reasonable rate. Implement delays between your requests to mimic human browsing speed. Avoid scraping too fast as it can overwhelm the website's server and is a clear sign of automated access.
    - **Random Clicks and Mouse Movements**: If using a headless browser like Puppeteer, Selenium, or Playwright, incorporate random mouse movements and clicks to emulate human interaction.
    - **Captcha Solving**: Some websites use captchas to block bots. If you encounter captchas, consider using captcha solving services, though this can be a legal and ethical grey area.
    
##  What is Playwright, and how does it assist in web scraping tasks? Provide an example of a use case where Playwright would be particularly beneficial.

**Playwright** is an open-source automation library developed by Microsoft, which provides a high-level API to control headless browsers.

1. **Handling Dynamic Content**: Playwright can render JavaScript-heavy pages, making it suitable for scraping modern web applications where content is dynamically loaded.
    
2. **Browser Automation**: Playwright automates browser actions like clicking buttons, filling out forms, navigating pages, and capturing screenshots, which is useful for interacting with web pages programmatically.
    
3. **Multi-Browser Support**: With the ability to work with different browsers, Playwright allows scraping tasks to be tested and executed in environments similar to those used by real users.
    
4. **Headless Browsing**: Playwright can run browsers in headless mode (without a GUI), which is faster and uses fewer resources, ideal for server environments and automated scraping tasks.
    
5. **Network Interception**: It can intercept and modify network requests and responses, allowing for testing of different scenarios or bypassing certain client-side restrictions.
    
6. **Consistency Across Browsers**: Playwright ensures consistent results across different browsers, reducing the hassle of dealing with browser-specific issues.
    
7. **Cross-Platform**: Being cross-platform, it allows the scraping scripts to be run on Windows, Linux, and macOS.

Example use case: A real estate data aggregator wants to collect detailed information on property listings from various real estate websites. These websites often have complex, JavaScript-rich interfaces with dynamic loading of content, interactive maps, and pagination.
- dynamic content handling
- automated form submission
- data extraction from interactive elements
- handling login and session management
- capturing screenshots
    
## Describe the purpose of using Xpath in web scraping, and provide an example of an Xpath expression to select a specific HTML element from a webpage.

XPath, which stands for XML Path Language, is a query language that is used for selecting nodes from an XML (or HTML, which is an application of XML) document. In the context of web scraping, XPath serves several crucial purposes:

1. **Precise Selection of Elements**: XPath allows for the precise targeting of elements within the complex structure of an HTML document. It provides a way to navigate the hierarchical structure of an HTML DOM (Document Object Model).
    
2. **Flexibility in Element Location**: With XPath, you can locate elements based not just on their tags, but also attributes, text content, and hierarchical position. This flexibility is particularly useful when dealing with dynamically generated content where element IDs or classes might change.
    
3. **Handling Dynamic and Complex Web Pages**: XPath expressions can be used to handle web pages with dynamic content and complex structures, where simpler methods of element selection (like CSS selectors) might fall short.
    
4. **Ability to Traverse the DOM**: XPath provides functions to move up, down, and across the DOM, making it easy to select elements based on their relation to other elements (e.g., selecting a button that is next to a certain label).
    
5. **Use in Various Web Scraping Tools**: Many web scraping tools and libraries, such as Scrapy, Selenium, and lxml in Python, support XPath expressions, making it a widely applicable skill for scraping different types of web data.

**Scenario**: Suppose you want to select the title of a blog post on a webpage. The HTML structure of the webpage is as follows:

```HTML
<html>
  <head>
    <title>Example Blog</title>
  </head>
  <body>
    <div id="content">
      <h1 class="post-title">Title of the Blog Post</h1>
      <!-- More content here -->
    </div>
  </body>
</html>

```

**XPath Expression**: To select the text of the blog post's title, you can use the following XPath expression:
```xpath
//h1[@class='post-title']/text()
```