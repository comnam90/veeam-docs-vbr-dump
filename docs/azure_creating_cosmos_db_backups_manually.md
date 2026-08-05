---
title: "Creating Cosmos DB Backups Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_creating_cosmos_db_backups_manually.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Cosmos DB Backups Manually


Veeam Plug-in for Microsoft Azure allows you to manually create backups of Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts.

|  |
| --- |
| Note |
| The backup appliance does not include backups of Cosmos DB accounts created manually in the backup chain and does not apply the [configured retention policy settings](azure_cosmos_db_backup_policy_schedule.md) to these backups. This means that the backups are kept in the repository unless you remove them manually, as described in section [Cosmos DB Data](azure_removing_cosmos_db_backups.md). |

To manually create backups of Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts, do the following:

1. Navigate to Resources > Databases > Cosmos DB.
2. Select the check box next to the necessary Cosmos DB for PostgreSQL and Cosmos DB for MongoDB accounts and click Take Backup Now.

For the accounts to be displayed in the list of available resources, they must reside in any region included in a backup policy as described in section [Creating Cosmos DB Backup Policies](azure_cosmos_db_backup_source_settings.md#regions) (step 3b).

1. Complete the Take Manual Backup wizard:

1. At the Account step of the wizard, select a service account whose permissions the backup appliance will use to create backups.

For an account to be displayed in the accounts list, it must be added to the backup appliance as described in section [Adding Service Accounts](azure_service_account_add.md).

1. At the Options step of the wizard, do the following:

1. In the Backup target section, click Choose repository.

In the Choose repository window, select a repository where the created backups will be stored. For a repository to be displayed in the Repository list, it must be added to the backup appliance, must have the Hot or Cool access tier assigned and must have immutability disabled, as described in section [Adding Backup Repositories](azure_repository_add_ui.md) or [Adding Storage Vaults](azure_repository_vdc_add_ui.md).

1. In the Processing options section, specify credentials that the backup appliance will use to connect to the processed Cosmos DB for PostgreSQL accounts. For more information, see [Configure Processing Options](azure_cosmos_db_processing_options.md).

1. At the Summary step of the wizard, review summary information, choose whether you want to proceed to the Session Log page to track the progress of repository creation, and click Finish.

[![Creating Backup Manually](images/azure_creating_cosmos_db_backups_manually.webp)](images/azure_creating_cosmos_db_backups_manually.webp "Creating Backup Manually")

Page updated 2026-07-01

