---
title: "Step 5. Configure Additional Restore Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_entire_vnet_restore_zone_mapping.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 5. Configure Additional Restore Settings


[This step applies only if you have selected the Restore to new location, or with different settings option at the Restore Mode step of the wizard]

At the Settings step of the wizard, you can choose whether to add a suffix to restored item names if items with the same names already exist. To do that, in the Item Names section, set the Add suffix toggle to On and enter the necessary suffix in the Suffix field.

|  |
| --- |
| Important |
| When restoring the configuration to a new location but the same subscription, make sure the name of each restored item is unique across the entire subscription. Otherwise, Veeam Backup for Microsoft Azure may not be able to perform the restore operation. |

[![Configuring Additional Restore Settings](images/azure_vnet_restore_settings.webp)](images/azure_vnet_restore_settings.webp "Configuring Additional Restore Settings")

Page updated 2024-06-12

