---
title: "Get-VESPOrganization"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesporganization.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---

# Get-VESPOrganization


Short Description

Returns SharePoint organizations added to Veeam Backup for Microsoft 365.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPOrganization [-Session] <VBOSharePointRestoreSession> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns SharePoint organizations added to Veeam Backup for Microsoft 365.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a SharePoint restore session. This cmdlet will return organizations from the specified restore session. | Accepts the [VBOSharePointRestoreSession](vbosharepointrestoresession.md) object. To get this object, run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of SharePoint organization names. The cmdlet will return an array of organizations with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPOrganization](vesporganization.md)[] array that contains SharePoint organizations added to Veeam Backup for Microsoft 365.

Example

Getting SharePoint Organization

This example shows how to get the ABC SharePoint organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VBOSharePointItemRestoreSession  Get-VESPOrganization -Session $session -Name "ABC\*" |

Perform the following steps:

1. Run the [Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Get-VESPOrganization cmdlet. Set the $session as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp.

Related Commands

[Get-VBOSharePointItemRestoreSession](get-vbosharepointitemrestoresession.md)


