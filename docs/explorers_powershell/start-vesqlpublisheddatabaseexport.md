---
title: "Start-VESQLPublishedDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlpublisheddatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VESQLPublishedDatabaseExport


Short Description

Exports a published Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Export a published database using explicitly provided credentials.

|  |
| --- |
| Start-VESQLPublishedDatabaseExport [-PublishedDatabase] <VESQLDatabasePublish> [-Path] <String> [-EnableCompression] [-Force] [-TargetHost <String>] -TargetGuestCredentials <PSCredential> [<CommonParameters>] |

* Export a published database using a Group Managed Service Account (gMSA) for authentication.

|  |
| --- |
| Start-VESQLPublishedDatabaseExport [-PublishedDatabase] <VESQLDatabasePublish> [-Path] <String> [-EnableCompression] [-Force] [-TargetHost <String>] [-TargetGuestCredentials <PSCredential>] -GMSAAccount <String> [<CommonParameters>] |

Detailed Description

This cmdlet exports a published Microsoft SQL Server database to the specified destination on the machine where the PowerShell session is running.

|  |
| --- |
| Note |
| The published database can only be exported as a .bak file. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| PublishedDatabase | Specifies a publishing session for the Microsoft SQL Server database that you want to export. | Accepts the [VESQLDatabasePublish](vesqldatabasepublish.md) object. To get this object, run the [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a full file path. The cmdlet will export the published Microsoft SQL Server database to that file path. | String | True | 1 | False |
| EnableCompression | Defines that the cmdlet will compress the backup file.  Note: This option is available only if your version of Microsoft SQL Server supports the compression option. | SwitchParameter | False | Named | False |
| Force | Defines that if there is a .bak file with the same name on the target location, the cmdlet will overwrite it.  Note: The cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| GMSAAccount | Specifies the name of the Group Managed Service Account (gMSA). The cmdlet will use this account to authenticate to Microsoft SQL Server on the target machine. | String | True | Named | False |
| TargetHost | Specifies the name of the target Windows server. | String | False | Named | False |
| TargetGuestCredentials | Specifies credentials to authenticate to the target Windows server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabaseExport](vesqldatabaseexport.md) object that contains information about the specified export job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Exporting Published Database

|  |  |
| --- | --- |
| This example shows how to export a published Microsoft SQL Server database to a file on a target Windows server.  |  | | --- | | $publishsession = Get-VESQLDatabasePublish  $guestcreds = Get-Credential  $export = Start-VESQLPublishedDatabaseExport -PublishedDatabase $publishsession[0] -Path "C:\Backup\db1.bak" -TargetGuestCredentials $guestcreds |  Perform the following steps:   1. Run the [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) cmdlet. Save the result to the $publishsession variable.   The cmdlet will return an array of publishing sessions. Note the ordinal number of the necessary publishing session. In this example, it is the first publishing session in the array.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to authenticate to the target Windows server. Save the result to the $guestcreds variable. 2. Run the Start-VESQLPublishedDatabaseExport cmdlet. Specify the following settings:  * Set the $publishsession variable as the PublishedDatabase parameter value. * Specify the Path parameter value. * Set the $guestcreds variable as the TargetGuestCredentials parameter value.   Save the result to the $export variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Exporting Published Database to Remote Server with Compression

|  |  |
| --- | --- |
| This example shows how to export a published Microsoft SQL Server database to a remote Windows server. The export job will run with the following settings:   * The cmdlet will export the database to a remote Windows server (sqlsrv02). * The cmdlet will compress the exported .bak file. * If a .bak file with the same name already exists at the target location, the cmdlet will overwrite it.   |  | | --- | | $publishsession = Get-VESQLDatabasePublish  $guestcreds = Get-Credential  $export = Start-VESQLPublishedDatabaseExport -PublishedDatabase $publishsession[0] -Path "C:\Backup\db1.bak" -TargetHost "sqlsrv02" -TargetGuestCredentials $guestcreds -EnableCompression -Force |  Perform the following steps:   1. Run the [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) cmdlet. Save the result to the $publishsession variable.   The cmdlet will return an array of publishing sessions. Note the ordinal number of the necessary publishing session. In this example, it is the first publishing session in the array.   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to authenticate to the target Windows server. Save the result to the $guestcreds variable. 2. Run the Start-VESQLPublishedDatabaseExport cmdlet. Specify the following settings:  * Set the $publishsession variable as the PublishedDatabase parameter value. * Specify the Path parameter value. * Specify the TargetHost parameter value. * Set the $guestcreds variable as the TargetGuestCredentials parameter value. * Provide the EnableCompression parameter. * Provide the Force parameter.   Save the result to the $export variable to be able to use it with other cmdlets. |

Related Commands

* [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md)

* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 2026-04-24

