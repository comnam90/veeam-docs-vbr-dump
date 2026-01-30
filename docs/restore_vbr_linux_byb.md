---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_linux_byb.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you start the restore process, check the following prerequisites:

* Multi-factor authentication (MFA) for the user account must be disabled before starting the configuration database restore process. To learn how to disable MFA, see [Multi-Factor Authentication](mfa.md).
* Stop all jobs that are currently running. During restore of configuration, Veeam Backup & Replication temporary stops the Veeam Backup Service and jobs.
* On the backup server running Veeam Backup & Replication 13, you can only restore configuration backups created with Veeam Backup & Replication 13.
* Make sure that the certificate chain restored from a configuration backup will successfully pass validation on the target backup server. This precaution is required if the following conditions are met:

1. You want to restore the configuration database of a backup server used in the Veeam Agent management scenario.
2. The backup server whose configuration database you want to restore uses a custom certificate issued by a Certificate Authority instead of the default self-signed certificate to ensure a secure connection in the Veeam Agent management infrastructure.

* If you plan to restore configuration data to the database on another PostgreSQL Server, make sure the account for using Veeam Backup & Replication has sufficient permissions. For more information, see [Permissions](required_permissions.md).
* After you run configuration restore for [capacity tier](capacity_tier.md), Veeam Backup & Replication will put the capacity tier extents into the [Sealed mode](sobr_seal.md). Rescan the backup infrastructure and then remove the extents from the Sealed mode.
* If you use a Veeam Backup & Replication server as a Veeam repository, after restore to a new host this repository will be located in the same file path as it was before the migration.
* If you use Veeam Plug-Ins ([Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9) and so on) and want to restore the configuration database to a new machine, make sure you have the plug-ins installed before the restoration process.
* To restore the configuration database from the backup server with the configured Security Officer account to another backup server, consider the following:

+ The target backup server must also have the configured Security Officer account.
+ In the Veeam Host Management console of the target backup server, a Security Officer must specify a configuration backup passphrase used to encrypt the configuration backup on the previous backup server. For more information, see [Managing Configuration Backup Passphrases](hmc_perform_so_tasks.md#manage_bco_passphrase).


