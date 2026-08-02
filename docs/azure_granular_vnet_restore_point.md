---
title: "Step 2. Select Region, Restore Point and Items to Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_granular_vnet_restore_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Region, Restore Point and Items to Restore


At the Restore List step of the wizard, select virtual network configuration items you want to restore, and choose an Azure region and a restore point that will be used to restore the selected items. By default, the backup appliance uses the most recent valid restore point. However, you can restore the virtual network configuration data to an earlier state.

1. To select the region and the restore point:

1. In the Region section, select an Azure region whose network configuration items you want to restore.
2. In the Restore point section, click the link to the right of Restore point.
3. In the Available restore points window, select the necessary restore point and click Apply.

1. To select the virtual network configuration items:

1. In the Items section, click Edit.
2. In the Edit restore list window, click Add to Restore List.
3. In the Items List window, select check boxes next to the items that you want to restore, and click Add.
4. In the Edit restore list window, review the restore list and click Apply.

|  |
| --- |
| Important |
| A resource group that has the same name as the original resource group must exist in the original location. Otherwise, Veeam Backup for Microsoft Azure will not be able to perform the restore operation. |

[![Selecting Virtual Network Restore Point and Items](images/azure_vnet_restore_granular_items.webp)](images/azure_vnet_restore_granular_items.webp "Selecting Virtual Network Restore Point and Items")

Page updated 2026-07-01

