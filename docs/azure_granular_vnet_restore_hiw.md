---
title: "Granular Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_granular_vnet_restore_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Granular Restore


To restore specific items of the virtual network configuration from a backup, a backup appliance performs the following steps:

1. Retrieves from the backup appliance database the backed-up virtual network configuration data on items added to a [restore list](azure_granular_vnet_restore_point.md).
2. Validates the restore operation: sends a REST API request to Microsoft Azure to verify that Azure service quotas are not exceeded and there are no subnet CIDR block conflicts.
3. Retrieves information on existing items and their settings in the current Azure virtual network configuration.
4. Restores the selected items of the backed-up virtual network configuration:

* Creates the missing virtual network configuration items.
* Modifies settings of the existing items that do not match the backed-up settings.

To learn how to restore restores the selected virtual network configuration items from a virtual network configuration backup, see [Performing Granular Restore](azure_granular_vnet_restore.md).

Page updated 2026-07-01

