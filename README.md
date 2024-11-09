[![CI](https://github.com/nogibjj/mini_project_PySpark_yl/actions/workflows/cicd.yml/badge.svg)](https://github.com/nogibjj/mini_project_PySpark_yl/actions/workflows/cicd.yml)


Week 10: PySpark Data Processing

### Overview

The project involves utilizing PySpark for data processing on a large dataset, include at least one Spark SQL query and one data transformation, demonstrating data processing functionality and the use of Spark SQL and transformations. 

The workflow includes running a Makefile to perform tasks such as installation (`make install`), testing (`make test`), code formatting (`make format`) with Python Black, linting (`make lint`) with Ruff, and an all-inclusive task (`make all`). This automation streamlines the data analysis process and enhances code quality.

### Preperation

I used the nogibjj/python-ruff-template template for this project.

I used the Comic Characters Dataset.

### Dataset Description

The Comic Characters Dataset comes from Marvel Wikia and DC Wikia. Characters were scraped on August 24, 2014. Appearance counts were scraped on September 2, 2014. The month and year of the first issue each character appeared in was pulled on October 6, 2014.

The data is split into two files, for DC and Marvel, respectively: `dc-wikia-data.csv` and `marvel-wikia-data.csv`. In this excercise, I use DC characters data, `dc-wikia-data.csv`.

[Resources](https://github.com/fivethirtyeight/data/tree/master/comic-characters)

### Description

1. Open codespaces and wait for environment to be installed

2. pip install pyspark

3. `mylib.lib.py`: This script is a comprehensive PySpark application encompassing data extraction, transformation, and loading (ETL), along with logging and analysis capabilities such as performing Spark SQL query and data transformation.

```
1. Logging Function: log_output is a utility function that appends a description of operations performed, along with their outputs and queries if present, to a markdown file named "pyspark_output.md".

2. Spark Session Management: Functions start_spark and end_spark are defined for initiating and stopping a Spark session, respectively.

3. Data Extraction: The extract function is responsible for downloading the comic character dataset from a given URL and saving it to a specified local directory and path.

4. Data Loading and Schema Definition: load_data loads the CSV data into a PySpark DataFrame with a predefined schema, then logs the output of the first 10 rows.

5. Spark SQL Querying: The query function takes a DataFrame and a SQL query string, registers the DataFrame as a temporary view to query against, executes the Spark SQL query, logs the output, and shows the results.

6. Data Description: describe produces summary statistics of the DataFrame, logs the output in markdown format, and shows the result.

7. Data Transformation: example_transform applies a transformation to the DataFrame by categorizing characters into "Hero", "Villain", or "Other" based on their alignment, logs the output of the first 10 transformed rows, and shows the result.
```

4. `main.py`: serves as the entry point for the Python application, organizing the flow of operations using functions imported from `mylib.lib`. 

```
1. Data Extraction: The extract function is called without arguments, triggering the download of the comic characters dataset from a predefined URL to a specified local file path.

2. Spark Session Initialization: The start_spark function is invoked with the application name "COMIC_CHARACTERS" to begin a new Spark session.

3. Data Loading: With the Spark session started, the load_data function loads the data from the CSV file into a Spark DataFrame, applying a predefined schema.

4. Data Description: The describe function is called to generate descriptive statistics of the DataFrame's columns, which are logged and displayed.

5. Data Querying: The query function is executed with a specific Spark SQL command to select and count the number of characters per year from the DataFrame, grouping the results by year and ordering them chronologically.

6. Data Transformation: An example transformation is applied to the DataFrame using the example_transform function, which categorizes characters into "Hero", "Villain", or "Other" based on their alignment.

7. Spark Session Termination: Finally, the end_spark function is called to cleanly stop the Spark session.
```

5. `test_main.py` : contains unit tests for the Python application, which utilizes the PySpark framework. These tests are designed to validate the correctness of the application's main functionalities. 

```
1. Spark Session Fixture: A pytest fixture named spark is defined to set up and tear down a Spark session. The scope is set to "module", meaning the Spark session will be created and reused for all tests in this module and closed after all tests are completed.

2. Test Data Extraction: test_extract checks that the extract function successfully downloads the file and saves it to the specified path on the local filesystem.

3. Test Data Loading: test_load_data ensures that the load_data function correctly loads the data into a DataFrame within the Spark session.

4. Test Data Description: test_describe tests that the describe function is able to generate descriptive statistics of the DataFrame. The result is not directly checked for content, but the absence of an error suggests the describe function can be called without issues.

5. Test Data Querying: test_query verifies that the query function can perform a SQL query on the DataFrame, specifically selecting records from the year 1939. It doesn't check the query's results but ensures that the function can be executed.

6. Test Data Transformation: test_example_transform confirms that the example_transform function is able to apply the transformation to categorize characters and does not result in an error.
```

6. Makefile

Install requirement: `make install`
Format code: `make format`
Lint code: `make lint`
Test code: `make test`

### Output

[Pyspark Output Data/Summary Markdown File](./pyspark_output.md)

### References
https://github.com/nogibjj/python-ruff-template
https://github.com/fivethirtyeight/data/tree/master/daily-show-guests
