---
title: "Remove-VBRAzureRestoreProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrazurerestoreproxy.html"
last_updated: "5/30/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRAzureRestoreProxy

In this article

Short Description

Removes a restore proxy appliance from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAzureRestoreProxy -Proxy <VBRAzureRestoreProxy> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a restore proxy appliance for restoring backups to Microsoft Azure VMs from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies the restore proxy appliance that you want to remove. | Accepts the VBRAzureRestoreProxy object. To get this object, run the [Get-VBRAzureRestoreProxy](get-vbrazurerestoreproxy.md) cmdlet. | True | Named | True |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Microsoft Azure Restore Proxy Appliance from Backup Infrastructure

This example shows how to remove a restore proxy appliance from the backup infrastructure.

|  |
| --- |
| $Proxy = Get-VBRAzureRestoreProxy Name "AzureProxy-01"  Remove-VBRAzureRestoreProxy -Proxy $Proxy |

Perform the following steps:

1. Run the [Get-VBRAzureRestoreProxy](get-vbrazurerestoreproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $Proxy variable.
2. Run the Remove-VBRAzureRestoreProxy cmdlet. Set the $Proxy variable as the Proxy parameter value.

Related Commands

[Get-VBRAzureRestoreProxy](get-vbrazurerestoreproxy.md)

Page updated 5/30/2025

Page content applies to build 13.0.1.1071
