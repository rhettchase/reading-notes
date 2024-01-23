# Class 12 Reading Notes: Pandas

sources: links below, chatGPT

## Reading

- [Pandas in 10](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)
- [Pandas - Getting Started](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)
- [Corey Schafer - Pandas Tutorials](https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS)
- [What is Pandas](https://www.youtube.com/watch?v=dcqPhpY7tWk&t=391s)
- [Master Pandas](https://towardsdatascience.com/be-a-more-efficient-data-scientist-today-master-pandas-with-this-guide-ea362d27386)

## Explain the purpose and basic functionality of the Pandas library. What are some common operations that can be performed on data using Pandas, and how do they contribute to data analysis and manipulation?

Pandas simplifies the process of data exploration, cleaning, transformation, and analysis, making it an essential tool for data professionals and analysts. It plays a crucial role in data preprocessing and preparation before applying machine learning algorithms and conducting in-depth data analysis.

1. **Data Structures**:
    - **DataFrame**: The central data structure in Pandas is the DataFrame, which is a two-dimensional, labeled data structure resembling a spreadsheet or SQL table. It allows you to store and manipulate data in rows and columns, where each column can have a different data type.
    - **Series**: Series is another fundamental data structure in Pandas, which is essentially a one-dimensional labeled array. Series can be thought of as individual columns of a DataFrame.
2. **Data Import and Export**:
    - Pandas supports reading data from various file formats, including CSV, Excel, SQL databases, JSON, and more. It also provides functionality for exporting data to these formats.
3. **Data Cleaning and Preparation**:
    - Data cleaning tasks like handling missing values, removing duplicates, and converting data types are made easier with Pandas.
    - You can also reshape data using operations like pivot, melt, and stack/unstack.
4. **Data Selection and Slicing**:
    - Pandas allows you to select, filter, and slice data easily. You can use boolean indexing, label-based indexing, and integer-based indexing to extract specific rows or columns.
5. **Data Aggregation and Grouping**:
    - You can perform aggregation operations like sum, mean, median, count, etc., on data using Pandas.
    - Grouping data by one or more columns and applying aggregation functions is a common operation for summarizing data.
6. **Data Visualization**:
    - Pandas integrates well with popular data visualization libraries like Matplotlib and Seaborn, making it easy to create informative plots and charts.
7. **Time Series Data**:
    - Pandas has extensive support for time series data, allowing you to work with date and time data efficiently.
8. **Merging and Joining Data**:
    - Combining data from multiple sources is straightforward in Pandas. You can merge DataFrames based on common columns or concatenate them vertically.
9. **Statistical Analysis**:
    - Pandas provides various statistical functions for basic statistical analysis, including descriptive statistics, correlation, and regression.
10. **Data Export**:
    - After analyzing and manipulating data, you can export the results back to different file formats or databases.

## What are the primary data structures in Pandas, and how do they differ in terms of use cases?

1. **DataFrame**:
    - Two-dimensional, labeled data structure resembling a table or spreadsheet.
    - Used for storing and manipulating structured data with rows and columns.
    - Ideal for working with tabular data, like datasets with multiple variables.
2. **Series**:
    - One-dimensional labeled array.
    - Useful for handling single columns or one-dimensional data.
    - Can be thought of as a basic building block of DataFrames.

DataFrames are suited for handling structured and tabular data, while Series are more appropriate for one-dimensional data or working with individual columns within a DataFrame. Both data structures are essential in Pandas and complement each other for data manipulation and analysis tasks.

## Describe the process of loading a dataset into a Pandas DataFrame. What are some common file formats that can be used, and which Pandas functions are utilized to read these formats?

Loading a dataset into a Pandas DataFrame involves these steps:

1. **Import Pandas**:
   - Import the Pandas library in your Python script or Jupyter Notebook.

2. **Select the File Format**:
   - Determine the format of the dataset you want to load.

3. **Use Pandas Functions**:
   - Choose the appropriate Pandas function based on the file format:
     - CSV: Use `pd.read_csv('filename.csv')`
     - Excel: Use `pd.read_excel('filename.xlsx')`
     - SQL Database: Use `pd.read_sql('SELECT * FROM table', connection)`
     - JSON: Use `pd.read_json('filename.json')`
     - Others: Pandas supports various formats like HDF5, Parquet, and more, each with its specific function.

4. **Optional Parameters**:
   - You can specify optional parameters like delimiter, header, encoding, and more to customize the import process.

5. **Assign to a DataFrame**:
   - Store the loaded data in a DataFrame variable for further manipulation and analysis.

Common file formats and Pandas functions for loading data:

- **CSV (Comma-Separated Values)**:
  - Function: `pd.read_csv('filename.csv')`

- **Excel**:
  - Function: `pd.read_excel('filename.xlsx')`

- **SQL Database**:
  - Function: `pd.read_sql('SELECT * FROM table', connection)`
  - Requires a database connection and a SQL query.

- **JSON (JavaScript Object Notation)**:
  - Function: `pd.read_json('filename.json')`

Pandas provides functions for reading various other formats, making it versatile for handling data from different sources. The choice of function depends on the specific file format and data source you are working with.
