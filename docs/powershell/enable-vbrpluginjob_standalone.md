---
title: "Enable-VBRPluginJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrpluginjob_standalone.html"
last_updated: "8/17/2023"
product_version: "13.0.1.1071"
---

# Enable-VBRPluginJob

In this article

Short Description

Enables backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRPluginJob -Job <VBRPluginJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Run the [Disable-VBRPluginJob](disable-vbrpluginjob.md) cmdlet to disable backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of jobs. The cmdlet will enable these jobs. | Accepts the VBRPluginJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Backup Job Created with Standalone Veeam Plug-in

This example shows how to enable backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

|  |
| --- |
| $job = Get-VBRPluginJob -Name "Plug-in backup 17"  Enable-VBRPluginJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Enable-VBRPluginJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRPluginJob](get-vbrpluginjob.md)

Page updated 8/17/2023

Page content applies to build 13.0.1.1071
