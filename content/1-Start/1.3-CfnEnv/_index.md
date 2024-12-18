---
title: "Prepare your environment"
weight: 3
chapter: false
pre: "<b> 1.3. </b>"
---

In this step, you will use a CloudFormation (CFN) template to deploy the infrastructure for this database migration. AWS CloudFormation simplifies provisioning the infrastructure, so we can concentrate on tasks related to data migration.

1. Open the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation/) , and click on Create Stack in the left-hand corner.

1. Select **Template is ready**, and choose **Upload a template file** as the source template. Then, click on **Choose file** and upload the [DMSWorkshop.yaml](https://static.us-east-1.prod.workshops.aws/public/9b44f2ff-63cb-460b-86c6-2e1e30e219b7/static/DMSWorkshop.yaml). Click **Next**.

1. Populate the form as with the values specified below, and then click **Next**.

    |  Input Parameter	 |  Values	 |
    ---------------------|----------------------------------|
    |  Stack Name	 |  A unique identifier without spaces.	 |
    |  MigrationType / Lab Type	 |  Database that you want to migrate (Oracle or SQL Server).	 |
    |  EC2ServerInstanceType	 |  An Amazon EC2 Instance type from the drop-down menu. Recommend using the default value.	 |
    |  KeyName	 |  The KeyPair (DMSKeypair) that you created in the previous step.	 |
    |  RDSInstanceType	 |  An Amazon RDS Instance type from the drop-down menu. Recommend using the default value.	 |
    |  VpcCIDR	 |  The VPC CIDR range in the form x.x.x.x/16. Defaults to 10.20.0.0/16	 |
    |  IAMRoleDmsVpcExist	 |  Does your AWS account already have dms-vpc-role(goto IAM>roles & search for "dms-vpc" to check) if this role is not there template will fail-rollback unless you change default Y to N?	 |

{{% notice info %}}
The resources that are created here will be prefixed with whatever value you specify in the Stack Name. Please specify a value that is unique to your account.
{{% /notice %}}

4. On the **Stack Options** page, accept all of the defaults and click **Next**.

1. On the **Review** page, click **Create stack**.

1. At this point, you will be directed back to the CloudFormation console and will see a status of **CREATE_IN_PROGRESS**. Please wait here until the status changes to **CREATE_COMPLETE**.

1. Once CloudFormation status changes to **CREATE_COMPLETE**, go to the Outputs section.

1. Make a note of the **Output** values from the CloudFormation environment that you launched as you will need them for the remainder of the tutorial: