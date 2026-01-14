---
title: "Import-VBRBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrbackup.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Import-VBRBackup

In this article

Short Description

Imports Veeam backups to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Import backups from the server.

|  |
| --- |
| Import-VBRBackup -Server <CHost> -FileName <String>  [<CommonParameters>] |

* Import backups from the repository.

|  |
| --- |
| Import-VBRBackup -FileName <String> -Repository <CBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet imports Veeam backups to Veeam Backup & Replication database. You can import Veeam backups that were, for example, created on other Veeam backup servers or stored on a repository that is newly added to the Veeam Backup & Replication console.

The imported backups are registered in Veeam Backup database. You can use them for any restore operation.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the target server where you want to store the imported backups. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| FileName | Specifies the path to the backup you want to import. | String | True | 1 | False |
| Repository | Specifies the repository where backups are located. You can use the parameter for all types of repositories, including CIFS (SMB) Share and deduplicating storage appliance (Dell EMS Data Domain, ExaGrid, HPE StoreOnce). | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | 2 | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackup object that defines imported backups imported to Veeam Backup & Replication database.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Importing Backup from Server

|  |  |
| --- | --- |
| This example shows how to import a backup from the server.  |  | | --- | | $server = Get-VBRServer -Name "Fileserver"  Import-VBRBackup -Server $server -FileName "C:\Backups\SureBackups\SureBackups.vbm" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Import-VBRBackup cmdlet. Set the $server variable as the Server parameter value. Specify the FileName parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Importing Backup from Repository

|  |  |
| --- | --- |
| This example shows how to import a backup from the repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "StoreOnce"  Import-VBRbackup -FileName "storeonce://10.0.0.1:Backup\_Store@/Backup\_Job/Backup\_Job.vbk" -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Import-VBRBackup cmdlet. Specify the Filename parameter value. Set the $repository variable as the Repository parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
