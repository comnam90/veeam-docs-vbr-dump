---
title: "Get-VBRCloudTapeBackupTenantJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtapebackuptenantjob.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTapeBackupTenantJob


Short Description

Returns tenant jobs.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tenant jobs by the job name.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantJob [-Name <string[]>]  [<CommonParameters>] |

* Get tenant jobs by the job ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantJob -Id <guid[]>  [<CommonParameters>] |

* Get tenant jobs by the tenant ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantJob -TenantId <guid[]>  [<CommonParameters>] |

* Get tenant jobs by the tenant repository ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenantJob -TenantRepositoryId <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the array of jobs from the tenant Veeam Backup & Replication infrastructure.

|  |
| --- |
| ![Get-VBRCloudTapeBackupTenantJob](images/icon_important.webp) Important! |
| You can run this cmdlet from the service provider side only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of tenant jobs IDs. The cmdlet will return tenant jobs with specified IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |
| TenantId | Specifies an array of tenant IDs. The cmdlet will return tenant jobs of specified tenant IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |
| TenantRepositoryId | Specifies an array of the tenant cloud repository IDs. The cmdlet will return tenant jobs that are targeted to these repositories. | Guid[] | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies an array of tenant jobs names. The cmdlet will return tenant jobs with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTapeBackupTenantJob](vbrcloudtapebackuptenantjob.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Tenant Job by Name

|  |  |
| --- | --- |
| This command gets a tenant job by the job name.  |  | | --- | | Get-VBRCloudTapeBackupTenantJob -Name "Backup Job 01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tenant Job by Job ID

|  |  |
| --- | --- |
| This command gets a tenant job by the job ID.  |  | | --- | | Get-VBRCloudTapeBackupTenantJob -Id "0814a9b4-5fba-4f20-86dd-4790a5b659ab" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Tenant Job by Tenant ID

|  |  |
| --- | --- |
| This command gets a tenant job by the tenant ID.  |  | | --- | | Get-VBRCloudTapeBackupTenantJob -TenantId "12a6f8f5-832a-4c7c-9b9b-74b020d6d78e" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Tenant Job by Tenant Repository ID

|  |  |
| --- | --- |
| This command gets a tenant job by the tenant repository ID.  |  | | --- | | Get-VBRCloudTapeBackupTenantJob -TenantRepositoryId "729c82d6-54d5-4eb6-b0f2-9d85bcff1b9b" | |


