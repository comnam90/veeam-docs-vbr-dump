---
title: "Switching from Linux Repository to Hardened Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_sobr_migration_linux.html"
last_updated: "4/23/2026"
product_version: "13.0.1.2067"
---

# Switching from Linux Repository to Hardened Repository


The SP can enable immutability for a Linux repository with tenant data. This allows the SP to increase the level of data protection for tenant backups. This operation is available for simple backup repositories and backup repositories used as a performance extent of a scale-out backup repository.

To enable immutability for tenant backups, the SP changes the type of the backup repository from the Linux repository to the hardened (immutable) repository. To achieve this, the SP must add the same server again under a different name:

* If the Linux repository server was added using an IP address, add the server using a hostname.
* If the Linux repository server was added using a hostname, add the server using a different hostname or using the IP address of the server.

For more information, see [Prerequisites](#prerequisites).

|  |
| --- |
| Important |
| This operation does not apply to repositories deployed with the JeOS (Just Enough Operating System) ISO file for Veeam Infrastructure Appliance. |

To learn more about hardened repositories, see the [Hardened Repository](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository.html?ver=13) section in the Veeam Backup & Replication User Guide.

Prerequisites

Before changing the repository type, complete the following prerequisites:

* If the Linux repository server was added using an IP address, ensure the local hosts file has a hostname set up that points to that IP address (for example /etc/hosts on Linux, C:\Windows\System32\drivers\etc\hosts on Windows) or in DNS.
* If the Linux repository server was added using a hostname, ensure there is either another hostname that points to the same IP address (use hosts file or DNS), or that the IP address of the server is known.
* Make sure that the Linux server you want to use as a hardened repository does not have other roles assigned. For example, the server must not be configured as a mount server, and mount server components must not be installed on the server.

|  |
| --- |
| Important |
| The hardened repository role cannot be assigned to a Linux server that has optional server roles installed. Before proceeding, use the Uninstall-VBRServerComponent cmdlet to remove any installed optional components, such as dell-ddboost-sdk,hpe-catalyst-client, veeam-mount or veeam-mount-server-dependencies. For details, see the [Uninstall-VBRServerComponent](https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrservercomponent.html?ver=13) section in the Veeam PowerShell Reference.  To check which components are installed, open Backup Infrastructure > Managed Servers. In the working area, select the Linux server and click Edit Server on the ribbon or right-click the server and select Properties. Navigate to the Access step, and click Optional components and advanced connection settings. To learn more, see the [Specify Credentials and SSH Settings](https://helpcenter.veeam.com/docs/vbr/userguide/linux_server_ssh.html?ver=13) section in the Veeam Backup & Replication User Guide. |

* On the Linux server, change permissions for the directory where backups are stored. Specify the account with non-root permissions that you use to connect to the Linux server as the owner of this directory, and the group to which this account belongs.

|  |
| --- |
| chown -R owner:group |

For detailed requirements and limitations for a hardened repository, see the [Requirements and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_limitations.html?ver=13) section in the Veeam Backup & Replication User Guide.

* For backup jobs targeting the Linux repository used as a cloud repository, ensure that tenants use forward incremental backup mode with periodic full backups enabled in the job settings.

* For backup copy jobs, ensure that the tenant has a GFS retention policy enabled and configured.

* In the Veeam Backup & Replication console, disable all tenants whose data resides in the Linux repository used as a cloud repository. Make sure related sessions are finalized.

For details, see [Disabling and Enabling Tenant Accounts](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_disable_account.html?ver=120).

* [For a scale-out backup repository] In the Veeam Backup & Replication console, put the Linux backup repository used as a performance extent of a scale-out backup repository to the Maintenance mode.

For details, see the [Switching to Maintenance Mode](https://helpcenter.veeam.com/docs/vbr/userguide/sobr_maintenance.html?ver=13) section in the Veeam Backup & Replication User Guide.

Switching from Linux Repository to Hardened Repository

To change the repository type from a Linux repository to a hardened repository, do the following:

1. Prepare the Linux server:

1. Open the Backup Infrastructure view. In the inventory pane, right-click the Managed Servers node and select Add Server. Alternatively, you can click Add Server on the ribbon.
2. In the Add Server window, select Linux.
3. At the Name step of the wizard, enter a full DNS name or IP address of the Linux server.

Make sure to use a different value than the one used when adding the Linux repository server, for example, if you used an IP address before, enter a hostname now.

|  |
| --- |
| Note |
| Note that you can use IPv6 addresses only if IPv6 communication is enabled. For details, see the [IPv6 Support](https://helpcenter.veeam.com/docs/vbr/userguide/ipv6.html?ver=13) section in the Veeam Backup & Replication User Guide. |

1. Complete the remaining steps of the wizard.

For detailed instructions, see the [Adding Linux Servers Using Console](https://helpcenter.veeam.com/docs/vbr/userguide/add_linux_server_console.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. At the SSH Connection step of the wizard, specify the account permissions you want to use to connect to the Linux server. Select Single-use credentials for hardened repository.

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

|  |
| --- |
| Note |
| Do not change the Cloud repository name. |

1. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

* [For a scale-out backup repository] Change settings of the scale-out backup repository.

1. Open the Backup Infrastructure view. In the inventory pane, click Scale-out Repositories.
2. In the working area, select the scale-out repository and click Edit Scale-out Repository on the ribbon or right-click the scale-out backup repository and select Properties.
3. At the Performance Tier step of the wizard, click Remove to remove the initial Linux repository, and then click Add to add the new hardened repository.
4. Proceed to the Summary step of the wizard and click Finish to exit the wizard.

1. Remove the initial Linux repository from the SP infrastructure.

For details, see the [Removing Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/repo_delete.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. [For a scale-out backup repository] Rescan the backup repository.

For details, see the [Rescanning Backup Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/rescanning_backup_repositories.html?ver=13) section in the Veeam Backup & Replication User Guide.

1. Enable the tenant account.

For details, see [Disabling and Enabling Tenant Accounts](cloud_connect_disable_account.md).

After you switch repositories, the existing backups will become immutable on the next backup job run.

What You Do Next

[For a simple Linux backup repository] After you switch from a Linux repository to a hardened repository, tenants must clone existing jobs and map the cloned jobs to the existing cloud backups to continue using the same backup chains. Otherwise, only newly created jobs will run successfully, and existing jobs will fail.

To map the existing backup chain, do the following:

1. In the Veeam Backup & Replication console, select the existing backup job and click Clone. For details, see the [Cloning Jobs](https://helpcenter.veeam.com/docs/vbr/userguide/rescanning_backup_repositories.html?ver=13) section in the Veeam Backup & Replication User Guide.
2. Select the cloned backup job and click Edit. For details, see the [Editing Job Settings](https://helpcenter.veeam.com/docs/vbr/userguide/editing_jobs_hv_web.html?ver=13) section in the Veeam Backup & Replication User Guide.
3. At the Storage step of the wizard, click Map backup and select the existing backup chain to which you want to map the cloned backup job.
4. When prompted that the selected backup is already used by another job, confirm the warning.
5. Delete the original job. For details, see the [Deleting Backup Jobs](https://helpcenter.veeam.com/docs/vbr/userguide/rescanning_backup_repositories.html?ver=13) section in the Veeam Backup & Replication User Guide.


