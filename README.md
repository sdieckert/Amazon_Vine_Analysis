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

products_table:

review_id_table:

vine_table:

Each dataframe was loaded to PostgreSQL and the RDS. Due to the size of each dataframe, it took some time to load. To verify the data loaded correctly, I ran a sql statement on each table.

customer_table:

products_table:

review_id_table:

vine_table:

### Deliverable 2: Determine Bias of Vine Reviews

Using PySpark, analysis the vine_table dataset to determine if there is any bias towards reviews that were written as part of the Vine program. 

Vine_Review_Analysis Code

After dropping the nulls the dataset was around 1.7 million reviews. 

Filtering for only reviews with 20 or more votes dropped the dataset down to 65K. 


Next the dataset was filtered for helpful votes at least 50% which brought the total dataset to 40,565.

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


