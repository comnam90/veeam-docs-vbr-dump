---
title: "Remove-VBRPluginJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrpluginjob.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRPluginJob

In this article

Short Description

Removes backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins from the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRPluginJob -Job <VBRPluginJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup jobs that were created with standalone Veeam Plug-ins and backup copy jobs of backups created with Veeam Plug-ins from the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of jobs. The cmdlet will remove these jobs from the Veeam Backup & Replication infrastructure. | Accepts the VBRPluginJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | True | 0 | True (ByValue) |
| WhatIf | Specifies a list of all jobs that will be deleted. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Backup Job Created with Standalone Veeam Plug-in

This example shows how to remove plug-in backup jobs and plug-in backup copy jobs from the Veeam Backup & Replication infrastructure.

|  |
| --- |
| $pluginjobs = Get-VBRPluginJob -Name "Plug-in backup 17"  Remove-VBRPluginJob -Job $pluginjobs |

Perform the following steps:

1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjobs variable.
2. Run the Remove-VBRPluginJob cmdlet. Set the $pluginjobs variable as the Job parameter value.

Related Commands

[Get-VBRPluginJob](get-vbrpluginjob.md)

Page updated 6/3/2024

Page content applies to build 13.0.1.1071
