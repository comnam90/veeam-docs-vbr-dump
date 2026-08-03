---
title: "Entire VPC Configuration Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_vpc_entire.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Entire VPC Configuration Restore


To restore the entire VPC configuration from a backup, a backup appliance performs the following steps:

1. Retrieves the backed-up VPC configuration from the backup appliance database.
2. Validates the restore operation: sends API requests to AWS to verify that AWS service quotas are not exceeded and there are no subnet CIDR block conflicts.
3. Retrieves information on existing items and their settings in the current Amazon VPC configuration.
4. Restores the backed-up VPC configuration:

1. Creates the missing VPC configuration items.
2. Modifies settings of the existing items that do not match the backed-up settings.

To learn how to restore an entire VPC configuration from a VPC configuration backup, see [Performing Entire Configuration Restore](aws_vpc_entire_restore.md).

Page updated 2026-05-19

