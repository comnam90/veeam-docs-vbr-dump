---
title: "Removing Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repositories_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Repositories


The consequences of actions performed with a backup repository depend on whether the repository has been added to the backup infrastructure using the Veeam Backup & Replication console or the the backup appliance Web UI.

Removing Repository Using Veeam Backup & Replication Console

Veeam Plug-in for AWS allows you to permanently remove backup repositories and storage vaults from the backup infrastructure:

1. In the Veeam Backup & Replication console, open the Backup Infrastructure view.
2. Navigate to External Repositories.
3. Select the necessary repository and click Remove Repository on the ribbon.

Alternatively, you can right-click the repository and select Remove.

Note that the repository will not be removed from the backup appliance. To learn how to remove repositories from backup appliances, see [Removing Backup Repository Using Backup Appliance Web UI.](#remove_repo_from_web_ui)

[![Removing Repository](images/aws_removing_repository.webp)](images/aws_removing_repository.webp "Removing Repository")

Removing Repository Using Backup Appliance Web UI

You can remove backup repositories and storage vaults from the backup appliance. When you remove a repository, the appliance unassigns the repository role from the folder in the Amazon S3 bucket so that this folder is no longer used as a repository.

|  |
| --- |
| Note |
| Even though the Amazon S3 bucket is no longer used as a repository, the backup appliance preserves all backup files previously stored in the repository and keeps these files in Amazon S3. You can assign the Amazon S3 bucket to a new repository so that the backup appliance imports the backed-up data to the configuration database. In this case, you will be able to perform all disaster recovery operations described in section [Performing Restore](aws_recovery.md).  If you no longer need the backed-up data, either delete it as described in section [Managing Backed-Up Data](aws_backups_view.md) before you remove the repository from the backup appliance, or [use the AWS Management Console](aws_uninstall.md#removeData) to delete the data if the repository has already been removed. |

To remove a repository, do the following:

1. Switch to the Configuration page.

1. Navigate to Repositories.

1. Select the check box next to the repository and click Yes.

1. In the Remove Repository window, click Remove to acknowledge the operation.

|  |
| --- |
| Important |
| You cannot remove a backup repository that is used by any backup policy or by a scheduled configuration backup. Modify the settings of all the related policies to remove references to the repository — and then try removing the repository again. To learn how to modify the backup policy settings, see [Performing Backup](aws_backup.md). |

[![Removing Repositories](images/aws_repo_remove.webp)](images/aws_repo_remove.webp "Removing Repositories")

Page updated 2026-07-13

