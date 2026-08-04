---
title: "Switching from Linux Hardened Repository to Linux Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_sobr_migration_linux_hardened.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Switching from Linux Hardened Repository to Linux Repository


The SP can enable governance mode immutability for a Linux hardened repository with tenant data. This operation is available for simple backup repositories and backup repositories used as a performance extent of a scale-out backup repository.

To enable governance mode immutability for tenant backups, the SP changes the type of the backup repository from the Linux hardened repository to the Linux repository. To achieve this, the SP must add the same server again under a different name:

* If the Linux hardened repository server was added using an IP address, add the server using a hostname.
* If the Linux hardened repository server was added using a hostname, add the server using a different hostname or using the IP address of the server.

For more information, see [Prerequisites](#prerequisites).

Prerequisites

Before changing the repository type, complete the following prerequisites:

* If the Linux hardened repository server was added using an IP address, ensure the local hosts file has a hostname set up that points to that IP address (for example /etc/hosts on Linux, C:\Windows\System32\drivers\etc\hosts on Windows) or in DNS.
* If the Linux hardened repository server was added using a hostname, ensure there is either another hostname that points to the same IP address (use hosts file or DNS), or that the IP address of the server is known.
* In the Veeam Backup & Replication console, disable all tenants whose data resides in the Linux hardened repository used as a cloud repository. Make sure related sessions are finalized.

For details, see [Disabling and Enabling Tenant Accounts](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_disable_account.html?ver=13).

* [For a scale-out backup repository] In the Veeam Backup & Replication console, put the Linux hardened backup repository used as a performance extent of a scale-out backup repository to the Maintenance mode.

For details, see the [Switching to Maintenance Mode](https://helpcenter.veeam.com/docs/vbr/userguide/sobr_maintenance.html?ver=13) section in the Veeam Backup & Replication User Guide.

Switching from Linux Hardened Repository to Linux Repository

To change the repository type from a Linux hardened repository to a Linux repository, do the following:

1. Prepare the Linux server:

1. Open the Backup Infrastructure view. In the inventory pane, right-click the Managed Servers node and select Add Server. Alternatively, you can click Add Server on the ribbon.
2. In the Add Server window, select Linux.
3. At the Name step of the wizard, enter a full DNS name or IP address of the Linux server.

Make sure to use a different value than the one used when adding the hardened repository server, for example, if you used an IP address before, enter a hostname now.

|  |
| --- |
| Note |
| Note that you can use IPv6 addresses only if IPv6 communication is enabled. For details, see the [IPv6 Support](https://helpcenter.veeam.com/docs/vbr/userguide/ipv6.html?ver=13) section in the Veeam Backup & Replication User Guide. |

1. Complete the remaining steps of the wizard.

For detailed instructions, see the [Adding Linux Servers Using Console](https://helpcenter.veeam.com/docs/vbr/userguide/add_linux_server_console.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. At the SSH Connection step of the wizard, specify the account permissions you want to use to connect to the Linux server.

For detailed instructions, see the [Specify Credentials and SSH Settings](https://helpcenter.veeam.com/docs/vbr/userguide/linux_server_ssh.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Use the New Backup Repository wizard to add the hardened repository as a backup repository:

1. Open the Backup Infrastructure view. Click Add Repository on the ribbon.
2. In the Add Backup Repository window, select Direct attached storage > Linux.
3. At the Server step of the wizard, select the Linux server you added in step 1.
4. At the Repository step of the wizard, select the same directory where tenant backups are stored.
5. At the Review step of the wizard, make sure that the Search the repository for existing backups and import them automatically check box is not selected. Note that the option to import backups is not available for service providers.
6. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

For detailed instructions, see the [Adding Hardened Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_add.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Do not rescan the initial Linux hardened repository after adding the new non-hardened repository to the SP Veeam Backup & Replication infrastructure. |

1. Point Veeam Backup & Replication at the newly added Linux repository with tenant data. This step differs depending on whether you want to switch a simple backup repository or a performance extent of a scale-out backup repository to a hardened repository.

* [For a simple Linux backup repository] Change backup resource allocation settings in the properties of the tenant account.

1. Open the Cloud Connect view. In the inventory pane, select Tenants.
2. In the working area, right-click the tenant account and select Properties.
3. At the Backup Resources step of the wizard, select the initial cloud hardened repository in the list and click Edit.
4. In the Edit Quota window, select the new non-hardened repository from the Backup repository list.

|  |
| --- |
| Note |
| Do not change the Cloud repository name. |

1. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

* [For a scale-out backup repository] Change settings of the scale-out backup repository.

1. Open the Backup Infrastructure view. In the inventory pane, click Scale-out Repositories.
2. In the working area, select the scale-out repository and click Edit Scale-out Repository on the ribbon or right-click the scale-out backup repository and select Properties.
3. At the Performance Tier step of the wizard, click Remove to remove the initial Linux hardened repository, and then click Add to add the new Linux repository.
4. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

1. Remove the initial Linux hardened repository from the SP infrastructure.

For details, see the [Removing Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/repo_delete.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. [For a scale-out backup repository] Rescan the backup repository.

For details, see the [Rescanning Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/rescanning_backup_repositories.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Enable the tenant account.

For details, see [Disabling and Enabling Tenant Accounts](cloud_connect_disable_account.md).

Page updated 2026-07-29

