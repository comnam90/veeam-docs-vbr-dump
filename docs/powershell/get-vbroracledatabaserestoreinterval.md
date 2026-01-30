---
title: "Get-VBROracleDatabaseRestoreInterval (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbroracledatabaserestoreinterval.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBROracleDatabaseRestoreInterval (obsolete)


Short Description

Shows interval of backups available for a selected database.

|  |
| --- |
| Note |
| This cmdlet is no longer supported, use the [Get-VEORDatabaseRestoreInterval](https://helpcenter.veeam.com/docs/backup/explorers_powershell/get-veordatabaserestoreinterval.html?ver=120) cmdlet instead. To learn more about the Get-VEORDatabaseRestoreInterval cmdlet, see the [Veeam Explorers PowerShell Reference](https://helpcenter.veeam.com/docs/backup/explorers_powershell/getting_started.html?ver=120). |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBROracleDatabaseRestoreInterval -Database <VBROracleDatabase>  [<CommonParameters>] |

Detailed Description

This cmdlet shows the oldest and the most recent points in time (UTC) presenting the interval available for database restore. If you have database archived logs backed up appropriately, you will be able to restore the database to the necessary point in time within that interval.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies the database for which you want to get the intervals. | Accepts the [VBROracleDatabase](vbroracledatabase.md) object. To get this object, run the [Get-VBROracleDatabase](get-vbroracledatabase.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBROracleDatabaseRestoreInterval](vbroracledatabaserestoreinterval.md)

Examples

Getting Available Restore Interval for Database

This example shows how to get the available restore interval for the Products database in the chosen restore point of the oracle\_prod VM.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -Oracle -Name "oracle\_prod"  $products = Get-VBROracleDatabase -ApplicationRestorePoint $restorepoint[2] -Name "Products"  Get-VBROracleDatabaseRestoreInterval -Database $products  From                                         To ----                                         -- 02/11/2014 12:33:39 PM                       10/28/2015 12:33:39 PM |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md) cmdlet. Provide the Oracle parameter. Specify the Name parameter value. Save the result to the $restorepoint variable.
2. Run the [Get-VBROracleDatabase](get-vbroracledatabase.md) cmdlet. Set the $restorepoint[2] variable as the ApplicationRestorePoint parameter value. Specify the Name parameter value. Save the result to the $products variable.
3. Run the Get-VBROracleDatabaseRestoreInterval cmdlet. Set the $products variable as the Database parameter value.

Related Commands

[Get-VBROracleDatabase](get-vbroracledatabase.md)


