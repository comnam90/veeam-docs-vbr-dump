---
title: "Selected Items Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_vpc_items.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Selected Items Restore


To restore specific items of the VPC configuration from a backup, a backup appliance performs the following steps:

1. Retrieves from the backup appliance database the backed-up VPC configuration data on items added to a [restore list](aws_restore_items_vpc_point.md).
2. Validates the restore operation: sends API request to AWS to verify that AWS service quotas are not exceeded and there are no subnet CIDR block conflicts.
3. Retrieves information on existing items and their settings in the current Amazon VPC configuration.
4. Validates the restore list: sends API requests to AWS to check whether any of the selected VPC configuration items depend on other items that are missing from the current VPC configuration.

In case any VPC configuration items on which the selected items depend are missing, the backup appliance allows the user to add the missing items to the restore list.

1. Restores the selected items of the backed-up VPC configuration:

* Creates the missing VPC configuration items.
* Modifies settings of the existing items that do not match the backed-up settings.

|  |
| --- |
| Important |
| * VPC peering connections will have the Pending Acceptance status after restoring. To accept the restored VPC peering connections, use the AWS Management Console. For more information, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/peering/create-vpc-peering-connection.html).  * If restore of any selected item fails, backup appliances will stop the restore operation and initiate a rollback. During the rollback, they delete all newly created items but retain all changes made to existing VPC configuration items. |

To learn how to restore restores the selected VPC configuration items from a VPC configuration backup, see [Performing Selected Items Restore](aws_vpc_items_restore.md).

Page updated 2026-05-19

