---
title: "VBRNASInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasinstantrecoverymigration.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# VBRNASInstantRecoveryMigration


Contains information about migration to production sessions for file share instant recovery sessions.

Properties

| Property | Type | Description |
| --- | --- | --- |
| GUID | GUID | Migration to production session ID. |
| BackupName | String | Backup name (the same as job name) of the RestorePoint used for NAS instant restore. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Migration to production session state as of the moment of the cmdlet start. |
| RestorePoint | DateTimeLocal | Date and time of creation of the RestorePoint used for NAS instant restore. |
| Platform | CPlatform | Migration target platform. |
| JobType | EDbJobType.FileShareMigration | Job type is always EDbJobType.FileShareMigration. |
| SessionName | String | Name of the migration to production session. |
| NASServer | VBRNASServer | Corresponds to the VBRNASServer parameter. |
| SharePath | String | UNC path of the SMB file share selected as the target for migration to production (not the path of the NAS instant restore). |
| ReplaceAll | Bool | Corresponds to the ReplaceAll parameter. |
| SwitchOverOptions | VBRNASInstantRecoveryMigrationSwitchOverOptions | Corresponds to the VBRNASInstantRecoveryMigrationSwitchOverOptions parameter. |

Related Commands

* [Start-VBRNASInstantRecoveryMigration](start-vbrnasinstantrecoverymigration.md)
* [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md)


