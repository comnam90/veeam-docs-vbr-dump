---
title: "Requirements and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_limitations.html"
last_updated: "1/23/2026"
product_version: "13.0.1.1071"
---

# Requirements and Limitations


For the hardened repository, consider the following requirements and limitations.

Linux Server

|  |
| --- |
| Note |
| Note that these requirements are for manually configured Linux servers. For Linux servers configured using the Veeam Infrastructure Appliance, see [Considerations and Limitations](linux_infrastructure_appliance_byb.md). |

* The role of the hardened repository can be assigned to a Linux machine with local or remotely attached block storage. The machine must meet [system requirements for backup repositories](system_requirements.md#repo).

|  |
| --- |
| Note |
| To reduce the attack surface, use a physical machine with local storage. For RAID configuration, recommendations are the following:   * [For the operating system] RAID 1 on SSDs with at least 100 GB disk space should be used. * [For backup data] RAID 6/60 with write-back cache should be used. At least one disk must be configured for the drive roaming. * Internal disk cache must be disabled. * RAID stripe size should be 128 or 256 KB. |

* The Linux machine file system must support immutable files and extended attributes modified by the [chattr](https://man7.org/linux/man-pages/man1/chattr.1.html) and [setxattr](https://man7.org/linux/man-pages/man2/setxattr.2.html) commands. We recommend using XFS for performance and space efficiency reasons (block cloning support).
* As the hardened repository requires the block storage, you cannot use the following storage types:

+ NFS share or a Linux machine with the mounted NFS volume.
+ ⁠A Linux machine with the mounted SMB (CIFS) volume.

* Depending on the Linux distribution, Veeam services use one of the following Linux firewall managers to operate correctly:

+ firewalld
+ ufw
+ iptables
+ [For IPv6] ip6tables

If none of these firewall managers are installed, make sure that you open all required ports manually. For more information, see [Ports](used_ports.md).

* You must add the Linux machine to the Veeam Backup & Replication console as a managed server. The hardened repository cannot be shared between different Veeam Backup & Replication servers.
* The Linux machine should have redundant network connection.
* Veeam Agent for Linux must not be installed on the Linux server.

Repository

* For the separate directory that you created for the backup data, consider the following:

+ Both owner and group must be the user account you use to connect to the Linux server.
+ Directory permissions must be 0700.
+ Directory must not have a sticky bit.

* To store backup files in a repository, use only a forward incremental backup method with enabled [active full backup](active_full_backup.md) or [synthetic full backup](synthetic_full_backup.md). Once a backup file becomes immutable, it can be merged or deleted only when the immutability time period expires. For this reason, you cannot select a reverse or a forever forward incremental backup method.

* For importing a backup, use VBK backup files. Metadata files of a backup chain (.VBM) cannot be immutable because they are updated on every job pass.
* Veeam Backup & Replication does not support symlinks in the path to the hardened repository.
* Only Veeam Data Mover Service/Veeam Transport Service child processes can run under the root account on a hardened repository.
* Hardened repositories are not visible in the Files view in the Veeam Backup & Replication console.

Immutability Feature

* To use the immutability feature for backup copy jobs, enable the GFS retention policy. For more information, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).

* Do not use the immutability feature for a [Nutanix Mine infrastructure](https://helpcenter.veeam.com/docs/backup/mine/overview.html). As Mine repositories contain thin-provisioned disks, there may be the case when Veeam Backup & Replication uses full storage capacity of a repository and cannot delete backup files from the file system.

Veeam Infrastructure Appliance Hardened Repository

When deploying a Veeam Hardened Repository with Veeam Infrastructure Appliance, consider the following:

* Hardened repositories created with Veeam Infrastructure Appliance must use certificate-based authentication. SSH cannot be used.
* The Host Management console web UI is disabled by default. It is automatically enabled for 24 hours when security officer approval is required. When the request is resolved, the web UI is automatically disabled.
* Multi-factor authentication cannot be disabled on hardened repositories that do not have security officer accounts enabled.
* If security officer accounts are enabled, you must initialize the default security officer account before you add the hardened repository to your Veeam Backup & Replication infrastructure.


