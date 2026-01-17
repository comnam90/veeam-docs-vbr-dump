---
title: "Get-VETOrganization"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetorganization.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns Microsoft Teams organizations added to Veeam Backup for Microsoft 365.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VETOrganization [-Session] <ITeamsRestoreSession> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft Teams organizations added to Veeam Backup for Microsoft 365.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active Microsoft Teams restore session. This cmdlet will return organizations from the specified restore session. | Accepts the [VBOTeamsRestoreSession](vboteamsrestoresession.md) object. To get this object, run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of Microsoft Teams organizations. The cmdlet will return an array of organizations with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETOrganization](vetorganization.md)[] array that contains Microsoft Teams organizations added to Veeam Backup for Microsoft 365.

Example

Getting Microsoft Teams Organization

This example shows how to get the ABC Microsoft Teams organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VBOTeamsItemRestoreSession  Get-VETOrganization -Session $session -Name "ABC\*" |

Perform the following steps:

1. Run the [Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Get-VETOrganization cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp.

Related Commands

[Get-VBOTeamsItemRestoreSession](get-vboteamsitemrestoresession.md)

Page updated 3/17/2025

Page content applies to build 13.0.1.1071
