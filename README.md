# Amazon_Vine_Analysis


## Project Overview

Selecting Amazon Video Game reviews from a given dataset, the projec will utilize PySpark to perform the ETL process to extract the dataset, transform the data, connect to a AWS RDS instance, and load the transformed data into pgAdmin. PySpark will be used to determine if there is any bias toward favorable reviews from Vine members in the dataset.

## Resources
- Data Source: Amazon Video Game Review Dataset
- Technology Used: AWS and RDS, PostgreSQL, Google Colab Notebook


## Challenge Overview

### Deliverable 1: Perform ETL on Amazon Product Reviews



Extract the Video Game Review dataset from an AWS S3 using PySpark in order to tranform the data into datasets that matched the schema of the PostgreSQL tables. The dataset was broken into 4 smaller dataframes:

Amazon_Reviews_ETL.ipynb Code

customer_table:

![customer_colab](https://user-images.githubusercontent.com/87085239/183271630-cbf5a034-df44-4971-9bec-c8e4ab44071a.png)

products_table:

![product_colab](https://user-images.githubusercontent.com/87085239/183271643-c51b5c1b-8cf3-4a16-8b9d-1fb654ea59c9.png)

review_id_table:

![review_colab](https://user-images.githubusercontent.com/87085239/183271651-7baf7de6-af0d-4425-a3d4-b3659fd7a688.png)

vine_table:

![vine_colab](https://user-images.githubusercontent.com/87085239/183271668-174baf63-863e-46ea-850f-5a431fb0e461.png)

Each dataframe was loaded to PostgreSQL and the RDS. Due to the size of each dataframe, it took some time to load. To verify the data loaded correctly, I ran a sql statement on each table.

customer_table:

![customer_sql](https://user-images.githubusercontent.com/87085239/183271677-d17b8f21-ad15-4ae5-afed-a9965fa1c7fb.png)

products_table:

![product_sql](https://user-images.githubusercontent.com/87085239/183271682-0d4533b8-dd1f-41dd-9006-8f5daa86ad20.png)

review_id_table:

![review_sql](https://user-images.githubusercontent.com/87085239/183271688-ed5d5848-0157-4bbe-9385-ea4077596bdb.png)

vine_table:

![vine_sql](https://user-images.githubusercontent.com/87085239/183271704-5617c3e3-4bc3-4d9a-971c-7f30263e32c7.png)

### Deliverable 2: Determine Bias of Vine Reviews

Using PySpark, analysis the vine_table dataset to determine if there is any bias towards reviews that were written as part of the Vine program. 

Vine_Review_Analysis Code

After dropping the nulls the dataset was around 1.7 million reviews. 

Filtering for only reviews with 20 or more votes dropped the dataset down to 65K. 

![twenty or more votes](https://user-images.githubusercontent.com/87085239/183271734-891c9347-4251-40aa-9425-43b1d55e91ea.png)

Next the dataset was filtered for helpful votes at least 50% which brought the total dataset to 40,565.

![50 helpful](https://user-images.githubusercontent.com/87085239/183271742-f452f657-28a3-40dc-aa4a-aa7a46a3503e.png)


## Results

- Total Reviews: 40,565

- Paid Vine Reviews
    - Total Reviews:94
    - 5 Star Reviews:48
    - 51% of vine reviews were 5-Star

- Non-Vine Reviews
    - Total Reviews:40471
    - 5 Star Reviews:15663
    - 38.7% of non-vine reviews were 5-Star


## Summary

It doesn't appear that the vine program is useful for the video game category. Although Vine reviews yield around 51% of 5-Star revies, they only make up around 0.23% of the total reviews. Non-paid 5-Star views is over 15.6K as opposed to 48 paid reviews.

### Additional Analysis

The average paid review is 4.2 and non-paid average around 3.3. 

I would recommend doing further anaylsis on paid reviews and their distribution of ratings and helpful_votes to detemine the quality of reviews being paid for.


