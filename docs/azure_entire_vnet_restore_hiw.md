---
title: "Entire Virtual Network Configuration Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_entire_vnet_restore_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Entire Virtual Network Configuration Restore


To restore the entire virtual network configuration from a backup, a backup appliance performs the following steps:

1. Retrieves the backed-up virtual network configuration from the backup appliance database.
2. Validates the restore operation: sends API requests to Microsoft Azure to verify that Azure service quotas are not exceeded and there are no subnet CIDR block conflicts.
3. Retrieves information on existing items and their settings in the current Azure virtual network configuration.
4. Restores the backed-up virtual network configuration:

1. Creates the missing virtual network configuration items.
2. Modifies settings of the existing items that do not match the backed-up settings.

To learn how to restore the entire virtual network configuration from a virtual network configuration backup, see [Performing Entire Virtual Network Configuration Restore](azure_entire_vnet_restore.md).

Page updated 2026-07-01

