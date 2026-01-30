---
title: "Backup Copy Modes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_modes.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Backup Copy Modes


Veeam Backup & Replication offers two backup copy modes:

* Immediate copy

In the immediate copy mode, Veeam Backup & Replication copies restore points as soon as they appear in a source backup repository. Veeam Backup & Replication copies only restore points created by source backup jobs (backup jobs that you select when configuring a backup copy job). Veeam Backup & Replication can also copy transaction log backups if you enable this capability in job settings.

The immediate copy mode is supported for the following backup types:

* Backups of VMware vSphere and Microsoft Hyper-V VMs created by Veeam Backup & Replication.

* Backups created by Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for IBM AIX, Veeam Agent for Oracle Solaris and Veeam Agent for Mac operating in the standalone or managed mode.

* Backups created by Veeam Plug-Ins for Enterprise Applications (Oracle RMAN, SAP HANA, SAP on Oracle).

* Backups created by Veeam Plug-In for Proxmox VE.

* Backups created by Veeam Plug-In for Nutanix AHV.
* Backups created by Veeam Backup for OLVM and RHV\*.
* Backups created by Veeam Backup for AWS.
* Backups created by Veeam Backup for Microsoft Azure.
* Backups created by Google Cloud.
* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13).

\* - Available on Microsoft Windows-based backup server.

* Periodic copy

In the periodic copy mode, Veeam Backup & Replication copies the latest source restore point according to schedule specified in backup copy job settings. Veeam Backup & Replication copies only restore points created by source backup jobs (backup jobs that you select when configuring a backup copy job).

The periodic copy mode is supported for the following backup types:

* Backups of VMware vSphere and Microsoft Hyper-V VMs created by Veeam Backup & Replication.
* Backups created by Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for IBM AIX, Veeam Agent for Oracle Solaris and Veeam Agent for Mac operating in the standalone or managed mode.

* Backups created by Veeam Plug-In for Proxmox VE.

* Backups created by Veeam Plug-In for Nutanix AHV.
* Backups created by Veeam Backup for OLVM and RHV\*.
* Backups created by Veeam Backup for AWS.
* Backups created by Veeam Backup for Microsoft Azure.
* Backups created by Google Cloud.
* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13).

\* - Available on Microsoft Windows-based backup server.

|  |
| --- |
| Note |
| [For Veeam Backup & Replication on Windows] Periodic backup copy jobs created in Veeam Backup & Replication 11 or earlier are deprecated.  If you want to upgrade Veeam Backup & Replication to version 13, you must upgrade the backup chain format of such jobs beforehand, as described in section [Upgrading Backup Chain Formats](backup_copy_change_type.md). |

Changing Backup Copy Modes

Veeam Backup & Replication allows you to change the selected backup copy mode by editing backup copy job settings.

|  |
| --- |
| Important |
| The periodic copy mode does not support processing of transaction log backups. Processing of transaction log backups must be turned off before changing the immediate copy mode to the periodic copy mode. |

[For Windows-based backup server] If you want to change the selected backup copy mode for a backup copy job created in earlier versions of Veeam Backup & Replication, it must have the per-machine backup with separate metadata files format. If a backup copy job has the per-machine backup with single metadata file format, you must upgrade its backup chain format to per-machine with separate metadata files or detach backups to start a new backup chain. For more information, see [Upgrading Backup Chain Formats](backup_copy_change_type.md).


