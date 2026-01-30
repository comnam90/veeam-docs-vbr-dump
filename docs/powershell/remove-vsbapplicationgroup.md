---
title: "Remove-VSBApplicationGroup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vsbapplicationgroup.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VSBApplicationGroup (obsolete)


Short Description

Removes a specified application group from Veeam Backup & Replication.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Remove-VBRApplicationGroup](remove-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VSBApplicationGroup -AppGroup <CSbAppGroup[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified application group from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| AppGroup | Specifies the array of application groups. The cmdlet will remove these application groups. | Accepts the CSbAppGroup[] object. To get this object, run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Application Groups [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the AppGroup 01 and AppGroup 02 application groups.  |  | | --- | | Get-VSBApplicationGroup -Name "AppGroup 01", "AppGroup 02"| Remove-VSBApplicationGroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VSBApplicationGroup cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Application Groups [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the AppGroup 01 and AppGroup 02 application groups.  |  | | --- | | $appgroup = Get-VSBApplicationGroup -Name "AppGroup 01", "AppGroup 02"  Remove-VSBApplicationGroup -AppGroup $appgroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $appgroup variable. 2. Run the Remove-VSBApplicationGroup cmdlet. Set the $appgroup as the AppGroup parameter value. |

Related Commands

[Get-VSBApplicationGroup](get-vsbapplicationgroup.md)


