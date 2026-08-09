---
title: "Connecting to Existing Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_add_console_existing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Connecting to Existing Repositories


When you connect to a backup appliance, all repositories that have already been configured on the appliance are automatically added to the backup infrastructure.

If an existing repository is not displayed under the External Repositories node or if you have recently configured a new repository on the appliance that is already connected to the backup server, do the following:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to Managed Servers.
3. Select a backup appliance that manages the necessary repository and click Edit Appliance on the ribbon.

Alternatively, you can right-click the backup appliance and select Properties.

1. In the Edit Veeam Backup for Microsoft Azure Appliance wizard, do the following:

1. Navigate to the Repositories step of the wizard and complete the step as described in section [Adding Appliances](azure_adding_appliance_repository.md) (step 8).

1. Complete the Edit Veeam Backup for Microsoft Azure Appliance wizard as described in section [Adding Appliances](azure_adding_appliance_apply.md) (steps 9-10).

Open the Backup Infrastructure view to verify that the repository is displayed under the External Repositories node.

|  |
| --- |
| Note |
| If you do not specify credentials of any Microsoft Azure storage account for a standard repository, you will only be able to use the Veeam Backup & Replication console to perform [entire VM restore](azure_entire_vm_restore_console.md) and [SQL database restore](azure_sql_restore_console.md) from backups stored in this repository. Moreover, information on the repository displayed in the Backup Infrastructure view under the External Repositories node will not include statistics on the amount of storage space that is currently consumed by restore points created by the backup appliance. |

Page updated 2026-07-01

