# Big Data - Extract Transform Load - Amazon Shoppers Reviews
Using PySpark, PgAdmin, and AWS' Relational Databases using Google's Colab.

### “Alexa, Can You Handle Big Data?”
Many of Amazon's shoppers depend on product reviews to make a purchase. Amazon makes these datasets publicly available. They are quite large and can exceed the capacity of local machines. One dataset alone contains over 1.5 million rows; with over 40 datasets, data analysis can be very demanding on the average local computer.


### Datasets
I chose two datasets to ETL and analyse using PySpark, SQL/PgAdmin and AWS's RDS from Amazon's list of Reviews datasets at https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt:
* **Digital Music Reviews**

* **Digital Video Games Reviews**


# Level 1
For the first level I created a bucket on Amazon AWS where I uploaded the above 2 datasets so I could perform ETL on both of them.
![Screenshot 2022-08-13 at 22 38 53](https://user-images.githubusercontent.com/67019030/184511613-6e223f25-6acd-43d7-b201-17d099ac17d1.png)

* **Extract**
Data was `extracted` (imported) from the S3 AWS Buckets using PySpark and loaded them into datafarmes for further data transormation:
![Screenshot 2022-08-13 at 23 07 45](https://user-images.githubusercontent.com/67019030/184512195-b004e600-6ed2-4d83-9d40-dd0a9cd53fa2.png)

* **Transform**
Data was then `transformed`(cleaned) before tables were created using our PgAdmin SQL schema for reference.

![Screenshot 2022-08-13 at 23 09 51](https://user-images.githubusercontent.com/67019030/184512404-c44d0716-0b16-4095-9fc1-02d0b6e1a6da.png)

![Screenshot 2022-08-13 at 23 14 13](https://user-images.githubusercontent.com/67019030/184513574-faa11fe8-4f8a-417c-ae0b-25d03d106a0a.png)


* **Load**

Data was loaded (written) onto the RDS (relational database). Each table that was created above was then loaded onto the PgAdmin using AWS's RDS connection I created.
![Screenshot 2022-08-13 at 23 15 42](https://user-images.githubusercontent.com/67019030/184513964-536d61f7-a867-43e3-8cc2-fa6971bfcc88.png)

Lastly I saved both Google Colab files as ipynb into the Level 1 folder.


# Level 2
I decided the use the **Digital Video Games Reviews** dataset to do further analysis using PySpark to investigate whether Vine reviews are free of bias but I could not find a dataset with vine reviews so I decided to look at verified purchase reviews vs unverified purchases.
![video_games_df](https://user-images.githubusercontent.com/67019030/184520044-6a5db4ed-5023-4617-8fd6-441e26f14df6.png)

## Summary Analyis

My findings:

* There are 124,316 verified purchase reviews and 21115 unverified purchase reviews in this dataset making it very skewed

![verified_vs_unverified](https://user-images.githubusercontent.com/67019030/184521933-ecb0f238-ae1a-4d0c-8b39-422adcfa77c1.png)


* Top Ten Verified vs Unverified Purchases reviews by Total Votes and Total Helpful Votes:
 `SimCity - Limited Edition` has the highest helpful votes count and highest total votes count of both Verified and Unverified Purchase reviews




* Reviews Summary Statistics:
The most reviewed video game for Verified Purchase reviews is `Playstation Network Card` and for Unverified Purchase reviews is  `SimCity - Limited Edition`.

