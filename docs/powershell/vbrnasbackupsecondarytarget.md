---
title: "VBRNASBackupSecondaryTarget"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasbackupsecondarytarget.html"
last_updated: "1/19/2024"
product_version: "13.0.1.1071"
---

# VBRNASBackupSecondaryTarget


Contains settings of secondary backup repositories.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupRepository | CBackupRepository | Secondary backup repository. |
| CustomRetentionEnabled | Bool | Defines if the custom retention policy is enabled:   * True - Enabled * False - Disabled |
| CustomRetentionType | VBRNASBackupShortTermRetentionType | Retention policy for the secondary repository. |
| CustomRetentionPeriod | Int32 | Time period for the custom retention policy. |
| UseCustomEncryptionKey | Bool | Defines if the custom encryption key is used to encrypt data:   * True - Enabled * False - Disabled |
| CustomEncryptionKey | VBREncryptionKey | Encryption key used to encrypt data. |
| BackupWindowEnabled | Bool | Defines if the backup window option is enabled:   * True - Enabled * False - Disabled |
| BackupWindow | VBRBackupWindowOptions | Backup window settings. |

Related Commands

* [New-VBRNASBackupSecondaryTarget](new-vbrnasbackupsecondarytarget.md)
* [Set-VBRNASBackupSecondaryTarget](set-vbrnasbackupsecondarytarget.md)


