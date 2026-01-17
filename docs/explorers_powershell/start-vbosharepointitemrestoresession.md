---
title: "Start-VBOSharePointItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vbosharepointitemrestoresession.html"
last_updated: "7/24/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts restore sessions to explore backed-up SharePoint items and to perform operations with these items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Explore and perform operations with SharePoint items from backups created by a specific job.

|  |
| --- |
| Start-VBOSharePointItemRestoreSession [-Job] <IVBOJob> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with SharePoint items from a specific restore point.

|  |
| --- |
| Start-VBOSharePointItemRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>] [-RestorePoint] <IVBORestorePoint> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with SharePoint items from the latest restore point.

|  |
| --- |
| Start-VBOSharePointItemRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>] [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-LatestState] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with SharePoint items from backups created for a specific organization.

|  |
| --- |
| Start-VBOSharePointItemRestoreSession [-Organization] <IVBOOrganization> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the Veeam Backup for Microsoft 365 server and retrieves SharePoint items backed up on this server. Within the restore session, you can get backed-up items using the following cmdlets:

* [Get-VESPOrganization](get-vesporganization.md)
* [Get-VESPSite](get-vespsite.md)
* [Get-VESPList](get-vesplist.md)
* [Get-VESPDocument](get-vespdocument.md)
* [Get-VESPDocumentVersion](get-vespdocumentversion.md)
* [Get-VESPDocumentLibrary](get-vespdocumentlibrary.md)
* [Get-VESPItem](get-vespitem.md)
* [Get-VESPItemAttachment](get-vespitemattachment.md)
* [Get-VESPItemVersion](get-vespitemversion.md)

After you get backed-up items, you can perform the following operations with these items:

* [Export-VESPItem](export-vespitem.md)
* [Restore-VESPItem](restore-vespitem.md)
* [Send-VESPItem](send-vespitem.md)
* [Save-VESPItem](save-vespitem.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a backup job to start a new restore session. You will be able to use the session to perform operations with items backed up by this job. | Accepts the IVBOJob object. To get this object, run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. | True | 0 | True (ByValue) |
| Server | Specifies DNS name or IP address of the Veeam Backup for Microsoft 365 server that backed up items you want to restore. | String | False | Named | False |
| Credential | Specifies credentials that will be used for authenticating to the Veeam Backup for Microsoft 365 server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Port | Specifies a port number that will be used to connect to the Veeam Backup for Microsoft 365 server.  Default: 9194 | Int32 | False | Named | False |
| ShowDeleted | Defines that deleted items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Default: False  Note: With this parameter provided, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| ShowAllVersions | Defines that all versions of SharePoint items will be included in the current session.  If you provide this parameter, you will be able to perform operations with these items. Otherwise, only the latest version of SharePoint items will be available.  Default: False  Note: With this parameter provided, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason to perform restore operation. | String | False | Named | False |
| Organization | Specifies an organization to start a new restore session. You will be able to use the session to perform operations with items backed up for this organization. | Accepts the IVBOOrganization object. To get this object, run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. | False | Named | True (ByValue) |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with items that this restore point contains. | Accepts the IVBORestorePoint object. To get this object, run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. | True | 0 | True (ByValue) |
| LatestState | Defines that the cmdlet will retrieve items from the latest restore point. If you provide this parameter, you will be able to perform operations with items in the most recent restore state.  Default: False | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOSharePointRestoreSession](vbosharepointrestoresession.md) object that contains settings of the restore session started to perform operations with backed-up SharePoint items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session for Backup Job

|  |  |
| --- | --- |
| This example shows how to start a new restore session to retrieve items backed up by a job running on the srv.tech.local server from the latest restore point. To connect to the Veeam Backup for Microsoft 365 server, the default port number (9194) will be used.  |  | | --- | | $credentials = Get-Credential  $job = Get-VBOJob -Name "SharePoint"  Start-VBOSharePointItemRestoreSession -LatestState -Job $job -Server "srv.tech.local" -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Run the Start-VBOSharePointItemRestoreSession cmdlet. Specify the following settings:  * Provide the LatestState parameter.  * Set the $job variable as the Job parameter value. * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to retrieve items from a specific restore point created on the srv.tech.local server. To connect to the Veeam Backup for Microsoft 365 server, the default port number (9194) will be used.  |  | | --- | | $credentials = Get-Credential  $restorepoint = Get-VBORestorePoint  Start-VBOSharePointItemRestoreSession -RestorePoint $restorepoint[0] -Server "srv.tech.local" -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. Save the result to the $restorepoint variable.   The cmdlet will return an array of all restore points created on the srv.tech.local server. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.   1. Run the Start-VBOSharePointItemRestoreSession cmdlet. Specify the following settings:  * Set the $restorepoint[0] variable as the RestorePoint parameter value. * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Restore Session for Backed-Up Microsoft Organization

|  |  |
| --- | --- |
| This example shows how to start a restore session to retrieve the TechCompany organization items backed up on the srv.tech.local server from the latest restore point. To connect to the Veeam Backup for Microsoft 365, the default port number (9194) will be used.  |  | | --- | | $credentials = Get-Credential  $organization = Get-VBOOrganization -Name "TechCompany"  Start-VBOSharePointItemRestoreSession -LatestState -Organization $organization -Server "srv.tech.local" -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $organization variable. 3. Run the Start-VBOSharePointItemRestoreSession cmdlet. Specify the following settings:  * Provide the LatestState parameter. * Set the $organization variable as the Organization parameter value. * Specify the Server parameter value. * Set the $credentials variable as the Credential parameter value. |

Related Commands

* [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80)
* [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80)

Page updated 7/24/2025

Page content applies to build 13.0.1.1071
