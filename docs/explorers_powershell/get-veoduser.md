---
title: "Get-VEODUser"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veoduser.html"
last_updated: "3/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns OneDrive users.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VEODUser [-Session] <VBOOneDriveItemRestoreSession> [[-Name] <String[]>] [[-Organization] <VBOOneDriveOrganization[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns OneDrive organization users.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies an active Microsoft OneDrive restore session. This cmdlet will return organizations from the specified restore session. | Accepts the [VBOOneDriveItemRestoreSession](vboonedriveitemrestoresession.md) object. To get this object, run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of user names. The cmdlet will return users with these names.  This parameter accepts wildcard characters. | String[] | False | 1 | False |
| Organization | Specifies an array of Microsoft OneDrive organizations. The cmdlet will return OneDrive users from these organizations. | Accepts the [VBOOneDriveOrganization](vboonedriveorganization.md)[] object. To get this object, run the [Get-VEODOrganization](get-veodorganization.md) cmdlet. | False | 2 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveUser](vboonedriveuser.md)[] array that contains OneDrive users.

Example

Getting OneDrive Organization User

This example shows how to get the userAlpha OneDrive user from the ABC OneDrive organization added to Veeam Backup for Microsoft 365.

|  |
| --- |
| $session = Get-VEODRestoreSession  $org = Get-VEODOrganization -Session $session -Name "ABC\*"  Get-VEODUser -Organization $org -Name "userAlpha" |

Perform the following steps:

1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VEODOrganization](get-veodorganization.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Use the \* wildcard character to substitute the timestamp. Save the result to the $org variable.
3. Run the Get-VEODUser cmdlet. Set the $org variable as the Organization parameter value. Specify the Name parameter value.

Related Commands

* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODOrganization](get-veodorganization.md)

Page updated 3/6/2025

Page content applies to build 13.0.1.1071
