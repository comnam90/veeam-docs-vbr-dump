---
title: "Export-VESQLPublishedDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-vesqlpublisheddatabase.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Export-VESQLPublishedDatabase


Short Description

Exports a published Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VESQLPublishedDatabase [-Database] <VESQLPublishedDatabase> [-Path] <String> [-EnableCompression] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet exports a published Microsoft SQL Server database to the specified destination on the machine where the PowerShell session is running.

|  |
| --- |
| Note |
| The published database can only be exported as a .bak file. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a published Microsoft SQL Server database that you want to export. | Accepts the [VESQLPublishedDatabase](vesqlpublisheddatabase.md) object. To get this object, run the [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a full file path. The cmdlet will the export published Microsoft SQL Server database to that file path. | String | True | 1 | False |
| EnableCompression | Defines that the cmdlet will compress the backup file.  Note: This option is available only if your version of Microsoft SQL Server supports the compression option. | SwitchParameter | False | Named | False |
| Force | Defines that if there is a .bak file with the same name on the target location, the cmdlet will overwrite it.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Exporting Published Microsoft SQL Database

This example shows how to export a published Microsoft SQL database.

|  |
| --- |
| $session = Get-VESQLRestoreSession  $database = Get-VESQLPublishedDatabase -Session $session[0] -Name "New SQL Database"  Export-VESQLPublishedDatabase -Database $database -Path "C:\NewPath\File.bak" |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Export-VESQLPublishedDatabase cmdlet. Set the $database variable as the Database parameter value. Specify the Path parameter value.

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md)


