---
title: "Performing VPC Configuration Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_vpc_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing VPC Configuration Restore Using Console


You can recover corrupted Amazon VPC configurations in the backup appliance UI only. However, you can launch the VPC Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the AWS account in which VPC configuration has been backed up, select the AWS Region whose VPC configuration you to want restore and click Amazon VPC on the ribbon.

Alternatively, you can right-click the selected region and click Restore to Amazon VPC.

Veeam Backup & Replication will open the VPC Restore wizard in a web browser. Complete the wizard as described in section [VPC Configuration Restore](aws_restore_entire_vpc_point.md).

|  |
| --- |
| Important |
| * VPC configuration restore is available only if you have logged in to the Veeam Backup & Replication console under a user account with the Backup Administrator role. For more information on user roles, see [Managing Users and Roles](users_roles.md).  * Selected items restore of the virtual network configuration is not available from the Veeam Backup & Replication console — you can perform it using the backup appliance Web UI only. For more information, see [Performing Selected Items Restore](aws_vpc_items_restore.md). |

[![Restore VPC configuration](images/aws_restore_vpc.webp)](images/aws_restore_vpc.webp "Restore VPC configuration")

Page updated 2026-07-10

