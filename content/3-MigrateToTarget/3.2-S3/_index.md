---
title: "Amazon S3 Target"
weight: 2
chapter: false
pre: "<b> 3.2. </b>"
---

This section is a step-by-step guide which demonstrates how you can use **AWS Database Migration Service (DMS)** to migrate data to **Amazon Simple Storage Service (Amazon S3)** bucket. Additionally, you will use AWS DMS to continually replicate database changes from the source database to the target S3 bucket.

The environment for this lab consists of:

- A data source like SQL Server or Oracle

- An EC2 instance with Schema Conversion Tool and other database gui tools, as the source database.

- An Amazon S3 Bucket as the target destination for the data.