---
title: "Amazon S3 Target"
weight: 4
chapter: false
pre: "<b> d. </b>"
---

In this section, we create an Amazon S3 bucket to use as the target destination for our data. Amazon S3 is a highly available, durable, and scalable object storage built to store and retrieve any amount of data from anywhere cost-effectively.

1. Open the [**Amazon S3 console**](https://console.aws.amazon.com/s3/) , and then Click on Create bucket.


1. S3 bucket names must be unique accross all Amazon S3. Name your bucket **_dmstargetbucket-<YourInitial>-<RandomNumber>_**, where **"YourInitial"** is the first letter of your first and last name in lowercase, and **"RandomNumber"** is any 4 digit random number you want to pick. For example: **_dmstargetbucket-xy-1234_**. Leave all other setting as default. Just be sure you are in the region where all the other DMS resources for your workshop have been created.


1. Navigate to the bucket that you just created usually by click on the name, and then choose **Create folder** button. Name the folder **_dmstargetfolder_**, take all the other defaults and then choose **Create Folder** button.


1. Next, you need to **Create an AWS IAM policy** that gives access to the S3 bucket that you just created.

    Navigate to the IAM console , and then choose **Policies** from the navigation pane.


1. Choose **Create policy** ,and then choose **JSON**. Copy the following JSON code to the IAM policy editor in the console. Update the resource section of the policy where it says **_"REPLACE-WITH-YOUR-BUCKET-NAME"_**, with the name of your bucket. Make sure to keep the * at the end of the name and you change it in both places below. Click on **Review policy**.

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
                    "s3:DeleteObject"
                ],
                "Resource": [
                    "arn:aws:s3:::REPLACE-WITH-YOUR-BUCKET-NAME*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:ListBucket"
                ],
                "Resource": [
                    "arn:aws:s3:::REPLACE-WITH-YOUR-BUCKET-NAME*"
                ]
            }
        ]
    }
    ```

1. In the Name field, enter **_DMS-LAB-S3-Access-Policy_**, and then click **Create policy**.


1. Next, you need to associate the policy with an AWS IAM role. AWS DMS will assume this role in order to have premissions to put objects in the target Amazon S3 bucket.

1. Open the [**IAM console**](https://console.aws.amazon.com/iam/), and then go to **Roles** from the navigation pane.

1. Click in the search bar and type **_dms-vpc_** and click on the **_dms-vpc-role_** link that shows up

1. Click add permissions then attach policy and add the policy we just created **_DMS-LAB-S3-Access-Policy_** then click **Add permission** button.

1. Save the **Role ARN** from **Summary** page into your notepad.