---
title: "get-veodorganization"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veodorganization.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns Microsoft OneDrive organizations added to Veeam Backup for Microsoft 365.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEODOrganization [-Session] <VBOOneDriveItemRestoreSession> [[-Name] <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft OneDrive organizations added to Veeam Backup for Microsoft 365.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active Microsoft OneDrive restore session. This cmdlet will return organizations from the specified restore session. | Accepts the [VBOOneDriveItemRestoreSession](vboonedriveitemrestoresession.md) object. To get this object, run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of Microsoft OneDrive organization names. The cmdlet will return an array of organizations with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveOrganization](vboonedriveorganization.md)[] array that contains OneDrive organizations added to Veeam Backup for Microsoft 365.

Example

Getting Microsoft OneDrive Organization

This example shows how to get the ABC OneDrive organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VEODRestoreSession  Get-VEODOrganization -Session $session -Name "ABC\*" |

Perform the following steps:

1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the Get-VEODOrganization cmdlet. Set the $session as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp.

Related Commands

[Get-VEODRestoreSession](get-veodrestoresession.md)

Page updated 3/17/2025

Page content applies to build 13.0.1.1071
