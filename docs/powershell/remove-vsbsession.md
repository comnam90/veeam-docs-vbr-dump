---
title: "Remove-VSBSession (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vsbsession.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VSBSession (obsolete)


Short Description

Removes a specified SureBackup job session from Veeam Backup & Replication.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Remove-VSBSession -Sessions <CSbSession[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified SureBackup job session from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Sessions | Specifies the SureBackup job session you want to remove.  You can assign multiple sessions to this object. | Accepts the CSbSession[] object. To get this object, run the [Get-VSBSession](get-vsbsession.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Selected SureBackup Sessions [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the Winserver SureJob and Mailserver SureJob SureBackup sessions.  |  | | --- | | Get-VSBSession -Name "Winserver SureJob", "Mailserver SureJob" | Remove-VSBSession |  Perform the following steps:   1. Run the [Get-VSBSession](get-vsbsession.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VSBSession cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Selected SureBackup Sessions [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Winserver SureJob and Mailserver SureJob SureBackup sessions.  |  | | --- | | $suresession = Get-VSBSession -Name "Winserver SureJob", "Mailserver SureJob"  Remove-VSBSession -Sessions $suresession |  Perform the following steps:   1. Run the [Get-VSBSession](get-vsbsession.md) cmdlet. Specify the Name parameter value. Save the result to the $suresession variable. 2. Run the Remove-VSBSession cmdlet. Set the $suresession as the Sessions parameter value. |

Related Commands

[Get-VSBSession](get-vsbsession.md)


