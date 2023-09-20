# Lambda Cloud Project

## Overview
This project is designed to read data from a MySQL database hosted on AWS RDS, save the results to an S3 bucket, and then post the data to an API endpoint. The architecture involves AWS RDS, EC2, S3, and Lambda services.

![Architecture](https://user-images.githubusercontent.com/108837052/194605139-52a6fc33-4ee7-46dd-b5fc-21fa5bf92e6f.png)

## How It Works

### Step 1: MySQL Database Setup
- Set up a MySQL database on AWS RDS and connect it with MySQL Workbench.

### Step 2: Data Loading
- Load data into the MySQL database using a provided SQL script.

### Step 3: Data Query
- Query the database to get the top 10 customers based on their purchases.

### Step 4: Save to S3
- Use an EC2 instance to run a Python script that fetches the query results and saves them as a JSON file in an S3 bucket.

### Step 5: Lambda Function
- A Lambda function is triggered when the JSON file is saved to the S3 bucket.
- The function fetches customer names from the database and sends the data to an API endpoint.

![Lambda Diagram](https://user-images.githubusercontent.com/108837052/194732445-3ce4dfc7-846f-455a-b045-ece143b4302f.JPG)

## Running the Project
- Use `init.sh` to initialize the project.
- `run.py` contains the main logic.
- AWS Lambda-related scripts are in the `lambda_script` folder.
- AWS Lambda Layer creation steps are in `mklayer.sh`.
- Libraries for the Lambda Layer are listed in `requirements.txt`.

## Note
- `.env` files containing secrets are not included in the repo. Make sure to create and use them for storing sensitive information.

## API Data Example
![API Data](https://user-images.githubusercontent.com/108837052/194609243-0abe3f13-dc76-473a-b51e-0b0f916bc72c.jpg)
