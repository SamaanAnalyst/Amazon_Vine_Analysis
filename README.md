# Amazon_Vine_Analysis
We are analyzing Amazon reviews of electronic products written by members of the paid Amazon Vine program and independent customers using AWS RDS and PySpark.

## Project Overview

BigMarket is a startup company that helps businesses optimize their marketing efforts based on advanced market analysis. <br>

One of the BigMarket clients, $ellBy company, has requested some market analytics to support the release of a large catalog of products on a leading retail website. <br>
The client wants to know how the reviews of their products compare to the reviews of similar products sold by their competitors and is also interested 
in enrolling in a program that gives out free products to select reviewers. However, they would like to know if it is worth the cost. <br>

The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products.<br>
Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review. <br>

There are thousands of items on Amazon, each with hundreds of reviews. 
These types of records are considered Big Data and would require robust storage and processing systems such as PySpark and Amazon Web Services to handle them. 

### Project Purpose

For this project, we will focus on an Amazon reviews dataset about electronic products, out of 50 available datasets containing reviews about a range of products from clothing apparel to wireless products. <br>
We will use PySpark to perform the Extract, Transform, and Load (ETL) process to extract the dataset of interest from an Amazone Simple Storage Service (S3) bucket, <br>
transform the data, connect to an Amazon Web Services (AWS) Relational Database Service (RDS) instance, and load the transformed data into a PostgreSQL database through pgAdmin. <br>
Next, we will use PySpark to determine if there is any bias towards favorable reviews from Vine members in our electronics reviews dataset and provide recommendations regarding the 
value and impact of incentivized reviews on the market. 

## Project Objectives

1. Perform ETL on Amazon Product Reviews.
2. Determine Bias of Vine Reviews.

## Sources

- Data Source: SQL_table_schema.sql, Amazon_Reviews_ETL.ipynb, amazon_reviews_us_Electronics_v1_00.tsv.gz, magzzie-electronics-reviews AWS RDS DataBase, Amazon_Vine_Analysis repository.
- Software and Frameworks: PostgreSQL (11.15-R1), pgAdmin4 (6.7), Spark (3.2.1).
- Libraries & Packages: PySpark, JAVA, PostgreSQL driver, MLlib. 
- Online Tools: AWS RDS, Google Colaboratory Notebooks, GitHub.

## Methods and Code:

Although Hadoop is one of the most popular open-source frameworks with a powerful storage and processing ecosystem, setting it up would be over the scale of operations for the BigMarket startup company. <br>
Therefore, we will use PySpark, Amazon Web Services, and Google Colaboratory Notebooks, which allow faster, more flexible, and easily accessible cloud-based solutions <br>
to analyze an extensive dataset such as Amazon reviews for electronic products. <br>

1. Perform ETL on Amazon electronic products reviews: <br>
- We start by creating an AWS RDS database with public access and then establishing a new server in pgAdmin that is connected to the AWS RDS.
- Next, we initiate an electronics-reviews database and create four tables to hold the data: customers_table, products_table, review_id_table, vine_table.
- After that, we start a new Google CoLab Notebook named Amazon_Reviews_ETL, install the necessary Spark libraries, and set up the connection to the database via PostgreSQL driver. 
- Now, we begin the extraction of electronics reviews from the Amazon bucket URL into a DataFrame, then manipulate data types and create four separate DataFrames <br>
that match the tables' schema in the electronics-reviews database. 
- Finally, we connect to the AWS RDS instance, load the DataFrames into their corresponding tables, and check that the tables have been successfully populated in pgAdmin.

2. Determine the bias of Vine reviews:<br>
Using PySpark: 
- We start by filtering the electronics reviews data and creating a new DataFrame to retrieve all the rows where the 'total_votes' count is equal to or greater than 20 <br>
to pick reviews that are more likely helpful and avoid division by zero errors later on. <br>
- Then, we filter the new votes_counts_df DataFrame to create a new DataFrame to retrieve all the rows where the number of 'helpful_votes' divided by 'total-votes' is equal to or greater than 50%.
- Next, we filter the DataFrame created in step 2, helpful_votes_df, and create a new DataFrame named paid_review_df that retrieves all the rows where a review was written as part of the Vine program (paid), 'vine == 'Y''.
- Additionally, we filter the DataFrame created in step 2 and create a new DataFrame named unpaid_review_df that retrieves all the rows where the review was not part of the Vine program (unpaid), 'vine == 'N''.
- Finally, we calculate the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of reviews (paid vs. unpaid).


## Results

1. The Extract, Transform, and Load process -performed on the Amazon electronics reviews dataset has resulted in four populated tables in the RDS database:
- Customers table: <br> 

     <img src="https://github.com/Magzzie/Amazon_Vine_Analysis/blob/branch1/Images/customers_table.png" width=25% height=25% align="center">

- Products table: <br>

     <img src="https://github.com/Magzzie/Amazon_Vine_Analysis/blob/branch1/Images/products_table.png" width=55% height=55% align="center">

- Review ID table: <br>

     <img src="https://github.com/Magzzie/Amazon_Vine_Analysis/blob/branch1/Images/review_id_table.png" width=45% height=45% align="center">

- Vine table: <br>

     <img src="https://github.com/Magzzie/Amazon_Vine_Analysis/blob/branch1/Images/vine_table.png" width=45% height=45% align="center">

2. We compared the Amazon reviews for electronics products that were submitted by independent customers who were not compensated by the Amazon Vine program for their reviews, <br>
with the reviews of the Vine program members, and we found that: <br> 
- There were 3,093,869 reviews on the Amazon website about electronics products. 
- Out of 3+ million reviews, 58,554 got more than 20 votes each from other amazon customers, and of these, 50,753 reviews had 50% or more helpfulness votes each. 
- The total number of paid electronics reviews through the Vine program was 1,080.
- The total number of unpaid electronics reviews on Amazon was 49,673.
- There were 454 paid reviews with five-star ratings, constituting 42.04% of the Vine reviews.
- There were 23,043 unpaid reviews with five star-rating, constituting 46.39% of the independent reviews on Amazon.


## Conclusions and Limitations

Based on the results of the Amazon electronics reviews, we can conclude that:
- In general, independent and unpaid product reviews on Amazon are more frequently favorable than incentivized reviews. 
- Sponsoring reviews is a top-rated marketing strategy to advertise products; however, in the specific case of electronics, the paid reviews were more reserved in their evaluation than their unpaid counterparts with a 5-star distribution of 42.04% and 46.39%, respectively.
- Based on this analysis, we do not recommend investing in the Vine program for incentivized reviewing services as it did not prove more valuable than random feedback. 
- There are limitations to this dataset regarding reviews' text availability and sales revenue. Thus, further analysis is recommended to investigate the impact of reviews on sales and possibly building a machine learning model to better understand and predict the syntax of positive language used to influence the sales of a product. 


---







