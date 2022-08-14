# big-data-challenge


## Big Data - Extract Transform Load - Amazon Shoppers Reviews
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


# Level 2
I decided the use the **Digital Video Games Reviews** dataset to do further analysis using PySpark to investigate whether Vine reviews are free of bias but I could not find a dataset with vine reviews so I decided to look at verified purchase reviews vs unverified purchases.
![video_games_df](https://user-images.githubusercontent.com/67019030/184520044-6a5db4ed-5023-4617-8fd6-441e26f14df6.png)

## Summary Analyis

My findings:
![verified_vs_unverified](https://user-images.githubusercontent.com/67019030/184520281-2617751c-4933-493c-9dd5-019f42283d08.png)

* There are 124,316 verified purchase reviews and 21115 unverified purchase reviews in this dataset making it very skewed
*
*


### Verified Purchases vs Unverified Purchases reviews
First I filtered the reviews to get **DataFrames of Verified and Unverified Purchases reviews:**
<table>
  <tr>
    <td>Verified Purchase Reviews</td>
     <td>Unverified Purchases reviews</td>
  </tr>
  <tr>
    <td><img src="![verified_purchases_df](https://user-images.githubusercontent.com/67019030/184520476-02edb4d1-e34a-40e5-a8ca-7ec2cf4a8f62.png)" width=500 height=480></td>
    <td><img src="![unverified_purchases_df](https://user-images.githubusercontent.com/67019030/184520488-1c53a8ce-4e93-46d6-b6ae-f039d1c22833.png)" width=500 height=480></td>
  </tr>
 </table>




**Top Ten Verified vs Unverified Purchases reviews by Total Votes and Total Helpful Votes:**

<table>
  <tr>
    <td>Verified Purchase Reviews</td>
     <td>Unverified Purchases reviews</td>
  </tr>
  <tr>
    <td><img src="![verified_top_ten](https://user-images.githubusercontent.com/67019030/184520533-42de18f8-4a33-477c-ad28-2424f7b5481d.png)" width=500 height=480></td>
    <td><img ![top_ten_unverified](https://user-images.githubusercontent.com/67019030/184520553-685daa83-9f13-4870-9af4-8fbe71c1579b.png)
src="![Uploading top_ten_unverified.png…]()
" width=500 height=480></td>
  </tr>
 </table>


### Reviews Summary Statistics:

* **Verified Purchase Reviews**
![verified_statistics](https://user-images.githubusercontent.com/67019030/184520152-127a4dcb-4c44-4403-ae94-3397570e1052.png)


* **Unverified Purchase Reviews Summary Statistics:**

![unverified_statistics](https://user-images.githubusercontent.com/67019030/184520275-f15e18e3-7017-482d-acf6-8fd60b913ddf.png)
