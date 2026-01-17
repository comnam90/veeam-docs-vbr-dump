---
title: "Get-VETPost"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetpost.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Get-VETPost


Short Description

Returns Microsoft Teams team channel posts.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get posts from a channel.

|  |
| --- |
| Get-VETPost -Channel <VETChannel> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get posts under the specified parent post.

|  |
| --- |
| Get-VETPost -ParentPost <VETPost> [-Query <String>] [-Recurse] [<CommonParameters>] |

* Get posts from an organization.

|  |
| --- |
| Get-VETPost [-Query <String>] -Organization <VETOrganization[]> [<CommonParameters>] |

* Get posts from a team.

|  |
| --- |
| Get-VETPost [-Query <String>] -Team <VETTeam> [<CommonParameters>] |

Detailed Description

This cmdlet returns posts published in Microsoft Teams team channels. You can get parent and child posts from the following backed-up sources:

* Microsoft Teams organization
* Microsoft Teams team
* Microsoft Teams channel

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Channel | Specifies a Microsoft Teams team channel. The cmdlet will return posts from this channel. | Accepts the [VETChannel](vetchannel.md) object. To get this object, run the [Get-VETChannel](get-vetchannel.md) cmdlet. | True | Named | True (ByValue) |
| Query | Specifies a query string for post search. The cmdlet will return posts that match the search query from the specified organization, team, channel or parent post.  For more information, see the [Appendix A. Item Search Parameters](https://helpcenter.veeam.com/docs/vbo365/guide/appendix_search.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. | String | False | Named | False |
| Recurse | Defines that the cmdlet will return the specified parent post and all of its child posts.  Default: False | SwitchParameter | False | Named | False |
| ParentPost | Specifies a parent post. The cmdlet will return child posts of this parent post. | Accepts the [VETPost](vetpost.md) object. To get this object, run the Get-VETPost cmdlet. | True | Named | True (ByValue) |
| Organization | Specifies an array of Microsoft Teams organizations. The cmdlet will return posts from these organizations. | Accepts the [VETOrganization](vetorganization.md)[] object. To get this object, run the [Get-VETOrganization](get-vetorganization.md) cmdlet. | True | Named | True (ByValue) |
| Team | Specifies a Microsoft Teams team. This cmdlet will return posts from this team. | Accepts the [VETTeam](vetteam.md) object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETPost](vetpost.md)[] array that contains Microsoft Teams posts.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Posts from Channel

|  |  |
| --- | --- |
| This example shows how to get all posts from the General channel.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  $channel = Get-VETChannel -Team $team -DisplayName "General"  Get-VETPost -Channel $channel |  Perform the following steps:   1. Get the channel:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable. 4. Run the [Get-VETChannel](get-vetchannel.md) cmdlet. Set the $team variable as the Team parameter value. Specify the DisplayName parameter value. Save the result to the $channel variable.  1. Run the Get-VETPost cmdlet. Set the $channel variable as the Channel parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Posts from Parent Post

|  |  |
| --- | --- |
| This example shows how to get channel posts under the Announcement parent post.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $post = Get-VETPost -Organization $org -Query "subject: announcement"  Get-VETPost -ParentPost $post |  Perform the following steps:   1. Get the parent post:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the Get-VETPost cmdlet. Set the $org variable as the Organization parameter value. Specify the Query parameter value. Save the result to the $post variable.  1. Run the Get-VETPost cmdlet. Set the $post variable as the ParentPost parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3 Getting Posts from Organization

|  |  |
| --- | --- |
| This example shows how to get channel posts from the ABC organization.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  Get-VETPost -Organization $org |  Perform the following steps:   1. Get the organization:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.  1. Run the Get-VETPost cmdlet. Set the $org variable as the Organization parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Posts from Team

|  |  |
| --- | --- |
| This example shows how to get channel posts from the IT team.  |  | | --- | | $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  Get-VETPost -Team $team |  Perform the following steps:   1. Get the team:  1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable. 3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable.  1. Run the Get-VETPost cmdlet. Set the $team variable as the Team parameter value. |

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)
* [Get-VETChannel](get-vetchannel.md)


