# Movies-ETL
## Overiview
Raw data exists in multiple places and forms. In order to perform any kind of data analysis, this data needs to be cleaned and structured. The ETL Data pipeline process – Extract, Transform, and Load is a core concept in data engineering, ensuring that data is consistent, maintains its integrity, and nontheless strives for automatization of data wrangling. Without a consistent and robust data structure, it’s nearly impossible to perform any meaningful analysis.

The goal is to create one function that takes in the three files—Wikipedia data, Kaggle metadata, and the MovieLens rating data—and performs the ETL process by adding the data to a PostgreSQL database.

## Purpose
The Amazing Prime, a video streaming company, is sponsoring a hackathon, where participants try to predict which low budget movies being released will become popular. Participants need a clean data set in order to perform analyses for their algorithms. In order to provide an organized and clean dataset, this project utlizes the ETL process.

* Extracting data from two different sources:
        1. web scrape of Wikipedia website for all movies released since 1990
        2.  data from Kaggle website for rating data.
* Transforming the data using Jupyter Notebook, Python, Pandas and Python RegEx module.
* Loading the data using PostgreSQL and pgAdmin to create a final cleaned data set.

### Resources
Data Sources: 
-	Wikipedia web scrape [JSON file](Resources/wikipedia-movies.json)
-	Kaggle data from [Kaggle.com](https://www.kaggle.com/rounakbanik/the-movies-dataset) - two files: movies_metadata.csv and ratings.csv

Enviroment:
-	Python 3.7

Dependencies:
-	Jupyter Notebook [ETL_create_database.ipynb](ETL_create_database.ipynb) for entire list of dependencies

Software:
-	Jupyter Notebook
-	PostgreSQL and PgAdmin

### Analysis and Results
I'm essentially creating an automated pipeline that extracts, transform and loads all relevant data. This analysis consists of four parts, where each step is building up from beginning of extracting data and function testing, through transformation and cleaning process to its final step connect and load to the database. The entire process of ETL can be executed with a single call of the function extract_transform_load in the final step [ETL_create_database.ipynb](ETL_create_database.ipynb). The ETL process is broken down into four jupyter notebook files:

1. [ETL_function_test.ipynb](ETL_function_test.ipynb)

- Data is extracted from the website in JSON and CSV formats.
- Data is transformed into Pandas data frames.
- JSON file requires loading file first and then transforming into data frame.

2. [ETL_clean_wiki_movies.ipynb](ETL_clean_wiki_movies.ipynb)

- The function clean_movie combines all scattered data of alternative languages and combines them into one column named alt_titles.
- Its subfunction change_column_name organizes all the column names. 
- In the function extract_transform_load the transformation process of wiki movies, data includes Python list comprehensions, apply() and map() methods in combination with lambda functions, and regular expressions or RegEx.

3. [ETL_clean_kaggle_data.ipynb](ETL_clean_kaggle_data.ipynb)

The function created, extract_transform_load, gets new tasks for cleaning Kaggle data and includes:

- Changing datatypes, using methods pd.to_numeric, astype() and python comparison operators for Boolean types.
- Filling missing values and filtering unwanted columns.
- Merging data frames using pd_merge method.

4. [ETL_create_database.ipynb](ETL_create_database.ipynb)

Finally, the function connects to the database by sqlalchemy library and to_sql method. The entire ETL process can be executed with a single function extract_transform_load call.