---
title: "Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_advanced_storage_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Storage Settings


To specify storage settings for the backup policy:

1. Open the Advanced Settings window at one of the following steps of the wizard:

* Storage — if you have selected to save backup files in a Veeam backup repository. Click Change default advanced settings.

* Local Storage — if you have selected to save backup files in a local storage of a Veeam Agent computer. Click Configure advanced settings.
* Shared Folder — if you have selected to save backup files in a network shared folder. Click Configure advanced settings.

1. In the Advanced Settings window, go to the Storage tab.
2. Under Data Reduction, from the Compression level drop-down list, select a compression level for the backup: None, Dedupe-friendly, Optimal, High or Extreme. To learn more about the compression levels, see the [Data Compression](https://helpcenter.veeam.com/docs/agentforwindows/userguide/compression_deduplication.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.
3. From the Storage optimization drop-down list, select the size of data blocks: 4 MB, 1 MB, 512 KB, or 256 KB. Veeam Agent for Microsoft Windows will use data blocks of the chosen size to optimize the size of backup files and job performance.

|  |
| --- |
| ![Storage Settings](images/icon_note.webp)NOTE |
| If you change the storage optimization settings for the backup policy, new settings will not have any effect on previously created files in the chain. They will be applied to new files created after the settings were changed.  To apply new storage optimization settings, you must create an active full backup after you change storage optimization settings. Veeam Backup & Replication will use the new block size for the active full backup and subsequent backup files in the backup chain. To learn about the active full backup, see [Performing Active Full Backup](agent_policy_active_full.md). |

1. To encrypt the content of backup files, under Encryption, turn on the Enable backup file encryption toggle. From the Password drop-down list, select a password that you want to use for encryption. If you have not created the password beforehand, click Add to specify a new password. For more information, see [Password Manager](password_manager.md).

If the backup server is not connected to Veeam Backup Enterprise Manager, you will not be able to restore data from encrypted backups in case you lose the password. Veeam Backup & Replication will display a Loss protection disabled warning under the Password field. For more information, see [Decrypting Data Without Password](decrypt_without_pass.md).

|  |
| --- |
| ![Storage Settings](images/icon_note.webp)NOTE |
| Consider the following:   * If you plan to encrypt the content of backup files, consider the limitations listed in the [Data Encryption Limitations](#encrypt_limits) subsection. * You must encrypt the backup policy if you want to back up data to the Veeam Data Vault storage. * You cannot use Key Management System (KMS) keys for data encryption with a Veeam Agent backup policy. To be able to use KMS keys, create a [backup job managed by the backup server](agent_job_create_win_web.md).   To learn more about KMS keys, see [Key Management System Keys](kms.md). |

[![Specify Storage Settings](images/agent_policy_settings_storage_web.webp)](images/agent_policy_settings_storage_web.webp "Specify Storage Settings")

Data Encryption Considerations and Limitations

If you plan to encrypt the content of the backup files, consider the following:

* Data encryption settings for Veeam Agent backup policies configured in Veeam Backup & Replication are stored in the Veeam Backup & Replication database.

For backup policies targeted at a Veeam backup repository, all data encryption operations are performed in Veeam Backup & Replication. Encryption settings are passed to the Veeam Agent computer only in case this computer is added to a backup policy targeted at a local drive of a protected computer or at an SMB network shared folder. Veeam Backup & Replication passes encryption settings when applying the backup policy to a protected computer.

* If you change a password for data encryption for an existing backup policy targeted at a Veeam backup repository without changing other backup policy settings, the process of applying the backup policy to a protected computer completes with a notification informing that the backup policy was not modified. This happens because data encryption settings for backup policies targeted at a Veeam backup repository are saved to the Veeam Backup & Replication database and are not passed to a Veeam Agent computer.
* If you enable or disable encryption for an existing Veeam Agent backup, during the next job session Veeam Agent for Microsoft Windows will create a full backup file. The created full backup file and subsequent incremental backup files in the backup chain will be encrypted with the specified password.
* Encryption is not retroactive. If you enable encryption for an existing backup policy, Veeam Agent for Microsoft Windows will encrypt the backup chain starting from the next restore point created with this policy.
* [For backup policies targeted at a local drive or network shared folder] When you enable data encryption for a backup policy, Veeam Backup & Replication uses the specified password to encrypt backups of all Veeam Agent computers added to the backup policy. A Veeam Agent computer user can restore data from the backup of this computer without providing a password to decrypt backup. To restore data from a backup of another computer in this backup policy, a user must provide a password specified in the backup policy settings.

This scenario differs from the same scenario in earlier versions of Veeam Backup & Replication where all backups created for Veeam Agent computers in the backup policy could be accessed from any computer in the backup policy without providing a password.

To learn more about data encryption in Veeam Backup & Replication, see [Data Encryption](data_encryption.md).

Page updated 2026-07-16

