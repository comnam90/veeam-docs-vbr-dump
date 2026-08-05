---
title: "Access to Tenant Backups"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_sp_restore_access.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Access to Tenant Backups


The SP can restore data from tenant backups stored in the cloud repository. The tenant controls the restore scope which is the group of backups the SP can access for restore. Starting from Veeam Backup & Replication version 13.1, the tenant can grant the SP access to both encrypted and unencrypted backups. As a result, the SP can perform recovery operations on behalf of the tenant directly in the SP infrastructure.

The tenant selects the restore scope when connecting to the SP or later when editing the SP connection. The following options are available:

* None. The SP cannot restore data from tenant backups from the cloud repository.
* Unencrypted backups only. The SP can only restore data from unencrypted tenant backups.
* All. The SP can restore data from both unencrypted and encrypted tenant backups.

To enable data restore from encrypted backups, Veeam Backup & Replication on the tenant side releases the encryption password to the SP, so that the SP can decrypt the backup for the restore operation. For details, see [How Access to Tenant Backups Works](#hiw).

For details on how to set up access to tenant backups, see [Specify Backup Storage Settings](cloud_connect_sp_enumerate.md).

When the tenant allows restore from encrypted backups, Veeam Backup & Replication decrypts the eligible backups on the SP side and stores them in decrypted form in the cloud repository. Backups outside the granted scope, or of unsupported types, remain encrypted. The SP cannot restore these backups.

How Access to Tenant Backups Works

After the tenant grants restore access to the SP, Veeam Backup & Replication on the tenant side performs the following steps:

1. Veeam Backup & Replication synchronizes information about all backups with the SP backup server. Synchronization runs when the feature is first enabled and every 15 minutes after that.
2. Veeam Backup & Replication checks what kind of restore access is granted to the SP.
3. Veeam Backup & Replication checks whether the backup is encrypted.
4. If the backup is encrypted, the tenant has allowed data restore from All backups, and the backup type is supported, Veeam Backup & Replication starts the decryption at the end of the synchronization. It releases the encryption password to the SP, which uses it in memory to decrypt the backup data and store it in decrypted form in the cloud repository and configuration database. Otherwise, the backup remains encrypted and is skipped during the SP restore.

Veeam Backup & Replication also starts the decryption when a tenant backup job begins, if a supported encrypted backup on the SP side has not been decrypted yet.

As a result of these operations, the SP has up-to-date information about which tenant backups it can restore, and all eligible encrypted backups are already decrypted on the SP side. Because the backups are already decrypted, the SP can restore them without requesting the encryption password from the tenant. The password is used only in memory during decryption and is never saved to the SP database.

Considerations and Limitations

For restore access to tenant backups, consider the following:

* The restore access settings apply to all backups of the tenant stored in the SP cloud repository.
* If the tenant Veeam backup server runs Veeam Backup & Replication version 13.1 and the SP Veeam backup server runs Veeam Backup & Replication version the Unencrypted backups only and the All option is unavailable. For the tenant to allow the SP to restore data from unencrypted backups, the tenant must select the Allow this Veeam Backup & Replication installation to be managed by the service provider check box when connecting to the SP. For details, see [Specify Cloud Gateway Settings](cloud_connect_sp_settings.md).

It is recommended, however, that the SP and tenant both always install latest hotfixes and updates on the backup server.

* Any updates to the restore scope or encryption password are not applied immediately. They take effect during the next synchronization cycle, which runs every 15 minutes.
* The feature is not supported if the SP uses tenant backup to tape job functionality for the tenant.

In such cases, the tenant cannot enable access to restore data from encrypted backups. The SP can only restore data from unencrypted tenant backups.

If the tenant has already enabled the option to restore data from both unencrypted and encrypted backups for the SP, tenant backup to tape job cannot be started on the SP side.

* The feature is not supported for backups created by Veeam Agent for Linux, Veeam Agent for Mac, Veeam Agent for Oracle Solaris and Veeam Agent for IBM AIX in any operation mode.
* For backups created by Veeam Agent for Microsoft Windows, the following limitations apply:

* The feature is not supported for Veeam Agent for Microsoft Windows operating in the standalone mode.
* The feature is not supported for Veeam Agent for Microsoft Windows version 13.0 or earlier. Only imported or orphaned backups created by these versions are decrypted.

* [For backups encrypted with a KMS key] Only KMS-encrypted backups created after the upgrade to Veeam Backup & Replication version 13.1 are supported. They are sent to the SP in decrypted form. Backups encrypted with a KMS key before the upgrade are skipped, because the tenant has no password to forward to the SP for decryption.
* [For backups encrypted with password loss protection enabled in Veeam Backup Enterprise Manager] The SP cannot decrypt such backups. To make these backups available to the SP, the tenant must map the backup to a backup job, assign a password, and run the job to re-encrypt the backup. After that, the backup works like a regular encrypted backup.
* To use this feature, both the SP and tenant must run Veeam Backup & Replication version 13.1 or later.
* The feature is not supported for backup formats unsupported in Veeam Backup & Replication version 13.0 (or earlier), such as reverse incremental backups or per-VM backups in the legacy (split VM) format.

* If a backup was decrypted on the SP side and then the backup is re-imported into the SP Veeam Backup & Replication configuration database, the backup will be encrypted again. To restore it on the SP side, the tenant must re-release the encryption password.
* If a tenant backup was ever offloaded to the capacity tier or archive tier of a scale-out backup repository, Veeam Backup & Replication skips its decryption on the SP side. This applies even if the backup was later removed from the configuration and re-imported, or if the capacity tier or archive tier was removed from the scale-out backup repository. Once a backup has been offloaded, it is never decrypted.
* Backups that are created after the feature is enabled and are decrypted on the SP side are not offloaded to the capacity tier or archive tier.

Related Topics

* [Connecting to Service Providers](cloud_connect_sp.md)
* [Restoring Data from Tenant Backups](cc_data_restore.md)
* [Data Encryption and Throttling](data_encryption_and_throttling.md)

Page updated 2026-08-04

