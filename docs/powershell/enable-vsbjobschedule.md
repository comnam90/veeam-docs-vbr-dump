---
title: "Enable-VSBJobSchedule (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vsbjobschedule.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Enable-VSBJobSchedule (obsolete)

In this article

Short Description

Enables a SureBackup job schedule.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VSBJobSchedule [-Job <CSbJob[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet enables a SureBackup job schedule.

You can enable the job schedule in case the schedule is pre-configured for a selected job. You can enable the schedule that was configured in a disabled state or that was disabled with the [Disable-VSBJobSchedule](disable-vsbjobschedule.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of SureBackup jobs. The cmdlet will enable schedule for these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VSBJob](get-vsbjob.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
