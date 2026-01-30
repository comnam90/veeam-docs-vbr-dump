---
title: "Start-VEODRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-veodrestoresession.html"
last_updated: "7/24/2025"
product_version: "13.0.1.1071"
---

# Start-VEODRestoreSession


Short Description

Starts restore sessions to explore backed-up OneDrive items and to perform operations with these items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Explore and perform operations with OneDrive items from backups created by a specific job.

|  |
| --- |
| Start-VEODRestoreSession [-Job] <IVBOJob> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with OneDrive items from a specific restore point.

|  |
| --- |
| Start-VEODRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>] [-RestorePoint] <IVBORestorePoint> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with OneDrive items from the latest restore point.

|  |
| --- |
| Start-VEODRestoreSession [[-Job] <IVBOJob>] [[-Organization] <IVBOOrganization>] [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-LatestState] [-Reason <String>] [<CommonParameters>] |

* Explore and perform operations with OneDrive items from backups created for a specific organization.

|  |
| --- |
| Start-VEODRestoreSession [-Organization] <IVBOOrganization> [-Server <String>] [-Credential <PSCredential>] [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [-Reason <String>] [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the Veeam Backup for Microsoft 365 server and retrieves data on OneDrive items backed up on this server. Within the restore session, you can get backed-up items using the following cmdlets:

* [Get-VEODOrganization](get-veodorganization.md)
* [Get-VEODDocument](get-veoddocument.md)
* [Get-VEODDocumentVersion](get-veoddocumentversion.md)
* [Get-VEODUser](get-veoduser.md)

After you get backed-up items, you can perform the following operations with these items:

* [Restore-VEODDocument](restore-veoddocument.md)
* [Save-VEODDocument](save-veoddocument.md)
* [Send-VEODDocument](send-veoddocument.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a backup job to start a new restore session. You will be able to use the session to perform operations with items backed up by this job. | Accepts the IVBOJob object. To get this object, run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. | True | 0 | True (ByValue) |
| Server | Specifies DNS name or IP address of the Veeam Backup for Microsoft 365 server that backed up items you want to restore. | String | False | Named | False |
| Credential | Specifies credentials that will be used for authenticating to the Veeam Backup for Microsoft 365 server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| Port | Specifies a port number that will be used to connect to the Veeam Backup for Microsoft 365 server.  Default: 9194 | Int32 | False | Named | False |
| ShowDeleted | Defines that deleted items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Default: False  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| ShowAllVersions | Defines that all versions of SharePoint items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Default: False  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason to perform restore operation. | String | False | Named | False |
| Organization | Specifies an organization to start a new restore session. You will be able to use the session to perform operations with items backed up for this organization. | Accepts the IVBOOrganization object. To get this object, run the [Get-VBOO rganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. | False | 0 | True (ByValue) |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with items that this restore point contains. | Accepts the IVBORestorePoint object. To get this object, run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. | True | 0 | True (ByValue) |
| LatestState | Defines that the cmdlet will retrieve items from the latest restore point. If you provide this parameter, you will be able to perform operations with items in the most recent restore state.  Default: False | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveItemRestoreSession](vboonedriveitemrestoresession.md) object that contains the restore session started to perform operations with backed-up OneDrive items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session from Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to retrieve items from a specific restore point created on the srv.tech.local server. The cmdlet will use the default port number (9194) to connect to the Veeam Backup for Microsoft 365 server.  |  | | --- | | $credentials = Get-Credential  $restorepoint = Get-VBORestorePoint  Start-VEODRestoreSession -RestorePoint $restorepoint[0] -Server "srv.tech.local" -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. Save the result to the $restorepoint variable.   The cmdlet will return an array of all restore points created on the srv.tech.local server. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.   1. Run the Start-VEODRestoreSession cmdlet. Specify the following settings:  * Set the $restorepoint[0] variable as the RestorePoint parameter value. * Set srv.tech.local as the Server parameter value. * Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from Latest State

|  |  |
| --- | --- |
| This example shows how to start a restore session to retrieve items from the latest restore point created on the srv.tech.local server. The cmdlet will use the default port number (9194) to connect to the Veeam Backup for Microsoft 365 server.  |  | | --- | | $credentials = Get-Credential  $job = Get-VBOJob -Name "Monthly Backup"  Start-VEODRestoreSession -LatestState -Job $job -Server "srv.tech.local" -Credential $credentials |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable. 2. Run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. Save the result to the $job variable. 3. Run the Start-VEODRestoreSession cmdlet. Specify the following settings:  * Specify the $job variable as the Job parameter value. * Provide the LatestState parameter.  * Set srv.tech.local as the Server parameter value. * Set the $credentials variable as the Credential parameter value. |

Related Commands

* [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80)
* [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)


