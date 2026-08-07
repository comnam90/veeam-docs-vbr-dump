---
title: "Step 3. Specify AWS Account Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_s3_account.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify AWS Account Settings


At the Account step of the wizard, do the following:

1. From the AWS account drop-down list, select access keys of an IAM user whose permissions Veeam Backup & Replication will use to access the repository. For more information on the required permissions that must be assigned to the IAM user, see [Plug-In Permissions](aws_req_permissions.md).

For access keys of an IAM user to be displayed in the AWS account drop-down list, they must be created in AWS and added to the Cloud Credentials Manager as described in section [Access Keys for AWS Users](cloud_credentials_aws.md). If you have not added the keys to the Cloud Credentials Manager beforehand, you can do it without closing the wizard. To do that, click either the Manage cloud accounts link or the Add button, and specify the access key and secret key in the Credentials window.

1. From the AWS region drop-down list, specify an AWS partition where the backup repository will reside; it can be either AWS Global Regions, AWS China Regions or AWS GovCloud (US) Regions.

|  |
| --- |
| Important |
| To check the availability of the region, Veeam Backup & Replication by default establishes a temporary test connection with the US East (N. Virginia) region using endpoints of the [AWS Security Token Service (STS)](https://docs.aws.amazon.com/general/latest/gr/sts.html) and [Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/general/latest/gr/ec2-service.html) AWS services. That is why the backup server must have access to this AWS Region. If you want to change the default region for a test connection, open a [support case](aws_logs.md). |

1. [Applies only if you choose to create a standard backup repository] From the Gateway server drop-down list, select a gateway server that will be used to access the repository.

For a server to be displayed in the Gateway server list, it must be added to the backup infrastructure. For more information on gateway servers, see [Solution Architecture](aws_overview.md).

![Step 3. Specify AWS Account Settings](images/aws_add_s3_account.webp "Add Amazon S3 repository - Account")

Page updated 2026-06-02

