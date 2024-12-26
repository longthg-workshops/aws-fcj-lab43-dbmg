---
title: "Convert the Schema"
weight: 3
chapter: false
pre: "<b> 3.1.1.3. </b>"
---

Now that you have created a new Database Migration Project, the next step is to convert the schema of the source database to the Amazon Aurora MYSQL.

1. Click on **_DMS_SAMPLE_** schema from source on the left hand side of screen

    {{% expand ">> For Oracle Source expand here" %}}



    {{% /expand %}}

    {{% expand ">> For SQL Server Source expand here" %}}



    {{% /expand %}}

    AWS SCT analyses the schema and creates a database migration assessment report for the conversion to PostgreSQL. Items with a red exclamation mark next to them cannot be directly translated from the source to the target. This includes Stored Procedures, and Packages.

1. Click on the View button, and choose Assessment Report view.

    For Oracle source it will look like

    ![Oracle assessment](/images/3/1/1/3/0001.png?width=80pc)

    SQL Server will look similar just with SQL Server source on left side of the screen and an SQL Server database hierachy instead of Oracle. You'll want to click on dms_sample in MS SQL Server

1. Next, navigate to the Action Items tab in the report to see the items that the tool could not convert, and find out how much manual changes you need to make.

    For MS SQL Server source, it should look like:

    ![Oracle Action](/images/3/1/1/3/0002.png?width=80pc)

    For Oracle source, it should look like:

    ![MSSQL Action](/images/3/1/1/3/0003.png?width=80pc)

    AWS SCT analyzes the schema and creates a database migration assessment report for the conversion to Aurora MySQL. Items with a blue mark next to them cannot be directly translated from the source to the target. Items in green will be translated over from source to target. In this case, this includes the stored procedures. For each conversion issue, you can complete one of the following actions:

    1. Modify the objects on the source database so that AWS SCT can convert the objects to the target Aurora MySQL database.
    2. Instead of modifying the source schema, modify scripts that AWS SCT generates before applying the scripts on the target Aurora MySQL database.

    However, for the sake of time, we skip modifying all the objects that could not be automatically converted. Instead, as an example, you will manually modify one of the stored procedures from within SCT to make it compatible with the target database. 
    
    This is demonstrated in [this subsection](./ModifyCode).


1. Click on the `**dms_sample**` for Oracle or dbo for sql server schema in the left-hand panel, and click **Convert Schema**.
For Oracle it will look like below and for other databases similar except that database name at the top and its hierarchy on the left

1. You may be prompted with a dialog box **“Object may already exist in the target database, replace?”** Select **Yes**.


1. Right click on the dms_sample_dbo(SQL Sever) or dms_sample(other DBs) schema in the right-hand panel, and click Apply to database.

    {{% expand ">> For Oracle Source expand here" %}}



    {{% /expand %}}

    {{% expand ">> For SQL Server Source expand here" %}}



    {{% /expand %}}


1. When prompted if you want to apply the schema to the database, click **Yes**.


1. At this point, the schema has been applied to the target database. Expand the dms_sample_dbo or dms_sample schema on the right hand pane to see the tables, views, procedures, etc. Note please expand per source below as some have extra steps specifically SQL Server requires additional steps

    {{% expand ">> For Oracle Source expand here" %}}



    {{% /expand %}}

    {{% expand ">> For SQL Server Source expand here" %}}



    {{% /expand %}}


You have sucessfully converted the database schema and object from source to Amazon Aurora.

This part demonstrated how easy it is to migrate the schema of a source database into Amazon Aurora PostgreSQL using the AWS Schema Conversion Tool. Similarly, you learned how the Schema Conversion Tool highlights the differences between different database engine dialects, and provides you with tips on how you can successfully modify the code when needed to migrate procedure and other database objects.

The same steps can be followed to migrate SQL Server and Oracle workloads to other RDS/Aurora engines including PostgreSQL and MySQL.