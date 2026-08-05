---
title: "Step 4. Choose Export Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_export_entire_vpc_mode.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Choose Export Mode


At the Export Mode step of the wizard, choose whether you plan to restore the exported VPC configuration to the original or to a custom location. If you select the Export to a new location option, specify the target AWS Region where the VPC configuration will be restored.

|  |
| --- |
| Important |
| * If you plan to restore the exported VPC configuration to the original location — when you restore the VPC configuration from the CloudFormation template, all exported VPC configuration items will be newly created in the source AWS Region. If there are any already existing items with the same names in the current VPC configuration, the restored items will be created with new IDs, but with the same names.  * If you plan to restore the exported VPC configuration to a custom location — the source and target AWS Regions may have different lists of the supported AWS services. In this case, when you restore the VPC configuration from the CloudFormation template, VPC endpoints created using an AWS service that is not available in the target AWS Region will not be restored. |

[![Exporting VPC Configuration](images/aws_vpc_export_entire_mode.webp)](images/aws_vpc_export_entire_mode.webp "Exporting VPC Configuration")

Page updated 2026-05-21

