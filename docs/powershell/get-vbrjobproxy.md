---
title: "Get-VBRJobProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjobproxy.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Get-VBRJobProxy

In this article

Short Description

Returns a list of proxy servers assigned to a specific job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobProxy -Job <CBackupJob[]> [-Target]  [<CommonParameters>] |

Detailed Description

This cmdlet returns proxy servers assigned to a specific job. If the automatic proxy selection is enabled, the cmdlet will return a warning.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of jobs. The cmdlet will return proxies assigned to these jobs. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Target | Defines that the cmdlet will return only target proxies.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the IBackupProxy[]object that contains an array of proxies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Target Proxies [Using Variable]

|  |  |
| --- | --- |
| This example shows how to get a list of proxies assigned to the Backup Copy job.  |  | | --- | | $job = Get-VBRJob -Name "Backup Copy"  Get-VBRJobProxy -Job $job -Target |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Get-VBRJobProxy cmdlet. Set the $job variable as the Job parameter value. Provide the Target parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting List of Target Proxies [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get a list of target proxies assigned to the Backup Copy job.  |  | | --- | | Get-VBRJob -Name "Backup Copy" | Get-VBRJobProxy -Target |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRJobProxy cmdlet. Provide the Target parameter. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
