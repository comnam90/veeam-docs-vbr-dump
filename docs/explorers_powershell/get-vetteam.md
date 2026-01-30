---
title: "Get-VETTeam"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetteam.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VETTeam


Short Description

Returns Microsoft Teams teams.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VETTeam [-Organization] <VETOrganization> [[-DisplayName] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns teams for a specified Microsoft Teams organization.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Organization | Specifies a Microsoft Teams organization. The cmdlet will return Microsoft Teams teams from this organization. | Accepts the [VETOrganization](vetorganization.md) object. To get this object, run the [Get-VETOrganization](get-vetorganization.md) cmdlet. | True | 0 | True (ByValue) |
| DisplayName | Specifies an array of display names for Microsoft Teams teams. The cmdlet will return an array of teams with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETTeam](vetteam.md)[] array that contains Microsoft Teams teams.

Example

Getting Microsoft Teams Team

This example shows how to get the IT team of the ABC Microsoft Teams organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VBOTeamsItemRestoreSession  $org = Get-VETOrganization -Session $session -Name "ABC\*"  Get-VETTeam -Organization $org -DisplayName "IT" |

Perform the following steps:

1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VETOrganization](get-vetorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.
3. Run the Get-VETTeam cmdlet. Set the $org variable as the Organization parameter value. Specify the DisplayName parameter value.

Related Commands

* [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)
* [Get-VETOrganization](get-vetorganization.md)


