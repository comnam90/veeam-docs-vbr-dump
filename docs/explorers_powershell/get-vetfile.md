---
title: "Get-VETFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetfile.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Get-VETFile


Short Description

Returns files published in Microsoft Teams team channels.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get files from a channel.

|  |
| --- |
| Get-VETFile -Channel <VETChannel> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get files under the specified folder.

|  |
| --- |
| Get-VETFile -Channel <VETChannel> -ParentFile <VETFile> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get files from an organization.

|  |
| --- |
| Get-VETFile [-Query <String>] -Organization <VETOrganization[]> [<CommonParameters>] |

* Get files from a team.

|  |
| --- |
| Get-VETFile [-Query <String>] -Team <VETTeam> [<CommonParameters>] |

Detailed Description

This cmdlet returns files published in Microsoft Teams team channels. You can get files from the following backed-up sources:

* Microsoft Teams organization
* Microsoft Teams team
* Microsoft Teams channel

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Channel | Specifies a Microsoft Teams team channel. The cmdlet will return files from this channel. | Accepts the [VETChannel](vetchannel.md) object. To get this object, run the [Get-VETChannel](get-vetchannel.md) cmdlet. | True | Named | True (ByValue) |
| Query | Specifies a query string for file search. The cmdlet will return files that match the search query from the specified organization, team, channel or folder.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Recurse | Defines that the cmdlet will return the specified folder and all files in this folder.  Default: False | SwitchParameter | False | Named | False |
| ParentFile | Specifies a folder. The cmdlet will return files from this folder. | Accepts the [VETFile](vetfile.md) object. To get this object, run the Get-VETFile cmdlet. | True | Named | True (ByValue) |
| Organization | Specifies an array of Microsoft Teams organizations. The cmdlet will return files from these organizations. | Accepts the [VETOrganization](vetorganization.md)[] object. To get this object, run the [Get-VETOrganization](get-vetorganization.md) cmdlet. | True | Named | True (ByValue) |
| Team | Specifies a Microsoft Teams team. This cmdlet will return files from this team. | Accepts the [VETTeam](vetteam.md) object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETFile](vetfile.md)[] array that contains Microsoft Teams files.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Files from Channel

|  |  |
| --- | --- |
| This example shows how to get all files from the General channel.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Get-VETFile -Channel $channel |  Perform the following steps:   1. Get the channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Get-VETFile cmdlet. Set the $channel variable as the Channel parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Files from Organization

|  |  |
| --- | --- |
| This example shows how to get the report.txt file from the ABC organization.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  Get-VETFile -Organization $org -Query "filename: report" |  Perform the following steps:   1. Get the organization:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.  1. Run the Get-VETFile cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Files from Team

|  |  |
| --- | --- |
| This example shows how to get files from the IT team.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  Get-VETFile -Team $team |  Perform the following steps:   1. Get the team:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable.  1. Run the Get-VETFile cmdlet. Set the $team variable as the Team parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETChannel](get-vetchannel.md)


