---
title: "Virtual Network Configuration Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_how_vnet_backup_works.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Virtual Network Configuration Backup


A backup appliance performs virtual network configuration backup in the following way:

1. Sends API requests to Microsoft Azure to retrieve the virtual network configuration data, and saves this data in the configuration database.

To back up virtual network configurations of Azure subscriptions added to backup policies, the backup appliance uses permissions of service accounts specified in the backup policy settings. The virtual network configuration data is collected for the Microsoft Entra tenants to which the specified service accounts belong.

1. Creates a configuration record for each pair of an Microsoft Entra tenant and an Azure subscription whose virtual network configuration data is being backed up. Every time the Virtual Network Configuration Backup policy runs, the backup appliance updates the record to create a new restore point for each protected virtual network configuration.
2. If you [enable additional backup copy](azure_vnet_backup_copies.md) for the Virtual Network Configuration Backup policy, the backup appliance launches the Veeam Data Mover service on the backup appliance to copy the restore points from the configuration database to the target repository, creating an individual folder for each Azure subscription whose virtual network configuration data is protected by the policy.

Related Topics

* [Backup Chain](azure_backup_chain_vnet.md)
* [Virtual Network Configuration Backup Retention](azure_retention_backup_vnet.md)

Page updated 2026-07-01

