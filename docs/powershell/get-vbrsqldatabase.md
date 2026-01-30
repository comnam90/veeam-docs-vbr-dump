---
title: "Get-VBRSQLDatabase (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsqldatabase.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSQLDatabase (obsolete)


Short Description

Returns Microsoft SQL Server databases in restore point.

|  |
| --- |
| Note |
| This cmdlet is no longer supported, use the [Get-VESQLDatabase](https://helpcenter.veeam.com/docs/backup/explorers_powershell/get-vesqldatabase.html?ver=120) cmdlet instead. To learn more about the Get-VESQLDatabase cmdlet, see the [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/backup/explorers_powershell/getting_started.html?ver=120). |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSQLDatabase -ApplicationRestorePoint <VBRApplicationRestorePoint> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft SQL Server databases in a selected restore point.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ApplicationRestorePoint | Specifies the restore point from which you want to get the databases. | Accepts the [VBRApplicationRestorePoint](vbrapplicationrestorepoint.md) object. To get this object, run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Filters the databases in the restore point by database name. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSQLDatabase](vbrsqldatabase.md)

Examples

Getting Last Restore Point

This example shows how to get the last restore point of the Locations database on the crm\_db VM.

|  |
| --- |
| $crmdb = Get-VBRApplicationRestorePoint -SQL -Name "crm\_db"  $locations = Get-VBRSQLDatabase -ApplicationRestorePoint $crmdb[0] -Name "Locations" |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the SQL parameter. Specify the Name parameter value. Save the result to the $crmdb variable.

The Get-VBRApplicationRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the first restore point in the array).

1. Run the Get-VBRSQLDatabase cmdlet. Set the $crmdb[0] variable as the ApplicationRestorePoint parameter value. Specify the Name parameter value. Save the result to the $locations variable.

Related Commands

[Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md)


