---
title: "Get-VBRSQLDatabaseRestoreInterval (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsqldatabaserestoreinterval.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSQLDatabaseRestoreInterval (obsolete)


Short Description

Shows interval of backups available for a selected database.

|  |
| --- |
| Note |
| This cmdlet is no longer supported, use the [Get-VESQLDatabaseRestoreInterval](https://helpcenter.veeam.com/docs/backup/explorers_powershell/get-vesqldatabaserestoreinterval.html?ver=120) cmdlet instead. To learn more about the Get-VESQLDatabaseRestoreInterval cmdlet, see the [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/backup/explorers_powershell/getting_started.html?ver=120). |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSQLDatabaseRestoreInterval -Database <VBRSQLDatabase>  [<CommonParameters>] |

Detailed Description

This cmdlet shows date and time of the first and the last available restore point for a selected database. This is reference information that helps you to select an available restore point.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies the database for which you want to get the intervals. | Accepts the [VBRSQLDatabase](vbrsqldatabase.md) object. To get this object, run the [Get-VBRSQLDatabase](get-vbrsqldatabase.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDatabaseRestoreInterval](vbrdatabaserestoreinterval.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Restore Interval for VM

|  |  |
| --- | --- |
| This example shows how to get the restore interval for the crm\_db VM.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SQL -Name "crm\_db"  Get-VBRSQLDatabase -ApplicationRestorePoint $restorepoint[2] | Get-VBRSQLDatabaseRestoreInterval |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the SQL parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.   The Get-VBRApplicationRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the third restore point in the array).   1. Run the Get-VBRSQLDatabase cmdlet. Set the $restorepoint[2] variable as the ApplicationRestorePoint parameter value. 2. Pipe the cmdlet output to the Get-VBRSQLDatabaseRestoreInterval cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Interval for Specific Database

|  |  |
| --- | --- |
| This example shows how to get the restore interval for the Locations database on the crm\_db VM.  |  | | --- | | $restorepoint = Get-VBRApplicationRestorePoint -SQL -Name "crm\_db"  $locations = Get-VBRSQLDatabase -ApplicationRestorePoint $restorepoint[2] -Name "Locations"  Get-VBRSQLDatabaseRestoreInterval -Database $locations  From                                         To ----                                         -- 02/11/2014 12:33:39 PM                       10/28/2015 12:33:39 PM |  Perform the following steps:   1. Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the SQL parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.   The Get-VBRApplicationRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the third restore point in the array).   1. Run the Get-VBRSQLDatabase cmdlet. Set the $restorepoint[2] variable as the ApplicationRestorePoint parameter value. Specify the Name parameter value. Save the result to the $locations variable. 2. Run the Get-VBRSQLDatabaseRestoreInterval cmdlet. Set the $locations variable as the Database parameter value. |

Related Commands

[Get-VBRSQLDatabase](get-vbrsqldatabase.md)


