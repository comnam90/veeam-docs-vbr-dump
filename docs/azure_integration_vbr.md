---
title: "Integration with Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_integration_vbr.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Integration with Veeam Backup & Replication


Starting from version 6.0, Veeam Plug-in for Microsoft Azure is part of the Veeam Backup & Replication solution. Veeam Plug-in for Microsoft Azure extends the Veeam Backup & Replication functionality and allows you to add backup appliances to Veeam Backup & Replication. With Veeam Plug-in for Microsoft Azure, you can manage data protection and recovery operations for all these appliances from a single Veeam Backup & Replication console.

Versions 6.0, 7.0 and 8.0 come with 2 major features — the ability to create backups of Azure Virtual Network configuration components and the ability to back up Cosmos DB accounts. These features are available only for backup appliances managed by a Veeam Backup & Replication server. To unlock the full functionality, [install Veeam Plug-in for Microsoft Azure on the server](azure_deploying_plug_in.md) and [add your appliances](azure_adding_appliance_console.md) to the backup infrastructure.

|  |
| --- |
| Note |
| The current version of the Veeam Backup & Replication console comes with Veeam Plug-in for Microsoft Azure pre-installed by default. For the list of compatible versions of Veeam Backup & Replication, see [System Requirements](azure_system_requirements.md#compatibility). |

Considerations and Limitations

Before you add backup appliances to the backup infrastructure, consider the following:

* If you remove a backup appliance from the backup infrastructure, the following will happen:

* You will no longer be able to enable and start the virtual network configuration backup policy.
* You will no longer be able to add and start Cosmos DB backup policies. Creating Cosmos DB backups manually will also be unavailable.

* If the connection between a backup appliance and the backup server is lost for more than 31 days, the appliance will enter the standalone mode, and you will no longer be able to back up virtual network configurations and Cosmos DB accounts.

Related Topics

* [Protecting Cosmos DB Accounts](azure_overview_cosmos_db.md)
* [Protecting Virtual Network Configurations](azure_overview_vnet.md)

Page updated 2026-07-01

