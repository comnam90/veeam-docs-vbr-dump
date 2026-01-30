---
title: "Get-VBRFilesInRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfilesinrestorepoint.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFilesInRestorePoint


Short Description

Returns backup files in a selected restore point.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRFilesInRestorePoint -RestorePoint <COib> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup files in a selected restore point.

With this cmdlet, you can get files in restore points created by the following types of jobs:

* Backup jobs
* Backup copy jobs
* Cloud Director backup jobs
* Veeam Agent for Microsoft Windows backup jobs (only volume level backups)

You can get the list of all files in a selected restore point or look for instances directly by name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore points for which you want to get the list of backup files. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Name | Specifies the array of names of backup files you want to get. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the COIBFileInfo that contains backup files in a selected restore point.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of all Backup Files from Restore Point

|  |  |
| --- | --- |
| This example shows how to get a list of files that are added to the Webservices01 restore point.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "Webservices01"  Get-VBRFilesInRestorePoint -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Run the Get-VBRFilesInRestorePoint cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting List of Backup Files from Latest Restore Point [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the list of files in the last restore point of the Webservices01 backup.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name "Webservices01" | Select-Object -Last 1  Get-VBRFilesInRestorePoint -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Select-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3&viewFallbackFrom=powershell-7) cmdlet. Specify the Last parameter value. Save the result to the $restorepoint variable.  1. Run the Get-VBRFilesInRestorePoint cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Select-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3&viewFallbackFrom=powershell-7)


