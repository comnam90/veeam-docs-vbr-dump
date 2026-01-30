---
title: "Get-VETTeamMember"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetteammember.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VETTeamMember


Short Description

Returns Microsoft Teams team members.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VETTeamMember -Team <VETTeam> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of team members from the specified Microsoft Teams team.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Team | Specifies a Microsoft Teams team. The cmdlet will return an array of team members from this team. | Accepts the [VETTeam](vetteam.md) object. To get this object, run the [Get-VETTeam](get-vetteam.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETTeamMember](vetteammember.md)[] array that contains Microsoft Teams team members.

Example

Getting Microsoft Teams Team Members

This example shows how to get team members from the IT team of the ABC Microsoft Teams organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  $team = Get-VETTeam -Organization $org -DisplayName "IT"  Get-VETTeamMember -Team $team |

Perform the following steps:

1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.
3. Run the [Get-VETTeam](get-vetteam.md) cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value. Save the result to the $team variable.
4. Run the Get-VETTeamMember cmdlet. Set the $team variable as the Team parameter value.

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)
* [Get-VETTeam](get-vetteam.md)


