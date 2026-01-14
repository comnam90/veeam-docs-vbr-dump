---
title: "Configuration Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/configuration_backup.html"
last_updated: "4/22/2024"
product_version: "13.0.1.1071"
---

# Configuration Backup

In this article

The configuration backup job is pre-configured in Veeam Backup & Replication. For this reason, you cannot remove the configuration backup job or create a new one.

You can disable the configuration backup job or change its schedule.

In This Section

| Cmdlet | Operation |
| --- | --- |
| [New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md) | Creates the object containing schedule for the configuration backup job |
| [Get-VBRConfigurationBackupJob](get-vbrconfigurationbackupjob.md) | Returns the configuration backup job |
| [Set-VBRConfigurationBackupJob](set-vbrconfigurationbackupjob.md) | Modifies the configuration backup job |
| [Start-VBRConfigurationBackupJob](start-vbrconfigurationbackupjob.md) | Starts the configuration backup job |
| [Set-VBRPSQLDatabaseServerLimits](set-vbrpsqldatabaseserverlimits.md) | Modifies settings of the PostgreSQL instance |

|  |
| --- |
| ![Configuration Backup](images/icon_note.webp) Note: |
| The [Export-VBRConfiguration](export-vbrconfiguration.md) cmdlet that was used in earlier versions for running configuration backup is obsolete. The cmdlet will still work but it is advised to rewrite your scripts using the new cmdlets from this section for added benefits. |

Page updated 4/22/2024

Page content applies to build 13.0.1.1071
