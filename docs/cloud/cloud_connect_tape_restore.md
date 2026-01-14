---
title: "cloud_connect_tape_restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_tape_restore.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication offers the following scenarios for restore of tenant data from tape:

* Restore to the original location. In this scenario, Veeam Backup & Replication restores tenant backups to the original cloud repository. The existing backups are overwritten. After restore, Veeam Backup & Replication maps tenant jobs to the restored backup chains.

* Restore to a new location. In this scenario, Veeam Backup & Replication restores tenant backups to another cloud repository specified by the SP. This option may be useful if you do not want to overwrite all tenant backups in the original cloud repository.
* Export backup files to disk. In this scenario, Veeam Backup & Replication restores tenant backups to a specified folder located on a server in the SP Veeam backup infrastructure.

|  |
| --- |
| Note |
| If the tenant backup resides in capacity tier, and immutability is enabled for data blocks in capacity tier, you cannot use this backup to restore data to the original location. If you restore data from this backup to a new location, and specify the same original repository and new repository, Veeam Backup & Replication will automatically keep the original tenant data. You cannot choose to overwrite the original data with backed-up data from tape. |

The SP can restore data of one tenant or several tenants simultaneously. The SP can restore all tenant data backed-up by a tenant backup to tape job or choose what data to restore. To do this, the SP can select for restore the following objects:

* Tenant
* Cloud repository
* Tenant job that created backup in the cloud repository

|  |
| --- |
| Tip |
| To restore tenant data from tape, the SP can also pass the tape media that contains tenant data to the tenant. In this case, the tenant can add the tape media to their Veeam backup infrastructure and use the Veeam backup console to perform regular restore operations from tape. To learn more, see the [Tape Devices Support](https://helpcenter.veeam.com/docs/vbr/userguide/tape_device_support.html?ver=13) section in the Veeam Backup & Replication User Guide. |

Related Tasks

[Restoring Tenant Data from Tape](cc_backup_to_tape_restore.md)

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
