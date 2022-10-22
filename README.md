# Lambda Cloud Project -- Mini Project

Lambda Cloud Project, Data Engineering Diploma Program, WeCloudData

Content developed by: WeCloudData Academy


## 1. Project Description

In this project, you need to read data from a relational database (MySQL), save the result to S3, and finally post your result to an API endpoint. Here is the general architecture:

<p align="center">
    <img src="https://user-images.githubusercontent.com/108837052/194605139-52a6fc33-4ee7-46dd-b5fc-21fa5bf92e6f.png" alt="architecture"/>
</p>

## 2. Detail Steps

1. Start a MySQL database on AWS RDS and connect RDS with MySQL Workbench. If you don’t know how to set this, please watch the ([video](https://www.youtube.com/watch?v=Ng_zi11N4_c)).
2. Download the sql script from the EXERCISE FILES. And run the script on MySQL to load data. You will have a database called superstore.
3. Query the database, to get the top 10 customer ids who have the most purchase. Get their customer id and sum of the customer sales (you can use different column name) from the database.
4. After getting the result, save the result to S3. In order to do so:
    1) You need to create an EC2 instance and build a python project.
    2) Use the python script to bring the result from MySQL to EC2. The result includes the customer id and the sum of the customer salesof the top 10 customers.
    3) Save the result as a .json file locally in EC2.
    4) Upload the file from EC2 to S3. The file should be in an ‘input’ folder in the S3 bucket. 

5. When the file lands on the S3 bucket, a lambda is triggered. The lambda function will:
    1) get the customer id list from the S3 ..json file;
    2) query the customer names from the database based on the customer id list.
    3) send a JSON data, including customer id , customer name and today’s date to an API endpoint. The API endpoint is: https://virtserver.swaggerhub.com/wcd_de_lab/top10/1.0.0/add
    4) Here are some tips for the lambda function: 
        * When you create a lambda function, you may need a lambda layer to install 3rd party libraries. This is an article about how to add a layer.([article](https://towardsdatascience.com/building-custom-layers-on-aws-lambda-35d17bd9abbb))
        * Put the customer id, customer name and today’s date (format: ‘1990-01-01’) in a JSON structure variable, such as data. (But the variable is a string).
        * Use POST to send data. Here is what the final API data looks like: 
        
        <p align="center">
            <img src="https://user-images.githubusercontent.com/108837052/194609243-0abe3f13-dc76-473a-b51e-0b0f916bc72c.jpg" alt="json"/>
        </p>
        

        
        * When the POST Succeed, the return code should be 201. Use the status_code method in requests to get the returned code. 

    5) Use python project structure.
    6) Use git repository to save your code. 


## 3. Diagram
The project diagram is below:

<p align="center">
    <img src="https://user-images.githubusercontent.com/108837052/194732445-3ce4dfc7-846f-455a-b045-ece143b4302f.JPG" alt="lambda-lab2"/>
</p>


## 4. How to run the project



1. use "init.sh" to run the program
2. "run.py" is the script to do main work
3. files under "lambda_script" is the files will be used in AWS lambda
4. 'lambda_function.py' is the script used to run lambda function
5. under 'my-lambda-script' aws-layer is the folder used to create lambda layer
6. under 'my-lambda-script', mklayer.sh is the steps to create a layer
7. under 'my-lambda-script', requirements.txt is the libaries used for the layer.
8. Be aware of all the .env files are missing from the repo, please create and use it for secrets.

