---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_export_items_vpc_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Restore Point


At the Export List step of the wizard, select the VPC configuration items you want to export and a restore point that will be used to export the selected VPC configuration items. By default, the backup appliance uses the most recent valid restore point. However, you can export the VPC configuration data to an earlier state.

1. To select the restore point:

1. In the Choose restore point section, click the link to the right of Restore point.
2. In the Available restore points window, select the necessary restore point and click Apply.

1. To select the VPC configuration items:

1. In the Create export list section, select the type of VPC configuration item you want to export and click Edit.
2. In the Edit export list window, click Add to Export List.
3. In the Item List window, select check boxes next to the items that you want to export, and click Add.
4. In the Edit export list window, review the restore list and click Apply.

|  |
| --- |
| Important |
| When performing the export operation, the backup appliance does not validate the export list. If any of the VPC configuration items on which the selected items depend are missing from the current VPC configuration, the restore of the selected VPC configuration items from the created CloudFormation template will fail. |

[![Exporting VPC Configuration Items](images/aws_vpc_export_items_point.webp)](images/aws_vpc_export_items_point.webp "Exporting VPC Configuration Items")

Page updated 2026-05-21

