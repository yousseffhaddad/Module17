## Amazon_Vine_Analysis

Module 16:  Big Data

Completed by Angela Kumar

### Purpose

Enter the world of Big Data as you perform ETL (Extract, Transform, Load) on a dataset from Amazon.

### Overview

We'll start by reviewing Hadoop and its ecosystem.

Within this big data and Hadoop context, we'll cover MapReduce and how it has improved the process for handling big data. We'll then move on to PySpark, which has become the leading technology for handling big data.

After diving into some of the technologies used with big data, we'll look at natural language processing (NLP) in relation to big data.

We'll close with an introduction to cloud services. Cloud services let us store large amounts of data at remote locations rather than locally, on top of many other services. This allows for more scalability and performance. We'll use the most popular cloud service available: Amazon Web Services (AWS).

### Resources

Data: challenge_schema.sql; Amazon_Reviews_ETL_Starter_code.ipynb converted to Amazon_Reviews_ETL.ipynb

Amazon Dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt

Technologies: Google Colab;Pyspark; AWS RDS, PgAdmin4: Postgres SQL; VSCode;

### Background

Since your work with Jennifer on the SellBy project was so successful, you’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. 
The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. 
Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, you’ll have access to approximately 50 datasets. Each one contains reviews of a specific product, from clothing apparel to wireless products. 
You’ll need to pick one of these datasets and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. 
Next, you’ll use PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members in your dataset. Then, you’ll write a summary of the analysis for Jennifer to submit to the SellBy stakeholders.

### Deliverables

* Deliverable 1: Perform ETL on Amazon Product Reviews

Using your knowledge of the cloud ETL process, you’ll create an AWS RDS database with tables in pgAdmin, pick a dataset from the Amazon Review datasets (Links to an external site.), and extract the dataset into a DataFrame. 
You'll transform the DataFrame into four separate DataFrames that match the table schema in pgAdmin. Then, you'll upload the transformed data into the appropriate tables and run queries in pgAdmin to confirm that the data has been uploaded.

An Amazon Review dataset is extracted as a DataFrame (selected the furniture dataset)
https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Furniture_v1_00.tsv.gz

<img width="410" alt="DF Furniture" src="https://user-images.githubusercontent.com/85860367/141735908-88579f68-5a4c-4472-b778-63bfb3fc6d8f.PNG">

The extracted dataset is transformed into four DataFrames with the correct columns 

**The customers_table DataFrame**

<img width="410" alt="Customer count df" src="https://user-images.githubusercontent.com/85860367/141736418-d8fb3136-a019-4cee-b703-164278470050.PNG">

**The products_table DataFrame**

<img width="410" alt="Products df" src="https://user-images.githubusercontent.com/85860367/141736865-fa0a4eed-53fe-449e-a2aa-e6c99af72bd8.PNG">

**The review_id_table DataFrame**

<img width="410" alt="review id df" src="https://user-images.githubusercontent.com/85860367/141737173-da110bcf-0b74-4bb8-aa05-20cbc24bcab9.PNG">

**The vine_table DataFrame**

<img width="410" alt="vine df" src="https://user-images.githubusercontent.com/85860367/141737382-41ffda4b-772e-4465-bcf9-628fecd3ef43.PNG">


All four DataFrames are loaded into their respective tables in pgAdmin 

**The customers_table**

<img width="410" alt="AVDB customers_table screenshot" src="https://user-images.githubusercontent.com/85860367/141739209-e7706fa9-75d0-4797-8ab8-8ed96125bfc4.PNG">

**The products_table**

<img width="410" alt="AVDB products_table screenshot" src="https://user-images.githubusercontent.com/85860367/141739431-0414dfdf-ad82-4329-958c-b9b6608b1e1c.PNG">

**The review_id_table**

<img width="410" alt="AVDB review_id_table screenshot" src="https://user-images.githubusercontent.com/85860367/141739835-1c1a5b60-3ba7-4034-97b5-4ea2cbf80cd1.PNG">

**The vine_table**

<img width="410" alt="AVDB vine_table screenshot" src="https://user-images.githubusercontent.com/85860367/141740075-8dcb2bbb-7089-4650-8d4c-c42083d8d3a8.PNG">

**Query to call each table:**

<img width="410" alt="Query snapshot" src="https://user-images.githubusercontent.com/85860367/141741349-79ce72e0-306f-47e1-b155-ffc769b20177.PNG">


* Deliverable 2: Determine Bias of Vine Reviews

Using either PySpark, Pandas, or SQL, follow the instructions below to complete Deliverable 2.

