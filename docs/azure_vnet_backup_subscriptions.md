---
title: "Step 2. Select Azure Subscriptions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vnet_backup_subscriptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Azure Subscriptions


At the Subscriptions step of the wizard, select Azure subscriptions whose virtual network configuration you want to back up.

The backup appliance allows you to automatically collect and back up virtual network configuration data for all Azure subscriptions selected for Azure VM, Azure SQL and Azure Files backup policies. To do that, [enable automatic protection](azure_vnet_backup_subscriptions_automatic.md) for Azure subscriptions. To retrieve virtual network configurations of all automatically protected Azure subscriptions, the backup appliance will use permissions of service accounts specified in the settings of backup policies that protect resources residing in these Azure subscriptions.

You can also configure the Virtual Network Configuration Backup policy to protect configuration data for Azure subscriptions that are not specified in the settings of any backup policy, or choose another service account whose permissions the backup appliance will use to collect the virtual network configuration data of the automatically protected Azure subscriptions. To do that, [manually add Azure subscriptions](azure_vnet_backup_subscriptions_manual.md) to the Virtual Network Configuration Backup policy and configure backup settings for them.

Page updated 2026-07-01

