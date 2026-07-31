---
title: "Step 7. Specify Amazon S3 Bucket"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_export_entire_vpc_bucket.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 7. Specify Amazon S3 Bucket


At the Target step of the wizard, specify an Amazon S3 bucket where the backup appliance will save the CloudFormation template with the exported VPC configuration data.

Choose whether you want to save the template in the root folder of the selected Amazon S3 bucket or to create a new folder for the template.

|  |
| --- |
| Note |
| If you enable the [private network deployment](aws_enable_private_network_deployment.md) functionality, the backup appliance will still use the public s3.<region>.amazonaws.com endpoint to export VPC configuration. |

[![Exporting VPC Configuration](images/aws_vpc_export_entire_bucket.webp)](images/aws_vpc_export_entire_bucket.webp "Exporting VPC Configuration")

Page updated 2026-05-21

