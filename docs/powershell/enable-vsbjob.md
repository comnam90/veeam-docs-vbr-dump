---
title: "Enable-VSBJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vsbjob.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Enable-VSBJob (obsolete)

In this article

Short Description

Enables a disabled SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Enable-VBRSureBackupJob](enable-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VSBJob -Job <CSbJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables a disabled SureBackup job. When you disable a job, you put it on hold until you enable it with this cmdlet. You can disable a job by running the [Disable-VSBJob](disable-vsbjob.md) cmdlet.

Run the [Start-VSBJob](start-vsbjob.md) cmdlet to run a disabled job once.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of SureBackup jobs. The cmdlet will enable these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VSBJob](get-vsbjob.md)

Page updated 2/23/2024

Page content applies to build 13.0.1.1071
