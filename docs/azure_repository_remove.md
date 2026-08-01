---
title: "Removing Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_repository_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Repositories


The consequences of actions performed with a repository depend on whether the repository has been added to the backup infrastructure using the Veeam Backup & Replication console or the backup appliance Web UI.

Removing Backup Repositories Using Veeam Backup & Replication Console

Veeam Plug-in for Microsoft Azure allows you to permanently remove repositories and storage vaults from the backup infrastructure:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to External Repositories.
3. Select the necessary repository and click Remove Repository on the ribbon.

Alternatively, you can right-click the repository and select Remove.

Note that the repository will not be removed from the backup appliance. To learn how to remove repositories from backup appliances, see [Removing Repositories Using Backup Appliance Web UI](#remove_repo_from_web_ui).

[![Remove repository](images/azure_removing_repository.webp)](images/azure_removing_repository.webp "Remove repository")

Removing Repositories Using Backup Appliance Web UI

You can remove backup repositories and storage vaults from the backup appliance. When you remove a repository, the appliance unassigns the repository from the folder in the target blob container so that the folder is no longer used as a repository.

|  |
| --- |
| Note |
| Even though the folder is no longer used as a repository, the backup appliance preserves all backups previously stored in the repository and keeps these backups in Microsoft Azure. You can assign the folder to a new backup repository so that the backup appliance imports the backed-up data to the configuration database. In this case, you will be able to perform all disaster recovery operations described in section [Performing Restore](azure_performing_restore.md).  If you no longer need the backed-up data, you can remove it as described in section [Managing Backed-Up Data](azure_managing_backups.md). |

To remove a repository, do the following:

1. Switch to the Configuration page.
2. Navigate to Repositories.
3. Select the repository and click Remove.

|  |
| --- |
| Important |
| Consider the following:   * You cannot remove a repository that is used by any backup policy or by a scheduled configuration backup. [Modify the settings of all the related policies](azure_backup.md) to remove references to the repository — and then try removing the repository again. * When you remove a backup repository from a backup appliance managed by a Veeam Backup & Replication server, this repository will not be removed from the Veeam Backup & Replication console automatically. In this case, you need to [remove the repository manually](#removing_repository_console). |

[![Removing Repositories](images/azure_removing_backup_repositories.webp)](images/azure_removing_backup_repositories.webp "Removing Repositories")

Page updated 2026-07-28

