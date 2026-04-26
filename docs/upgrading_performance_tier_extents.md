---
title: "Upgrading Performance Extent to Hardened Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/upgrading_performance_tier_extents.html"
last_updated: "4/24/2026"
product_version: "13.0.1.2067"
---

# Upgrading Performance Extent to Hardened Repository


If you have Linux servers added as performance extents to a scale-out backup repository (SOBR), you can upgrade the extents to hardened repositories. This enables immutability and increases the level of data protection.

Considerations and Limitations

Before you upgrade a performance extent to a hardened repository, consider the following:

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

Upgrading Performance Extent

To upgrade a performance extent to a hardened repository, perform the following steps:

1. In the Veeam Backup & Replication console, disable all backup jobs that use the SOBR. For more information, see [Disabling Jobs](disabling_jobs.md).

|  |
| --- |
| Note |
| If you have Veeam Agent backup jobs managed by Veeam Agent, you need to delete these jobs and configure them again after you switch to the hardened repository. |

1. Switch the Linux server used as a performance extent in the SOBR to maintenance mode. For more information, see [Switching to Maintenance Mode](sobr_maintenance.md).
2. On the Linux server used as performance extent, change permissions for the directory where the backups are stored. Both owner and group must be the account with non-root permissions you use to connect to the Linux extent.

|  |
| --- |
| chown -R owner:group <dir\_path> |

1. Add the Linux server to your backup infrastructure again. For more information, see [Adding Linux Servers](add_linux_server.md).
2. Add the same Linux server to the backup infrastructure as a hardened repository. At the Review step of the wizard, select the Search the repository for existing backups and import them automatically check box. For more information, see [Adding Hardened Repositories](hardened_repository_add.md).

|  |
| --- |
| Important |
| When you add the hardened repository, consider the following:   * You must select the same directory as where tenant backups are stored. * You must not rescan the Linux repository after adding the new hardened repository to your backup infrastructure. * If you work with encrypted backups, you must decrypt them after importing. For more information, see [How Data Decryption Works](decryption_hiw.md). |

1. Go to the Performance Tier step of the Edit Scale-out Repository wizard and remove all Linux extents. Then, add the newly-created hardened repositories. Go to the last step of the wizard, click Apply.
2. Open the Backup Infrastructure view and select Scale-out Repositories in the navigation pane. Right-click the SOBR and select Rescan. Any backup files stored on the added repositories will be automatically imported and displayed in the Veeam Backup & Replication console under the Imported > Backups node.
3. Go to the Jobs node and edit the jobs associated with the SOBR. At the Storage step of the wizard, select the SOBR from the backup repository list. Select Map Backup and map the job to the corresponding imported backup. Finish the wizard to apply changes. Repeat this process for each backup job using the SOBR.
4. Re-enable the jobs that you disabled on the SOBR.
5. Open the Backup Infrastructure view and remove the unused Linux repositories from the backup infrastructure.


