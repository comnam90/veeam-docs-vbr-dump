---
title: "Disable-VBRCloudMaintenanceMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcloudmaintenancemode.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCloudMaintenanceMode


Short Description

Disables Maintenance mode for the cloud infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Disable-VBRCloudMaintenanceMode [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the cloud infrastructure to the normal operational mode. Cloud resources become available for the associated cloud tenants.

Run the [Enable-VBRCloudMaintenanceMode](enable-vbrcloudmaintenancemode.md) cmdlet to bring the cloud infrastructure back to the Maintenance mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Maintenance Mode for Cloud Infrastructure

This command returns the cloud infrastructure to the normal operational mode.

|  |
| --- |
| Disable-VBRCloudMaintenanceMode |


