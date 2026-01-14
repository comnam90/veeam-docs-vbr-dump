---
title: "Remove-VBREntraIDTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrentraidtenant.html"
last_updated: "12/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBREntraIDTenant

In this article

Short Description

Removes Microsoft Entra ID tenants from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBREntraIDTenant -Tenant <VBREntraIDTenant[]>  [<CommonParameters>] |

Detailed Description

This cmdlet removes Entra ID tenants from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies an array of tenants that you want to remove from the backup infrastructure. | Accepts the VBREntraIDTenant[] object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Entra ID Tenant

This example shows how to remove an Entra ID tenant from the backup infrastructure.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxxx"  Remove-VBREntraIDTenant -Tenant $tenant |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the Remove-VBREntraIDTenant cmdlet. Set the $tenant variable as the Tenant parameter value.

Related Commands

[Get-VBREntraIdTenant](get-vbrentraidtenant.md)

Page updated 12/17/2024

Page content applies to build 13.0.1.1071
