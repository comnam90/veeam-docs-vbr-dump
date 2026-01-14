---
title: "Disable-VSBJobSchedule (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vsbjobschedule.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Disable-VSBJobSchedule (obsolete)

In this article

Short Description

Disables a selected SureBackup job schedule.

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
| Disable-VSBJobSchedule -Job <CSbJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables a selected SureBackup job schedule. The schedule settings are not deleted. When you disable a job schedule, you can launch the job manually by running the [Start-VSBJob](start-vsbjob.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of SureBackup jobs. The cmdlet will disable schedule of these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VSBJob](get-vsbjob.md)

Page updated 2/23/2024

Page content applies to build 13.0.1.1071
