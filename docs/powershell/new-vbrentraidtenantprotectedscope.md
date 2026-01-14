---
title: "New-VBREntraIDTenantProtectedScope"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrentraidtenantprotectedscope.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# New-VBREntraIDTenantProtectedScope

In this article

Short Description

Specifies the tenant protection scope.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBREntraIDTenantProtectedScope [-ResourceType <VBREntraIDResourceType[]>]  [<CommonParameters>] |

Detailed Description

Specifies the scope of resources that will be protected for a specific Microsoft Entra ID tenant.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ResourceType | Specifies the types of resources that will be protected for the tenant.  Depending on the resources you want to add to the protection scope, you can set the following resource types:   * Users * Groups * AdminUnits * Roles * Apps * Logs * ConditionalAccessPolicies * IntunePolicies | VBREntraIDResourceType | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantProtectedScope](vbrentraidtenantprotectedscope.md) object that defines the tenant protection scope.

Examples

Specifying Entra ID Tenant Protection Scope

This example adds to the protection scope all users, groups, administrative units and conditional access policies of the tenant.

|  |
| --- |
| New-VBREntraIDTenantProtectedScope -ResourceType Users, Groups, AdminUnits, ConditionalAccessPolicies |

Related Commands

* [Add-VBREntraIDTenant](add-vbrentraidtenant.md)
* [Set-VBREntraIDTenant](set-vbrentraidtenant.md)

Page updated 10/15/2025

Page content applies to build 13.0.1.1071
