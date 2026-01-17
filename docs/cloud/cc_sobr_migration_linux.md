---
title: "Switching from Linux Repository to Hardened Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_sobr_migration_linux.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

The SP can enable immutability for a Linux repository with tenant data. This allows the SP to increase the level of data protection for tenant backups. This operation is available for simple backup repositories and backup repositories used as performance extent of a scale-out backup repository.

To enable immutability for tenant backups, the SP changes the type of the backup repository from the Linux repository to the hardened (immutable) repository. To learn more about repositories of this type, see the [Hardened Repository](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository.html?ver=13) section in the Veeam Backup & Replication User Guide.

Before changing the repository type, complete the following prerequisites:

* In the Veeam Backup & Replication console, disable all tenants whose data resides in the Linux repository used as the cloud repository. Make sure related sessions are finalized.

For details, see [Disabling and Enabling Tenant Accounts](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_disable_account.html?ver=120).

* [For a scale-out backup repository] In the Veeam Backup & Replication console, put the Linux backup repository used as performance extent of a scale-out backup repository to the Maintenance mode.

For details, see the [Switching to Maintenance Mode](https://helpcenter.veeam.com/docs/vbr/userguide/sobr_maintenance.html?ver=13) section in the Veeam Backup & Replication User Guide.

To change the repository type from a Linux repository to a hardened repository, do the following:

1. Prepare the Linux server:

1. Open the Backup Infrastructure view. In the inventory pane, select Managed Servers.
2. In the working area, select a Linux server used as a Linux repository and click Edit Server on the ribbon or right-click the server and select Properties.
3. At the SSH Connection step of the wizard, specify the account with non-root permissions you want to use to connect to the Linux server. These credentials must be single-use.

For detailed instructions, see the [Specify Credentials and SSH Settings](https://helpcenter.veeam.com/docs/vbr/userguide/linux_server_ssh.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Use the New Backup Repository wizard to add the hardened repository as a backup repository:

1. Open the Backup Infrastructure view. Click Add Repository on the ribbon.
2. In the Add Backup Repository window, select Direct attached storage > Linux (Hardened Repository).
3. At the Server step of the wizard, select the same Linux server where tenant backups are stored.
4. At the Repository step of the wizard, select the same directory where tenant backups are stored.
5. At the Review step of the wizard, make sure that the Search the repository for existing backups and import them automatically check box is not selected.
6. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

For detailed instructions, see the [Adding Hardened Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_add.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Do not rescan the initial Linux repository after adding the new hardened repository to the SP Veeam Backup & Replication infrastructure. |

1. Point Veeam Backup & Replication at the newly added hardened repository with tenant data. This step differs depending on whether you want to switch a simple backup repository or a performance extent of a scale-out backup repository to a hardened repository.

* [For a simple Linux backup repository] Change backup resource allocation settings in the properties of the tenant account.

1. Open the Cloud Connect view. In the inventory pane, select Tenants.
2. In the working area, right-click the tenant account and select Properties.
3. At the Backup Resources step of the wizard, select the initial cloud repository in the list and click Edit.
4. In the Edit Quota window, select the new hardened repository from the Backup repository list.
5. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

* [For a scale-out backup repository] Change settings of the scale-out backup repository.

1. Open the Backup Infrastructure view. In the inventory pane, click Scale-out Repositories.
2. In the working area, select the scale-out repository and click Edit Scale-out Repository on the ribbon or right-click the scale-out backup repository and select Properties.
3. At the Performance Tier step of the wizard, click Remove to remove the initial Linux repository, and then click Add to add the new hardened repository.
4. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

1. Remove the initial Linux repository from the SP infrastructure.

For details, see the [Removing Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/repo_delete.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. On the Linux server, change permissions for the directory where backups are stored. Specify the account with non-root permissions that you use to connect to the Linux server as the owner of this directory, and the group to which this account belongs.

|  |
| --- |
| chown -R owner:group <dir\_path> |

1. [For a scale-out backup repository] Rescan the backup repository.

For details, see the [Rescanning Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/rescanning_backup_repositories.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Enable the tenant account.

For details, see [Disabling and Enabling Tenant Accounts](cloud_connect_disable_account.md).

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
