---
title: "Get-VBRNASBackup (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackup.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackup (obsolete)

In this article

Short Description

Returns backup files created by the file backup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Getting all backup files created by the file backup job.

|  |
| --- |
| Get-VBRNASBackup  [<CommonParameters>] |

* Getting backup files by the file backup job name.

|  |
| --- |
| Get-VBRNASBackup -Name <string[]>  [<CommonParameters>] |

* Getting backup files by the file backup job ID.

|  |
| --- |
| Get-VBRNASBackup -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup files created by the file backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of the file backup job. The cmdlet will return an array of backup files that are created by this file backup job. | String[] | True | Named | False |
| Id | Specifies an array of the file backup IDs. The cmdlet will return an array of backup files that are created by this file backup. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackup object that contains backup files created by the file backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backup Files

|  |  |
| --- | --- |
| This command gets all backup files that are created by the file backup jobs. The cmdlet output will contain details of these backup files.  |  | | --- | | Get-VBRNASBackup  Id                           : 86f24760-ea7e-475a-88ab-1b328e3694f4  Name                         : Reports backup  JobId                        : d9fa21cf-4917-48b8-ad81-53a997923c5f  CreationTime                 : 8/26/2019 8:11:50 AM  LastRestorePointCreationTime : 8/26/2019 8:26:19 AM  IsEncrypted                  : False    Id                           : e5559d89-ca63-48dc-a53b-d9c54b7f2482  Name                         : Transaction backups  JobId                        : d4d289aa-eff8-4983-a5e3-5fd2c7ff7500  CreationTime                 : 8/26/2019 8:29:05 AM  LastRestorePointCreationTime : 8/26/2019 8:29:12 AM  IsEncrypted                  : False | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Files by Name

|  |  |
| --- | --- |
| This command gets backup files that are created by the Reports backup file backup job. The cmdlet output will contain settings of the backup file created by the Reports backup file backup job.  |  | | --- | | Get-VBRNASBackup -Name "Reports backup"  Id                           : 86f24760-ea7e-475a-88ab-1b328e3694f4  Name                         : Reports backup  JobId                        : d9fa21cf-4917-48b8-ad81-53a997923c5f  CreationTime                 : 8/26/2019 8:11:50 AM  LastRestorePointCreationTime : 8/26/2019 8:26:19 AM  IsEncrypted                  : Falseget-vbohelp | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Backup Files by ID

|  |  |
| --- | --- |
| This command gets backup files that are created by the e5559d89-ca63-48dc-a53b-d9c54b7f2482 file backup job. The cmdlet output will contain settings of the backup file crated by the e5559d89-ca63-48dc-a53b-d9c54b7f2482 file backup job.  |  | | --- | | Get-VBRNASBackup -ID e5559d89-ca63-48dc-a53b-d9c54b7f2482  Id                           : e5559d89-ca63-48dc-a53b-d9c54b7f2482  Name                         : Transaction backups  JobId                        : d4d289aa-eff8-4983-a5e3-5fd2c7ff7500  CreationTime                 : 8/26/2019 8:29:05 AM  LastRestorePointCreationTime : 8/26/2019 8:29:12 AM  IsEncrypted                  : False | |

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
