---
title: "start-vboteamsitemrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vboteamsitemrestoresession.html"
last_updated: "7/24/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts restore sessions to explore backed-up Microsoft Teams objects and to perform operations with these items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Explore or restore Microsoft Teams objects from the latest restore point.

|  |
| --- |
| Start-VBOTeamsItemRestoreSession [-LatestState] [-Job <IVBOJob>] [-Organization <IVBOOrganization>] [-ShowDeleted] [-ShowAllVersions] [<CommonParameters>] |

* Explore or restore Microsoft Teams objects from the specified restore point.

|  |
| --- |
| Start-VBOTeamsItemRestoreSession -RestorePoint <IVBORestorePoint> [-Job <IVBOJob>] [-Organization <IVBOOrganization>] [-ShowDeleted] [-ShowAllVersions] [<CommonParameters>] |

* Explore or restore Microsoft Teams objects remotely.

|  |
| --- |
| Start-VBOTeamsItemRestoreSession -Server <String> -Credential <PSCredential> [-Port <Int32>] [-ShowDeleted] [-ShowAllVersions] [<CommonParameters>] |

Detailed Description

This cmdlet establishes a connection to the Veeam Backup for Microsoft 365 server and retrieves Microsoft Teams objects backed up on this server. Within the restore session, you can get backed-up Microsoft Teams objects using the following cmdlets:

* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETTeamMember](get-vetteammember.md)
* [Get-VETChannel](get-vetchannel.md)
* [Get-VETPost](get-vetpost.md)
* [Get-VETFile](get-vetfile.md)
* [Get-VETOtherTab](get-vetothertab.md)

After you get backed-up Microsoft Teams objects, you can perform the following operations with these objects:

* [Export-VETPost](export-vetpost.md)
* [Restore-VETItem](restore-vetitem.md)
* [Send-VETItem](send-vetitem.md)
* [Save-VETItem](save-vetitem.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LatestState | Defines that the cmdlet will retrieve items from the latest restore point in the backup.  Default: False | SwitchParameter | True | Named | False |
| Job | Specifies a backup job to start a new restore session. You will be able to use the session to perform operations with items backed up by this job. | Accepts the IVBOJob object. To get this object, run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. | False | Named | True (ByValue) |
| Organization | Specifies an organization to start a new restore session. You will be able to use the session to perform operations with items backed up for this organization. | Accepts the IVBOOrganization object. To get this object, run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. | False | Named | True (ByValue) |
| ShowDeleted | Defines that deleted items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Default: False  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| ShowAllVersions | Defines that all versions of Microsoft Teams items will be included in the current session. If you provide this parameter, you will be able to perform operations with these items.  Default: False  Note: If you provide this parameter, the amount of data returned by cmdlets within the current session may significantly increase. | SwitchParameter | False | Named | False |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with items that this restore point contains. | Accepts the IVBORestorePoint object. To get this object, run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. | True | Named | True (ByValue) |
| Server | Specifies DNS name or IP address of the Veeam Backup for Microsoft 365 server that backed up items that you want to restore. | String | True | Named | False |
| Credential | Specifies credentials that will be used for authenticating to the Veeam Backup for Microsoft 365 server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | True | Named | False |
| Port | Specifies a port number that will be used to connect to the Veeam Backup for Microsoft 365 server. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOTeamsRestoreSession](vboteamsrestoresession.md) object that contains the restore session started to perform operations with backed-up Microsoft Teams objects.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session from Latest Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to perform operations with Microsoft Teams objects. The restore session will start with the following settings:   * The cmdlet will retrieve data from a backup at the state of the latest restore point. * The cmdlet will start a restore session only for backups associated with the ABC organization.     |  | | --- | | $org = Get-VBOOrganization -Name "ABC"  Start-VBOTeamsItemRestoreSession -LatestState -Organization $org |  Perform the following steps:   1. Run the [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $org variable. 2. Run the Start-VBOTeamsItemRestoreSession cmdlet. Provide the LatestState parameter. Set the $org variable as the Organization parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a restore session to perform operations with Microsoft Teams objects. The restore session will start with the following settings:   * The cmdlet will retrieve data from a backup at the state of the selected restore point. * The cmdlet will start a restore session only for backups that were created by the Sales Backup backup job.   |  | | --- | | $restorepoint = Get-VBORestorePoint  $job = Get-VBOJob -Name "Sales Backup"  Start-VBOTeamsItemRestoreSession -RestorePoint $restorepoint[2] -Job $job |  Perform the following steps:   1. Run the [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80) cmdlet. Save the result to the $restorepoint variable.   The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the third restore point in the array.   1. Run the [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80) cmdlet. Specify the Name parameter value. Save the result to the $job variable.  1. Run the Start-VBOTeamsItemRestoreSession cmdlet. Set the $restorepoint[2] variable as the RestorePoint parameter value. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Restore Scenario

|  |  |
| --- | --- |
| This example shows how to perform a restore scenario. The restore scenario includes the following steps:   * Start a remote restore session for a backup at the state of the latest restore point. * Perform an item restore from a Microsoft Teams team. * Stop a restore session.     |  | | --- | | $vbosrvcreds = Get-Credential  $session = Start-VBOTeamsItemRestoreSession -LatestState -Server vbo365server.support.local -Credential $vbosrvcreds  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $file = Get-VETFile -Team $team -Query "filename: report"  $orgcreds = Get-Credential  Restore-VETItem -Credential $orgcreds -File $file -RestoreChangedItem -RestoreMissingItem  Stop-VBOTeamsItemRestoreSession -Session $session |  Perform the following steps:   1. Start the remote restore session at the state of the latest restore point:  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $vbosrvcreds variable. 2. Run the Start-VBOTeamsItemRestoreSession cmdlet. Provide the LatestState parameter value. Specify the Server parameter value. Set the $vbosrvcreds variable as the Credential parameter value. Save the result to the $session variable.  1. Perform item restore:  1. Get files that you want to restore:  1. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 2. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the Name parameter value. Save the result to the $team variable. 3. Run the [Get-VETFile](get-vetfile.md) cmdlet. Set the $team variable as the Team parameter value. Specify the Query parameter value. Save the result to the $file variable.  1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Enter credentials that will be used to connect to the Microsoft Teams organization. Save the result to the $orgcreds variable. 2. Run the [Restore-VETitem](restore-vetitem.md) cmdlet. Set the $orgcreds variable as the Credential parameter value. Set the $file variable as the File parameter value. Provide the RestoreChangedItem and RestoreMissingItem parameter values.  1. Run the [Stop-VBOTeamsItemRestoreSession](stop-vboteamsitemrestoresession.md) cmdlet. Set the $session variable as the Session parameter value. |

Related Commands

* [Get-VBOOrganization](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vboorganization.html?ver=80)
* [Get-VBORestorePoint](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vborestorepoint.html?ver=80)
* [Get-VBOJob](https://helpcenter.veeam.com/docs/vbo365/powershell/get-vbojob.html?ver=80)
* [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETFile](get-vetfile.md)
* [Restore-VETitem](restore-vetitem.md)
* [Stop-VBOTeamsItemRestoreSession](stop-vboteamsitemrestoresession.md)

Page updated 7/24/2025

Page content applies to build 13.0.1.1071
