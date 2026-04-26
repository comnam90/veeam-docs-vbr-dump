---
title: "Upgrading or Switching Linux Repositories to Hardened Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/switching_from_linux_repository.html"
last_updated: "4/24/2026"
product_version: "13.0.1.2067"
---

# Upgrading or Switching Linux Repositories to Hardened Repositories


If you have a standalone Linux server added to your backup infrastructure as a backup repository, you can upgrade it to a hardened repository. This enables immutability and increases the level of data protection.

Considerations and Limitations

Before you upgrade a Linux repository to a hardened repository, consider the following:

* A Veeam Infrastructure Appliance used as a backup repository cannot be upgraded to a hardened repository.
* A Linux repository with the mount server role cannot be upgraded to a hardened repository.
* A Linux repository cannot be upgraded to a hardened repository if any of the following optional packages are installed:

* StoreOnceLibrary
* DataDomainLibrary
* NfsGateway
* CifsGateway
* GuestInteractionProxy
* MountTarget
* SnapDiffV3
* ApplicationBackupRepository

|  |
| --- |
| Important |
| To check which packages are installed, open Backup Infrastructure > Managed Servers. Select the Linux server and click Edit Server. Navigate to the Access step, and click Optional components and advanced connection settings. To remove any installed packages, use the [Uninstall-VBRServerComponent](https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrservercomponent.html?ver=13) cmdlet. |

* When you add the hardened repository, you cannot use the same value that was used to add the Linux repository. If you originally used a hostname, you must use a different hostname or an IP address instead. Likewise, if you used an IP address, you must use a hostname.

* If you added the Linux repository to your backup infrastructure using an IP address, ensure that a hostname resolving to that IP address is configured in the DNS or the local hosts file (/etc/hosts on a Linux-based backup server and C:\Windows\System32\drivers\etc\hosts on a Microsoft Windows-based backup server).
* If you added the Linux repository to your backup infrastructure using a hostname, ensure that a different hostname resolving to the same IP address is available or you know the IP address of the server.

Upgrading Linux Repository

To upgrade a Linux repository to a hardened repository, perform the following steps:

1. On the Linux server, change permissions for the directory where backups are stored. Both owner and group must be the account with non-root permissions you use to connect to the Linux server.

|  |
| --- |
| chown -R owner:group <dir\_path> |

1. Disable all backup jobs that use this Linux repository. For more information, see [Disabling and Deleting Jobs](disabling_jobs.md).
2. In the Veeam Backup & Replication console or Web UI, add the server to your backup infrastructure again. For more information, see [Adding Linux Servers](add_linux_server.md).
3. Add the same Linux server to the backup infrastructure as a hardened repository. At the Review step of the wizard, select the Search the repository for existing backups and import them automatically check box. For more information, see [Adding Hardened Repositories](hardened_repository_add.md).

|  |
| --- |
| Important |
| When you add the hardened repository, consider the following:   * You must select the same directory as where tenant backups are stored. * You must not rescan the Linux repository after adding the new hardened repository to your backup infrastructure. * If you work with encrypted backups, you must decrypt them after importing. For more information, see [How Data Decryption Works](decryption_hiw.md). |

1. Go to the Jobs node and edit the job associated with the Linux repository. At the Storage step of the wizard, select the hardened repository from the Backup repository list. Click Map backup and specify imported backups from the previous step. Finish the wizard to apply changes.
2. Delete any jobs associated with the Linux repository.
3. Open the Backup Infrastructure view and remove the unused Linux repositories from the backup infrastructure.


