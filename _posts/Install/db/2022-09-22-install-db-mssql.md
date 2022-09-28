---
title: Mssql server install
author: kimjeahyun
date: 2022-09-22 00:00:00 +0900
categories: [설치,db]
tags: [설치,db]
---

# How to install MSSQL Server in windows 10 

>What is SQL Server?

Today we are gonna study about installation of the Microsoft SQL Server 

Microsoft is a relational database management System developed by Microsoft As a database server it is a software product with the primary function of storing and retrieving data as requested by other software application 

>Pre-Requisites

Below is a step by step process on how to download SQL in windows 10


link to download URL : [https://www.microsoft.com/en-in/sql-server/sql-server-downloads](https://www.microsoft.com/en-in/sql-server/sql-server-downloads)

Step 1) Go to upper URL : [https://www.microsoft.com/en-in/sql-server/sql-server-downloads](https://www.microsoft.com/en-in/sql-server/sql-server-downloads)

-   Developer - it has all feature which MS SQL Server offers but we cannot use it in production. From the learing perspective , is it an ideal condidate to start

-   Express - it is business intelligence application 

so we install useing Developer version

Step 2) Double Click on SQL2019-SSEI-DEV 
and then Choose the Basic version by clicking on the Basic option 


Step 3) Accept the terms 

Microsoft Server License Terms screen will aprear. Read The License Terms and them click !!!!
and then Choose the Location 

after the download is complete


This setup is self-sufficient for proceeding further with learning SQL server, and we can ‘Close’ this window.

However, below is a summary of the label and button:


- Instance name: This is by default labeled as MSSQLSERVER.

- Connect now: This will open a separate command line window for connection testing of what we have just installed.The system will run by default ‘select @@Version’ statement to confirm that we can connect to new MSSQLSERVER instance successfully.

-   Customize: This will open the SQL Installation center to customize further and add feature other than which are there as a part of the BASIC installation.

-   Install SSMS: This is IDE which will take us to Microsoft SSMS download link. We will cover SSMS in detail in our SSMS tutorial.

-   Close: This will close this window. The user is now ready to install SSMS IDE as instructed in SSMS tutorial.