---
title: "Schema Conversion"
weight: 1
chapter: false
pre: "<b> 3.1.1. </b>"
---

{{% notice info %}}
This section is only apply for Amazon Aurora targets. If you are using another target, you can skip to [section 3.1.2](../3.1.2-Migration/)
{{% /notice %}}

This section demonstrates how to use the AWS Schema Conversion Tool for schema conversion from Microsoft SQL Server or Oracle to Amazon Aurora (MySQL or PostGreSQL). Additionally, you will observe how AWS SCT helps you spot the differences between the two dialects; and, provides you with tips about how you can modify procedural code when needed to successfully migrate all database objects.

![Convert MS SQL to Aurora MySQL](/images/3/1/1/0001.png?width=50pc)