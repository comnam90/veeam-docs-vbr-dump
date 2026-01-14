---
title: "Set-VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeMedium

In this article

Short Description

Modifies tape properties.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeMedium -Medium <VBRTapeMedium> [-Name <String>] [-Description <String>] [-MarkAsFree] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies properties of a selected tape. You can modify name and/or description of the tape, or mark it as free.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies tape you want to modify. | Accepts the [VBRTapeMedium](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the new name you want to assign to the tape. | String | False | Named | False |
| Description | Specifies the new description you want to assign to the tape. | String | False | Named | False |
| MarkAsFree | If you provide this parameter, the cmdlet will mark the tape as free.  Veeam Backup & Replication will delete from backup and tape catalogs information about backup contents stored on tape. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMedium](vbrtapemedium.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Updating Tape Name and Description [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to rename the 0014001F tape into SQL 9/2022 and sets a description for it.  |  | | --- | | Get-VBRTapeMedium -Name "0014001F" | Set-VBRTapeMedium -Name "SQL 9/2022" -Description "SQL DB monthly full backups: Sept/2022" |  Perform the following steps:   1. Run the Get-VBRTapeMedium cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRTapeMedium cmdlet. Specify the Name parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Marking Tape as Free [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to mark the 0014001F tape as free.  |  | | --- | | Get-VBRTapeMedium -Name "0014001F" | Set-VBRTapeMedium -MarkAsFree |  Perform the following steps:   1. Run the Get-VBRTapeMedium cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRTapeMedium cmdlet. Provide the MarkAsFree parameter. |

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
