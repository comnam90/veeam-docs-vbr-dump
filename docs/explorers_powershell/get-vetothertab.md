---
title: "Get-VETOtherTab"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetothertab.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Get-VETOtherTab


Short Description

Returns Microsoft Teams team channel tabs.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tabs from a channel.

|  |
| --- |
| Get-VETOtherTab -Channel <VETChannel> [-Query <String>] [<CommonParameters>] |

* Get tabs from an organization.

|  |
| --- |
| Get-VETOtherTab [-Query <String>] -Organization <VETOrganization[]> [<CommonParameters>] |

* Get tabs from a team.

|  |
| --- |
| Get-VETOtherTab [-Query <String>] -Team <VETTeam> [<CommonParameters>] |

Detailed Description

This cmdlet returns tabs of Microsoft Teams team channels. You can get tabs from the following backed-up sources:

* Microsoft Teams organization
* Microsoft Teams team
* Microsoft Teams channel

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Channel | Specifies a Microsoft Teams team channel. The cmdlet will return tabs from this channel. | Accepts the [VETChannel](vetchannel.md) object. To get this object, run the [Get-VETChannel](get-vetchannel.md) cmdlet. | True | Named | True (ByValue) |
| Query | Specifies a query string for search of channel tabs. The cmdlet will return tabs that match the search query from the specified organization, team or channel.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Organization | Specifies an array of Microsoft Teams organizations. The cmdlet will return channel tabs from these organizations. | Accepts the [VETOrganization](vetorganization.md)[] object. To get this object, run the [Get-VETOrganization](get-vetorganization.md) cmdlet. | True | Named | True (ByValue) |
| Team | Specifies a Microsoft Teams team. This cmdlet will return channel tabs from this team. | Accepts the [VETTeam](vetteam.md) object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETOtherTab](vetothertab.md)[] array that contains Microsoft Teams channel tabs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Tabs from Channel

|  |  |
| --- | --- |
| This example shows how to get all tabs from the General channel.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Get-VETOtherTab -Channel $channel |  Perform the following steps:   1. Get the channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Get-VETOtherTab cmdlet. Set the $channel variable as the Channel parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tabs from Organization

|  |  |
| --- | --- |
| This example shows how to get Website tabs from channels of the ABC organization.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  Get-VETOtherTab -Organization $org -Query "name: website" |  Perform the following steps:   1. Get the organization:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.  1. Run the Get-VETOtherTab cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Tabs from Team

|  |  |
| --- | --- |
| This example shows how to get tabs from channels of the IT team.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  Get-VETOtherTab -Team $team |  Perform the following steps:   1. Get the team:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable.  1. Run the Get-VETOtherTab cmdlet. Set the $team variable as the Team parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETChannel](get-vetchannel.md)


