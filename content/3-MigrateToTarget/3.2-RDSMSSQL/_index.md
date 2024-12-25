---
title: "Amazon RDS for SQL Server Target"
weight: 2
chapter: false
pre: "<b> 3.2. </b>"
---

This step-by-step guide demonstrates how you can use **AWS Database Migration Service (DMS)** to migrate data to Microsoft SQL Server databse running on an **Amazon RDS instance**. Additionally, you will use AWS DMS to continually replicate database changes from the source database to the target database. 

{{% notice info %}}
AWS doesn't offer schema conversion to SQL Server as a target. Most customers are migrating to open source databases from SQL Server vs. moving non-SQLServer to SQL Server. If you have that use case please contact your AWS team so they can request that as a feature. Thus for this lab we'll move the tables and the data over to our SQL Server target.
{{% /notice %}}

The environment for this lab consists of:

- A data source like SQL Server or Oracle

- An EC2 instance with Schema Conversion Tool and other database gui tools, as the source database.

- A Microsoft SQL Server instance running on AWS RDS as the target database.