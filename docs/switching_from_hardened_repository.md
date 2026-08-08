---
title: "Switching Hardened Repositories to Linux Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/switching_from_hardened_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Switching Hardened Repositories to Linux Repositories


If you have a Linux hardened repository that already contains backup data, you can enable governance mode immutability for it.

To do this, you change the repository type from a hardened repository to a Linux repository by adding the same server to your backup infrastructure again under a different name. This operation is available for standalone backup repositories and for repositories used as performance extents of a scale-out backup repository.

Considerations and Limitations

Before you switch a hardened repository to a Linux repository, consider the following:

* When you add the Linux repository, you cannot use the same value that was used to add the hardened repository. If you originally used an IP address, you must use a hostname instead. If you originally used a hostname, you must use a different hostname or an IP address instead.

* If you added the hardened repository to your backup infrastructure using an IP address, ensure that a hostname resolving to that IP address is configured in the DNS or the local hosts file (/etc/hosts on a Linux-based backup server and C:\Windows\System32\drivers\etc\hosts on a Microsoft Windows-based backup server).
* If you added the hardened repository to your backup infrastructure using a hostname, ensure that a different hostname resolving to the same IP address is available or you know the IP address of the server.

Switching Standalone Backup Repository

To switch a standalone backup repository to a Linux repository, perform the following steps:

1. In the Veeam Backup & Replication console, disable all backup jobs that use the hardened repository and make sure the related sessions are finalized. For more information, see [Disabling and Deleting Jobs](disabling_jobs.md).
2. Add the Linux server to your backup infrastructure again. Use a different value than the one used to add the hardened repository. For more information, see [Adding Linux Servers](add_linux_server.md).
3. Add the same Linux server to the backup infrastructure as a Linux repository. At the Review step of the wizard, make sure the Search the repository for existing backups and import them automatically check box is cleared. For more information, see [Adding Linux Repositories](linux_repository_add.md).

|  |
| --- |
| Important |
| When you add the Linux repository, consider the following:   * You must select the same directory where the backups are stored. * You must not rescan the hardened repository after adding the new Linux repository to your backup infrastructure. |

1. Go to the Jobs node and edit each backup job associated with the hardened repository. At the Storage step of the wizard, select the newly added Linux repository from the Backup repository list. Click Map backup, select the existing backup chain, and finish the wizard to apply changes.
2. Remove the hardened repository from the backup infrastructure. For more information, see [Removing Backup Repositories](repo_delete.md).
3. Enable the backup jobs that you disabled. For more information, see [Disabling and Deleting Jobs](disabling_jobs.md).

Switching Performance Extent

To switch a performance extent of a scale-out backup repository to a Linux repository, perform the following steps:

1. Switch the hardened repository used as a performance extent of the scale-out backup repository to maintenance mode. For more information, see [Switching to Maintenance Mode](sobr_maintenance.md).
2. Add the Linux server to your backup infrastructure again. Use a different value than the one used to add the hardened repository. For more information, see [Adding Linux Servers](add_linux_server.md).
3. Add the same Linux server to the backup infrastructure as a Linux repository. At the Review step of the wizard, make sure the Search the repository for existing backups and import them automatically check box is cleared. For more information, see [Adding Linux Repositories](linux_repository_add.md).

|  |
| --- |
| Important |
| When you add the Linux repository, consider the following:   * You must select the same directory where the backups are stored. * You must not rescan the hardened repository after adding the new Linux repository to your backup infrastructure. |

1. Go to the Performance Tier step of the Edit Scale-out Repository wizard. Remove the hardened repository, and then add the new Linux repository. Finish the wizard to apply changes.
2. Remove the hardened repository from the backup infrastructure. For more information, see [Removing Backup Repositories](repo_delete.md).
3. Rescan the scale-out backup repository. For more information, see [Rescanning Backup Repositories](rescanning_backup_repositories.md).

Page updated 2026-07-27