Filter the data and create a new DataFrame or table to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on.

Pgadmin:
<img width="410" alt="screenshot of total votes over 20" src="https://user-images.githubusercontent.com/85860367/141741628-bb544b16-3c44-4894-88d2-45878c786917.PNG">

Pyspark:
<img width="410" alt="Pyspark Total over 20 df" src="https://user-images.githubusercontent.com/85860367/141741930-048892dc-0b1e-4a4d-9998-3fa4bd7e4d78.PNG">

Filter the new DataFrame or table created in Step 1 and create a new DataFrame or table to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.

Pyspark
<img width="410" alt="Helpful df" src="https://user-images.githubusercontent.com/85860367/141742725-ad21b241-71af-4e10-b5e3-134daa7daba0.PNG">

If you use the SQL option below, you’ll need to cast your columns as floats using WHERE CAST(helpful_votes AS FLOAT)/CAST(total_votes AS FLOAT) >=0.5.

Pgadmin
<img width="410" alt="helpful votes table screenshot" src="https://user-images.githubusercontent.com/85860367/141742478-75a3560d-8af1-4678-a514-dc14f22f8e67.PNG">

Filter the DataFrame or table created in Step 2, and create a new DataFrame or table that retrieves all the rows where a review was written as part of the Vine program (paid), vine == 'Y'.

Pgadmin
<img width="410" alt="paid vine table screenshot" src="https://user-images.githubusercontent.com/85860367/141743024-86a0cc7c-46ef-4423-8d03-4b275493e4af.PNG">

Pyspark
<img width="410" alt="paid vine df" src="https://user-images.githubusercontent.com/85860367/141743190-00010434-fbc6-4077-8098-494f49bbb8ea.PNG">

Repeat Step 3, but this time retrieve all the rows where the review was not part of the Vine program (unpaid), vine == 'N'.

Pgadmin
<img width="410" alt="unpaid vine table" src="https://user-images.githubusercontent.com/85860367/141743474-b35f17a2-211f-42b0-8772-9514a2383f22.PNG">

Pyspark
<img width="410" alt="Unpaid df" src="https://user-images.githubusercontent.com/85860367/141743577-5f2526d8-5e91-4e99-8969-ef2fd8c62e63.PNG">

Determine the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of review (paid vs unpaid).

Pyspark
<img width="410" alt="percentage and count for 5 stars" src="https://user-images.githubusercontent.com/85860367/141744320-9a48a744-8a54-42d1-b21a-c27cb669ebf6.PNG">

* Deliverable 3: A Written Report on the Analysis (README.md)

Overview of the analysis: Explain the purpose of this analysis.

Results: Using bulleted lists and images of DataFrames as support, address the following questions:

Summary

Pgadmin 
<img width="410" alt="Total Summary snapshot" src="https://user-images.githubusercontent.com/85860367/141743775-b7373180-ddd1-43db-80a9-16f9178cce2e.PNG">

Pyspark
<img width="410" alt="Summary df" src="https://user-images.githubusercontent.com/85860367/141743989-4e7ded5b-546a-4db8-898f-00847bf8e0d6.PNG">

How many Vine reviews and non-Vine reviews were there?
For the Furniture dataset:

_**Vine Reviews = 136**_

_**Non-Vine Reviews = 18,019**_

How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
For the furniture dataset:

_**Vine Reviews that were 5-stars = 74**_

**_Non-Vine Reviews that were 5-stars = 8,482_**

What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
For the furniture dataset:

**_Vine Reviews that were 5-stars percentage = 74/136 or 54.41%_**

**_Non-Vine Reviews that were 5-stars = 8,482/18,019 or 47.07%_**

### Summary
Summary: In my opinion there is no positivity bias for reviews in the Vine program. At first glance, it appeared that there would be bias; however after further analysis, it indicates that there are more non-members entering the reviews than Vine members.  As a marketing strategy, we may want to know why don't more Vine members provide a review and how to increase the 5-star rating.  We may want to provide incentives for the Vine members to provide more reviews and increase ratings.  Or reach out to Non-members to provide a membership on a trial period.
Then, provide one additional analysis that you could do with the dataset to support your statement, I think I would like to analyze the number of years a member has been a Vine member.  It is possible that they are satisfied with the service but feel that they do not need to offer a review.  I would like to analyze the number of purchases a member has made or the amount of the purchase in a given year.  We may need to reach out to the loyal customers for process improvement or incentive for a loyalty program.

For this assignment I ended up doing SQL and Pyspark due to the percentage calculation, so that is why there are SQL tables and screenshots.

