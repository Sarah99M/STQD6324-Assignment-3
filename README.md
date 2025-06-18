# STQD6324-Assignment3-P146399
# 🎬 MovieLens 100k Dataset Analysis Report

![Project cover](image.png)


## Project Introduction

This assignment uses the [MovieLens 100k dataset](https://grouplens.org/datasets/movielens/100k/) and Apache Zeppelin combined with PySpark and Spark SQL to analyze movie rating data, explore user preferences, rating distribution and other behavioral patterns, and answer a series of key questions related to recommendation systems.

---

## Using the Dataset

The data comes from MovieLens 100k, including the following three files (downloaded via wget):

- `u.user`: user information (user ID, age, gender, occupation, zip code)

- `u.data`: user rating record (user ID, movie ID, rating, timestamp)

- `u.item`: movie information (movie ID, movie name, type label, etc.)

The data is uploaded to the HDFS `/tmp/ml-100k/` directory and loaded through Spark.
---

## Analysis tools and platforms

- Apache Zeppelin
- PySpark (RDD and DataFrame)
- Spark SQL
- Cassandra
- HDFS distributed file system
- Shell + SQL + Markdown multi-stage collaboration

---

## Problems to be solved

This task aims to answer the following five core questions:

1. What is the average rating of each movie?

2. Which movies have the highest average rating? (Exclude movies with less than 15 ratings)

3. Which active users (ratings ≥ 50) prefer which types of movies?

4. Which users are younger than 20 years old?

5. Which users are between 30 and 40 years old and are scientists?

---

## Overview of analysis steps

1. Use the `%sh` command to download and upload raw data to HDFS;
2. Use `%pyspark` to read data as RDD and convert it to a structured DataFrame;
3. Use Spark SQL to register as a temporary view (TempView) to execute SQL queries;
4. Write SQL or PySpark query statements to complete the analysis of each problem;
5. Output intermediate results and generate an explanatory Markdown summary.

---

## summary

In this data analysis task, using the MovieLens 100k dataset, an analysis environment based on PySpark and Spark SQL was built through Apache Zeppelin to complete the exploration and analysis of user, movie and rating data.
I first used PySpark to upload the three files u.user, u.data and u.item to HDFS and read them into RDD format.

Then, these RDDs were converted into structured DataFrames and registered as SQL temporary views (Temp View) to facilitate subsequent SQL operations.

Then, in Zeppelin, %pyspark and %sql were combined to write query statements to solve the five problems in the job one by one.

In the processing process, SQL table connections (JOIN) and some aggregate functions (such as AVG, COUNT, GROUP BY, etc.) were mainly used to implement analysis logic, such as calculating the average score, finding high-scoring movies, analyzing user preferences, etc.

I first calculated the average rating of each movie, which laid the foundation for finding high-scoring movies later. Then I filtered and selected only movies with more than 15 ratings to avoid being interfered by "score-brushing" of unpopular movies, and the results were more realistic. Next, we analyzed those active users who rated more than 50 times, and inferred their favorite genres, such as dramas, comedies, etc., based on the types of movies they rated the most. In addition, we also found young user groups under the age of 20, and users between the ages of 30 and 40 who are scientists. These data can help us make more accurate user portraits and personalized recommendations.

---

## Author Info

- **Name:** MAO JINLIN
- **Course:** STQD6324 Data Management
- **Year:** 2025
- **Institution:** Univerdity Kebangsaan Malaysia
