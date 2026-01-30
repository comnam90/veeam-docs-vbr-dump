---
title: "VBRNASInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasinstantrecovery.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# VBRNASInstantRecovery


Contains information about active instant restore sessions for file backups.

Properties

| Property | Type | Description |
| --- | --- | --- |
| GUID | GUID | Instant restore session ID. |
| NASBackupName | String | File backup name (the same as job name) of the RestorePoint used for NAS instant restore. |
| RestorePoint | DateTimeLocal | Date and time of creation of the RestorePoint used for NAS instant restore. |
| JobType | EDbJobType.InstantFileShareRestore | Job type is always EDbJobType.InstantFileShareRestore. |
| NASServerId | GUID | ID of the mount server where file backup restore is started. |
| NASServerName | String | Name of the mount server where file backup restore is started. |
| SharePath | String | UNC path of the published SMB file share with the content of the file backup. |
| SessionName | String | Name of the instant restore session. |
| Permissions | VBRNASPermissionSet | [Optional] Permission settings field. Can be not specified only if the session was started from UI. |
| MountState | [EVmssState](enums.md#EVmssState) | Mount state. |
| StateString | String | Mount state in string view (user-friendly). |

Related Commands

* [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md)
* [Start-VBRNASInstantRecovery](start-vbrnasinstantrecovery.md)
* [Stop-VBRNASInstantRecovery](stop-vbrnasinstantrecovery.md)
* [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md)
* [Start-VBRNASInstantRecoveryMigration](start-vbrnasinstantrecoverymigration.md)


