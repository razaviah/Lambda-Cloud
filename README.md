# Lambda Cloud Project -- Mini Project

Lambda Cloud Project, Data Engineering Diploma Program, WeCloudData

Content developed by: WeCloudData Academy


## 1. Project Description

In this project, you need to read data from a relational database (MySQL), save the result to S3, and finally post your result to an API endpoint. Here is the general architecture:

![architecture](https://user-images.githubusercontent.com/108837052/194605139-52a6fc33-4ee7-46dd-b5fc-21fa5bf92e6f.png)

## 2. Detail Steps

1. Start a MySQL database on AWS RDS and connect RDS with MySQL Workbench. If you don’t know how to set this, please watch the ([video](https://www.youtube.com/watch?v=Ng_zi11N4_c)).
2. Download the sql script from the EXERCISE FILES. And run the script on MySQL to load data. You will have a database called superstore.
3. Query the database, to get the top 10 customer ids who have the most purchase. Get their customer id and sum of the customer sales (you can use different column name) from the database.
4. After getting the result, save the result to S3. In order to do so:
