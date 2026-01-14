---
title: "Get-VSBTaskSession (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbtasksession.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Get-VSBTaskSession (obsolete)

In this article

Short Description

Returns tasks performed during the specified SureBackup session.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. Use the [Get-VBRSureBackupTaskSession](get-vbrsurebackuptasksession.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VSBTaskSession -Session <CSbSession> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of tasks performed during the specified SureBackup session.

Run the [Get-VBRTaskSession](get-vbrtasksession.md) cmdlet to get the tasks for backup, replication and backup copy sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the array of SureBackup sessions. The cmdlet will return tasks performed during these sessions. | Accepts the CSbSession object. To get this object, run the [Get-VSBSession](get-vsbsession.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the array of SureBackup job names. The cmdlet will return tasks performed for VMs in these jobs during the selected job session. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Tasks for Selected SureBackup Session [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the list of tasks performed for the DC and DNS VMs in the Exchange SureJob SureBackup job session.  |  | | --- | | Get-VSBSession -Name "Exchange SureJob" | Get-VSBTaskSession -Name "DC", "DNS" |  Perform the following steps:   1. Run the [Get-VSBSession](get-vsbsession.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VSBTaskSession cmdlet. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting List of Tasks for Selected SureBackup Session [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get the list of tasks performed for the DC and DNS VMs in the Exchange SureJob SureBackup job session.  |  | | --- | | $ExchangeSureJob = Get-VSBSession -Name "Exchange SureJob"  Get-VSBTaskSession -Session $ExchangeSureJob -Name "DC", "DNS" |  Perform the following steps:   1. Run the [Get-VSBSession](get-vsbsession.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeSureJob variable. 2. Run the Get-VSBTaskSession cmdlet. Set the $ExchangeSureJob variable as the Session parameter value. Specify the Name parameter value. |

Related Commands

[Get-VSBSession](get-vsbsession.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
