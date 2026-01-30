---
title: "Disable-VBRPluginJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrpluginjob.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRPluginJob


Short Description

Disables backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRPluginJob -Job <VBRPluginJob[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Run the [Enable-VBRPluginJob](enable-vbrpluginjob.md) cmdlet to enable backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array jobs. The cmdlet will disable these jobs. | Accepts the VBRPluginJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | True | 0 | True (ByValue) |
| WhatIf | Specifies a list of all jobs that will be disabled. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will return a notification that the backup files created by these jobs will be left in the inconsistent state after running this cmdlet. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Backup Job Created with Standalone Veeam Plug-in

This example shows how to disable backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins.

|  |
| --- |
| $job = Get-VBRPluginJob -Name "Plug-in backup 17"  Disable-VBRPluginJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Disable-VBRPluginJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRPluginJob](get-vbrpluginjob.md)


