# Data Modeling with Postgres

## Introduction
Sparkify, a new startup, wants to analyze the data they've been collecting on songs and users' activities on their new music streaming app. 
They want to understand what songs users like to listen to so that they can improve their app for users having better exeprience.

They'd like a data engineer to create a Postgres database to model song and log datasets (originaly stored in `JSON` format) with a star schema optimized for queries on song play analysis.

In this project, the data engineer needs to create the database and an ETL pipeline to help them on their analytic purposes.

## Prerequisites
- Python 3
- `pandas` and `psycopg2`
- A PosgreSQL database available on localhost

## Requirements
`pandas` should be upgraded first, at least to version 1.1.5:
```shell
pip3 install -U "pandas>=1.1.5"
```

## How to run
At the terminal:
1. Create the database with all of necessary tables:
```shell
python3 create_tables.py
```
2. After that, execute the ETL:
```shell
python3 etl.py
```

## Explanation of Files
- `create_tables.py` is used to create `sparkifydb` database with all tables needed.
- `etl.ipnyb` and `etl.py` perform ETL process: iterate over all JSON files, load the data into pandas DataFrame, then insert into the tables.
- `sql_queries.py` contains SQL queries that are used to create tables, insert data and drop tables. Also it contains a SQL that selects `song_id` and `artist_id` based on the conditions from the joined table of `songs` and `artists`.
- `test.ipynb` is used to perform sanity tests, such as primary keys, type mismatch warnings and not null warnings.

## Schema Design and ETL pipelines
The schema is a Star Schema, with 1 fact table and 4 dimension tables. 
Queries to create the database are stored in `create_tables.py` file, and queries to create tables, insert into tables, drop tables and select from tables are in the `sql_queries.py` file.