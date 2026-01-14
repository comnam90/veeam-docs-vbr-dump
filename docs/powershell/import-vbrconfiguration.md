---
title: "Import-VBRConfiguration (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrconfiguration.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Import-VBRConfiguration (obsolete)

In this article

Short Description

Imports backup of Veeam Backup & Replication server configuration file.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Import-VBRConfiguration -FileName <String> [-DatabaseName <String>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet imports configuration file of Veeam Backup & Replication that was previously backed up.

With configuration backup, you can store a copy of your host configuration: your virtual infrastructure, jobs configuration, Veeam Backup & Replication settings and other data. You can restore configuration in case the Veeam Backup & Replication host is failed or configuration is corrupted.

By default, configuration backups are stored to the C:\backup\VeeamConfigBackup\%BackupServer% folder on the Veeam backup server.

You can select any configuration file to restore to.

You can restore configuration data to the default Veeam Backup & Replication SQL database or to another database. If you restore to the default database, it is recommended to backup the database first.

Run the [Export-VBRConfiguration (obsolete)](export-vbrconfiguration.md) cmdlet to retrieve and export your current configuration.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| FileName | Specifies the configuration file path you want to restore. | String | True | Named | False |
| DatabaseName | Specifies the name of the database into which data from the configuration backup should be imported.  If not set, the data will be restored to the Veeam Backup & Replication database set by default. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Importing Configuration Backup File to Default Database

|  |  |
| --- | --- |
| This command imports the VEEAMBACKUP-10-06-2021 configuration backup file to the default database.  |  | | --- | | Import-VBRConfiguration -FileName "C:\backup\VeeamConfigBackup\VEEAMBACKUP\VEEAMBACKUP-10-06-2021" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Importing Configuration Backup File to Specific Database

|  |  |
| --- | --- |
| This command imports the VEEAMBACKUP-10-06-2021 configuration backup file to the ConfigBackup database.  |  | | --- | | Import-VBRConfiguration -FileName "C:\backup\VeeamConfigBackup\VEEAMBACKUP\VEEAMBACKUP-10-06-2021" -DatabaseName "ConfigBackup" | |

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
