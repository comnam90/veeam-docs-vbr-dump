---
title: "Enable-VBRCloudMaintenanceMode"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcloudmaintenancemode.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCloudMaintenanceMode

In this article

Short Description

Enables Maintenance mode for the cloud infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Enable-VBRCloudMaintenanceMode [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet sets the cloud infrastructure into Maintenance mode to let a service provider perform Maintenance tasks.

Run the [Disable-VBRCloudMaintenanceMode](disable-vbrcloudmaintenancemode.md) cmdlet to bring the cloud infrastructure back to the normal operational mode.

|  |
| --- |
| Important |
| When a service provider enables the Maintenance mode, cloud resources become temporarily inaccessible for the associated cloud tenants. As a result, most of the running jobs fail. For more information, see the [Maintenance Mode](https://helpcenter.veeam.com/docs/backup/cloud/cc_maintenance_mode.html?ver=120) section in the Veeam Cloud Connect Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Maintenance Mode for Cloud Infrastructure

This command puts the cloud infrastructure to Maintenance mode.

|  |
| --- |
| Enable-VBRCloudMaintenanceMode |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
