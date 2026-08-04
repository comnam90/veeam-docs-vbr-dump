---
title: "Performing Selected Items Export"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_vpc_items_export.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Selected Items Export


|  |
| --- |
| Note |
| If you export only specific VPC configuration items, you will not be able to choose a location. By default, the backup appliance will create a CloudFormation template to restore to the original location.  When you restore the exported items from the CloudFormation template, all exported VPC configuration items will be newly created in the source AWS Region. If there are any already existing items with the same names in the current VPC configuration, the restored items will be created with new IDs, but with the same names. |

To export specific VPC configuration items to a CloudFormation template, do the following:

1. [Launch the VPC Export wizard](aws_export_items_vpc_launch.md).
2. [Select a restore point and VPCs to export](aws_export_items_vpc_point.md).
3. [Specify an IAM identity for export](aws_export_items_vpc_account.md).
4. [Specify an Amazon S3 bucket where the Cloud Formation template must be placed](aws_export_items_vpc_bucket.md).
5. [Specify a reason for the export](aws_export_items_vpc_reason.md).
6. [Finish working with the wizard](aws_export_items_vpc_finish.md).

Page updated 2026-05-21

