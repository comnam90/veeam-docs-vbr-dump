---
title: "Get-VBRCloudInfrastructureState"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudinfrastructurestate.html"
last_updated: "1/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudInfrastructureState


Short Description

Returns the current state of the cloud infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Get-VBRCloudInfrastructureState  [<CommonParameters>] |

Detailed Description

This cmdlet returns the current state of the cloud infrastructure:

* Active: the cloud infrastructure is in normal operational mode.
* Maintenance: the cloud infrastructure is in Maintenance mode.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudInfrastructureState](enums.md#VBRCloudInfrastructureState)

Examples

Getting Cloud Infrastructure State

This command returns the state of the cloud infrastructure.

|  |
| --- |
| Get-VBRCloudInfrastructureState  Maintenance |


