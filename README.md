# Amazon_Vine_Analysis
Analyzing Amazon reviews written by members of the paid Amazon Vine program using AWS RDS and PySpark.

## Project Overview

BigMarket is a startup company that helps businesses optimize their marketing efforts based on advanced market analysis. <br>

One of the BigMarket clients, $ellBy, has requested some market analytics to support the release of a large catalog of products on a leading retail website. <br>
The client wants to know how the reviews of their products compare to the reviews of similar products sold by their competitors and is also interested <br>
in enrolling in a program that gives out free products to select reviewers, but they would like to know if it is worth the cost. <br>

The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products.<br>
Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review. <br>

There are tens of thousands of items on Amazon, each with hundreds of reviews. 
These types of records are considered Big Data that need robust storage and processing systems such as PySpark and Amazon Web Services. 
In order to analyze these reviews, they need to be translated from words into numbers using Natural Language Processing methods,
then fitted into a machine learning model for further breakdown to deduce value and impact. 

### Project Purpose


## Project Objectives
- Perform ETL on Amazon Product Reviews.
- Determine Bias of Vine Reviews.
- Provide a written report on the analysis.

## Sources
- Data Source: SQL_table_schema.sql, Amazon_Reviews_ETL.ipynb, amazon_reviews_us_Electronics_v1_00.tsv.gz
- Softwares and Frameworks: PostgreSQL (11.15-R1), pgAdmin4 (6.7), Spark (3.2.1).
- Libraries & Packages: PySpark, JAVA, PostgreSQL driver, MLlib. 
- Online Tools: AWS RDS (electronics-reviews), Google Colaboratory Notebooks

## Methods and Code:

Although Hadoop is one of the most popular open-source frameworks with a powerful storage and processing ecosystem. <br>
However, setting it up would be over the scale of operations for the BigMarket startup company. <br>
Hence, we will depend on PySpark, Amazon Web Services, and Google Colaboratory Notebooks, <br>
which allow faster, flexible, and accessible cloud-based solutions to analyze an extensive dataset such as Amazon reviews for electronic products. 




## Results


## Conclusions and Limitations