---
title: "Step 5. Specify Advanced Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_advanced_mssql.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
---

# Step 5. Specify Advanced Settings


At the Target step of the wizard, click Advanced job settings to configure compression, RPO and notifications settings.

* [Compression and Deduplication](#compr)
* [RPO](#rpo)
* [Notifications](#notif)

Compression and Deduplication

At the Storage tab, define compression and deduplication settings.

By default, Veeam Backup & Replication performs deduplication before storing copied data on the target backup repository. Deduplication provides a smaller size of the resulting backup file but may reduce the job performance.

1. You can disable data deduplication. To do this, clear the Enable inline data deduplication check box.
2. From the Compression level list, choose a compression level to be used: Auto, None, Dedupe-friendly, Optimal, High or Extreme. The recommended level of compression for backup copy jobs is Auto. In this case, Veeam Backup & Replication uses compression settings of the copied backup files. For more information, see [Compression and Deduplication](compression_deduplication.md).

|  |
| --- |
| Note |
| Veeam Backup & Replication does not support data compression for databases encrypted with transparent data encryption (TDE). |

1. To encrypt the content of backup copy files, select the Enable backup file encryption check box. In the Password field, select a password that you want to use for encryption. If you have not created the password beforehand, click Add or use the Manage passwords link to specify a new password. For more information, see [Password Manager](password_manager.md).

If the backup server is not connected to Veeam Backup Enterprise Manager, you will not be able to restore data from encrypted backups in case you lose the password. Veeam Backup & Replication will display a warning about it. For more information, see [Decrypting Data Without Password](decrypt_without_pass.md).

You can select a Key Management System (KMS) server in the Password field. To do this, the KMS server must be added to Veeam Backup & Replication in advance. If you choose to use KMS keys for backup file encryption at this step of the wizard, Veeam Backup & Replication immediately starts communication with the KMS server to retrieve the encryption keys. To learn more, see [Key Management System Keys](kms.md).

|  |
| --- |
| Note |
| When specifying encryption settings, consider the following:   * To enable encryption for an existing backup copy job, you must disable a backup copy job. Otherwise, you cannot reconfigure the Enable backup file encryption check box.   After you enable encryption and enable the backup copy job, Veeam Backup & Replication applies new settings only starting from the next backup session (created manually or by the GFS schedule). The next created backup file will be encrypted with the specified password..   * Encryption is not retroactive. If you enable encryption for an existing job, Veeam Backup & Replication does not encrypt the previous backup chain created with this job. If you want to start a new chain so that the unencrypted previous chain can be separated from the encrypted new chain, follow the scenario described in [this Veeam KB article](https://www.veeam.com/kb1885). |

![Step 5. Specify Advanced Settings](images/plugins_backup_copy_storage.webp)

RPO Monitor

At the RPO Monitor tab, specify RPO warning settings.

Enable the Warn me if backup is not copied within check box and specify the time period in minutes, hours, or days.

If the backup copy is not created within the specified time period, the backup copy job will finish with the Warning status. The countdown starts from the moment when the required backup is finished and ready to be copied.

![Step 5. Specify Advanced Settings](images/plugins_backup_copy_rpo.webp)

Notifications

At the Notifications tab, to specify notification settings for the backup copy job:

1. At the Target step of the wizard, click Advanced.
2. Click the Notifications tab.
3. Select the Send SNMP notifications for this job check box if you want to receive SNMP traps when the job completes successfully. SNMP traps will be sent if you specify global SNMP settings in Veeam Backup & Replication and configure software on recipient's machine to receive SNMP traps. For more information, see [Specifying SNMP Settings](snmp_settings.md).
4. Select the Send email notifications to the following recipients check box if you want to receive notifications by email in case of job failure or success. In the field below, specify a recipient email address. You can enter several addresses separated by a semicolon.
5. Veeam Backup & Replication sends a consolidated email notification once for the specified backup copy interval. Even if the synchronization process is started several times within the interval, for example, due to job retries, only one email notification will be sent.
6. Email notifications will be sent if you configure global email notification settings in Veeam Backup & Replication. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).
7. At the Send at field, specify the time when you want to receive notifications. Note that you will receive a notification on the job status once a day.
8. You can choose to use global notification settings or specify custom notification settings.

* To receive a typical notification for the job, select Use global notification settings. In this case, Veeam Backup & Replication will apply to the job global email notification settings specified for the backup server. For more information, see [Configuring Global Email Notification Settings](general_email_notifications.md).
* To configure a custom notification for a job, select Use custom notification settings specified below. You can specify the following notification settings:

1. In the Subject field, specify a notification subject. You can use the following variables in the subject: %Time% (completion time), %JobName%, %JobResult%, %VmCount% (number of machines in the job) and %Issues% (number of machines in the job that have been processed with the Warning or Failed status).
2. Select the Notify on success, Notify on warning and Notify on error check boxes to receive email notification if data processing within the backup copy interval completes successfully, fails or completes with a warning.

![Step 5. Specify Advanced Settings](images/plugins_backup_copy_notifications.webp)


