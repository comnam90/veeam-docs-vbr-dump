---
title: "Export-VEORPublishedDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/export-veorpublisheddatabase.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Exports a published Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VEORPublishedDatabase [-Database] <VEORPublishedDatabase> [-Path] <String> [-RmanBackupFormat <String>] [-RmanBackupTagName <String>] [-RmanBackupEnableCompression] [-Force] [-ChannelsNumber <Int32>] [<CommonParameters>] |

Detailed Description

This cmdlet exports a published Oracle database as an RMAN backup. The database is exported to the specified path on the machine where the PowerShell session is running.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a published Oracle database that you want to export. | Accepts the [VEORPublishedDatabase](veorpublisheddatabase.md) object. To get this object, run the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet. | True | 0 | True |
| Path | Specifies a target directory. The cmdlet will export the Oracle database to the specified directory. | String | True | 1 | True |
| RmanBackupFormat | Specifies the FORMAT parameter of backed-up Oracle databases. The cmdlet will back up Oracle databases using the specified FORMAT parameter. | String | False | Named | False |
| RmanBackupTagName | Specifies tags of backed-up Oracle databases. The cmdlet will back up Oracle databases using the specified tags. | String | False | Named | False |
| RmanBackupEnableCompression | Defines that the cmdlet will back up Oracle databases with compression.  If you do not specify this parameter, the cmdlet will back up Oracle databases without compression. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will overwrite the existing Oracle database files with the database files from the backup.  If you provide this parameter, the cmdlet will show no prompt before executing the command. Otherwise, the cmdlet will keep the existing version of Oracle database files. | SwitchParameter | False | Named | False |
| ChannelsNumber | Specifies a number of channels that will be used to export Oracle databases.  Default: 4  Permitted value: 1-255. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Exporting Published Oracle Databases

This example shows how to export a published Oracle database as an RMAN backup.

|  |
| --- |
| $session = Get-VEORRestoreSession  $database = Get-VEORPublishedDatabase -Session $session[0] -Name "orcl"  Export-VEORPublishedDatabase -Database $database -Path "C:\Users\Administrator\Desktop\orcl" |

Perform the following steps:

1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Export-VEORPublishedDatabase cmdlet. Set the $database variable as the Database parameter value. Specify the Path parameter value.

Related Commands

* [Get-VEORRestoreSession](get-veorrestoresession.md)
* [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md)

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
