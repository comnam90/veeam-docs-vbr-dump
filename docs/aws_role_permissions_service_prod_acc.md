---
title: "Worker Configuration IAM Role Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_service_prod_acc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker Configuration IAM Role Permissions


When creating a new [worker configuration](aws_worker_add_config_prod.md), you specify an IAM role whose permissions will be used to list network settings available in AWS Regions of production AWS accounts. The specified IAM role must be granted the following permissions:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Action": [                 "ec2:DescribeAvailabilityZones",                 "ec2:DescribeVpcs",                 "ec2:DescribeRegions",                 "ec2:DescribeAccountAttributes",                 "ec2:DescribeSubnets",                 "ec2:DescribeSecurityGroups"             ],                       "Resource": "\*",                       "Effect": "Allow"           }     ]  } |

Page updated 2026-05-19

