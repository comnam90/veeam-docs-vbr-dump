---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_before_you_begin.html"
last_updated: "11/9/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you start the restore process, check the following prerequisites:

* Make sure the user, who initiates the backup configuration restore process, has the Debug programs policy applied. Otherwise, Veeam Backup & Replication returns the Access is Denied error. To learn how to apply the policy, see [this Veeam KB article](https://www.veeam.com/kb2465).
* Multi-factor authentication (MFA) for the user account must be disabled before launching configuration database restore wizard. To learn how to disable MFA, see [Multi-Factor Authentication](mfa.md).
* Stop all jobs that are currently running. During restore of configuration, Veeam Backup & Replication temporary stops the Veeam Backup Service and jobs.
* Save registry values that you changed or created on the backup server. After restore, you will need to recreate or change the keys manually because the configuration database does not store them.
* Check the version of the backup server. On the backup server running Veeam Backup & Replication 13, you can restore configuration backups created with the following product versions: 13, 12, 11a, 11 and 10a.
* Make sure that the certificate chain restored from a configuration backup will successfully pass validation on the target backup server. This precaution is required if the following conditions are met:

1. You want to restore configuration database of a backup server used in the Veeam Agent management scenario.
2. The backup server whose configuration database you want to restore uses a custom certificate issued by a Certificate Authority instead of the default self-signed certificate to ensure a secure connection in the Veeam Agent management infrastructure.

* If you plan to restore configuration data to the database on another Microsoft SQL Server or PostgreSQL Server, make sure the account for using Veeam Backup & Replication has sufficient permissions. For more information, see [Permissions](required_permissions.md).

* Veeam Backup & Replication supports configuration database migration between different database engines only within the same Veeam Backup & Replication version.

* After you run configuration restore for [capacity tier](capacity_tier.md), Veeam Backup & Replication will put the capacity tier extents into the [Sealed mode](sobr_seal.md). Rescan the backup infrastructure and then remove the extents from the Sealed mode.
* If you use a Veeam Backup & Replication server as a Veeam repository, after restore to a new host this repository will be located in the same file path as it was before the migration.
* If you use Veeam Plug-Ins ([Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7), [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9) and so on) and want to restore the configuration database to a new machine, make sure you have the plug-ins installed before the restoration process.

|  |
| --- |
| Important |
| You can start configuration restore only from the Veeam Backup & Replication console installed locally on the backup server. You cannot start configuration restore from the console installed on a remote machine. |


