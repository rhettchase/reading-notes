# Class 14 Reading Notes: Data Visualization

sources: Links below, chat GPT

- [Matplotlib Tutorial](https://www.labri.fr/perso/nrougier/teaching/matplotlib/)
- [Seaborn Tutorial](https://seaborn.pydata.org/tutorial.html)
- [Bokeh Tutorial](https://mybinder.org/v2/gh/bokeh/bokeh-notebooks/master?filepath=tutorial%2F00%20-%20Introduction%20and%20Setup.ipynb)
- [Seaborn Cheat Sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_Seaborn_Cheat_Sheet.pdf)

## What are the key differences between Matplotlib, Seaborn, and Bokeh libraries in terms of their features and use cases? Provide an example of a specific visualization that is more suitable for each library.

**Matplotlib**:

- **Base Library**: Matplotlib is a foundational library for data visualization in Python. It provides a wide range of customization options for creating static, publication-quality plots and charts.
- **Use Cases**: Matplotlib is versatile and can be used for a variety of plots and charts, including line plots, scatter plots, bar charts, histograms, and more. It is suitable for creating standard, static visualizations.
- **Example**: A line plot showing the trend of stock prices over time would be a suitable example for Matplotlib.

**Seaborn**:

- **Built on Matplotlib**: Seaborn is built on top of Matplotlib and provides a higher-level interface for creating aesthetically pleasing statistical visualizations.
- **Use Cases**: Seaborn is particularly useful for creating statistical plots, such as distribution plots, heatmaps, and pair plots. It simplifies the creation of complex visualizations with concise code.
- **Example**: A histogram with a kernel density estimate (KDE) overlayed would be a suitable example for Seaborn.

**Bokeh**:

- **Interactive and Web-Based**: Bokeh is designed for creating interactive, web-based visualizations. It allows for building interactive dashboards, tools, and applications that can be deployed on the web.
- **Use Cases**: Bokeh is ideal for creating interactive data visualizations, such as interactive line charts, scatter plots, and geographic maps. It provides widgets for interactivity and can handle large datasets.
- **Example**: An interactive scatter plot with tooltips and zooming capabilities would be a suitable example for Bokeh.
    
## In the Seaborn library, what are the main functions to create relational, categorical, and distribution plots? Briefly explain the purpose of each type of plot and provide an example use case.

**Relational Plots**:

- **Function**: `sns.relplot()`
- **Purpose**: Relational plots are used to visualize the relationship between two or more variables. They are often used for exploring how variables interact with each other and can show patterns and trends in the data.
- **Example Use Case**: Scatter plots are a common type of relational plot. You can use `sns.relplot()` to create scatter plots, line plots, or other types of plots to explore relationships between variables.

**Categorical Plots**:

- **Functions**: Various functions like `sns.catplot()`, `sns.barplot()`, `sns.boxplot()`, etc.
- **Purpose**: Categorical plots are used to visualize the distribution of data within categorical variables. They help in understanding the distribution of data across different categories or groups.
- **Example Use Case**: A common use case is creating bar plots to compare the average values of a numerical variable across different categories.

**Distribution Plots**:

- **Functions**: Various functions like `sns.histplot()`, `sns.kdeplot()`, `sns.distplot()`, etc.
- **Purpose**: Distribution plots are used to visualize the distribution of a single variable. They help in understanding the shape, central tendency, and spread of data.
- **Example Use Case**: Creating a histogram to visualize the distribution of a numerical variable is a common use case for distribution plots.
    
## Discuss the role of the Seaborn Cheat Sheet in a Python developer’s workflow. What are some key sections or elements featured in the cheat sheet that can help a developer quickly reference Seaborn functionalities?

It simplifies the process of referencing Seaborn's functionalities, making it easier to create a wide range of data visualizations and customize them to suit specific needs. It's particularly useful for both beginners and experienced developers looking to streamline their data visualization workflow with Seaborn

- Importing Seaborn
- Loading Example Datasets
- Basic Plot Types
- Customization options
- Advanced Plot Types
- Statistical Estimations
- Faceting - create multiple subplots based on categories in the data.