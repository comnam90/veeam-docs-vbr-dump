---
title: "Export-VBRConfiguration (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrconfiguration.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Export-VBRConfiguration (obsolete)


Short Description

Starts configuration backup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using cmdlets from the [Configuration Backup](configuration_backup.md) section. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRConfiguration [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet backs up current configuration of Veeam Backup & Replication server.

With configuration backup, you can store a copy of your host configuration: your virtual infrastructure, jobs configuration, Veeam Backup & Replication settings and other data. In case the Veeam Backup & Replication host is failed or configuration is corrupted, you can restore configuration with this copy.

The configuration backup is job-driven. You can configure settings of the configuration backup job, including schedule, in the main menu of the Veeam backup console. With Veeam PowerShell, you can start a job session but you cannot change the settings.

By default, the configuration backup job runs daily. The resulting backup files are stored to the C:\backup\VeeamConfigBackup\%BackupServer% folder on the Veeam backup default repository.

You cannot restore configuration with Veeam PowerShell. It is recommended to perform the restore operation with Veeam Backup & Replication UI for full functionality.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

This command backs up current configuration of Veeam Backup & Replication host.

|  |
| --- |
| Export-VBRConfiguration |


