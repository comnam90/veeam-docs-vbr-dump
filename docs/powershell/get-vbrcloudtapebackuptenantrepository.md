---
title: "Get-VBRCloudTapeBackupTenantRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtapebackuptenantrepository.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTapeBackupTenantRepository

In this article

Short Description

Returns tenant cloud repositories.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tenant cloud repositories by the tenant friendly name.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantRepository [-Name <string[]>]  [<CommonParameters>] |

* Get tenant cloud repository by the repository ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantRepository -Id <guid[]>  [<CommonParameters>] |

* Get tenant cloud repository by the tenant ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantRepository -TenantId <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the array of tenant cloud repositories.

|  |
| --- |
| ![Get-VBRCloudTapeBackupTenantRepository](images/icon_important.webp) Important! |
| You can run this cmdlet from the service provider side only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of friendly names for tenant backup repositories. The cmdlet will return the tenant backup repositories with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies an array of IDs for tenant backup repositories. The cmdlet will return the tenant backup repositories with the specified IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |
| TenantId | Specifies an array of tenant IDs. The cmdlet will return tenant backup repositories with the specified tenant IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRCloudTapeBackupTenantRepository

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Tenant Cloud Repositories

|  |  |
| --- | --- |
| This command gets an array of all tenant cloud repositories.  |  | | --- | | Get-VBRCloudTapeBackupTenantRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tenant Cloud Repository by Repository ID

|  |  |
| --- | --- |
| This command gets a tenant cloud repository by the repository ID.  |  | | --- | | Get-VBRCloudTapeBackupTenantRepository -ID "0fccf7c9-1f90-49de-8bec-53a0697e04ab" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Tenant Cloud Repository by Repository Name

|  |  |
| --- | --- |
| This command gets tenant cloud repositories by the tenant friendly name.  |  | | --- | | Get-VBRCloudTapeBackupTenantRepository -Name "New tenant" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Tenant Cloud Repository by Tenant ID

|  |  |
| --- | --- |
| This command gets tenant cloud repositories by the tenant ID.  |  | | --- | | Get-VBRCloudTapeBackupTenantRepository -TenantId "4bff98a5-c49e-473c-8ce0-4203549b7560" | |

Page updated 4/12/2024

Page content applies to build 13.0.1.1071
