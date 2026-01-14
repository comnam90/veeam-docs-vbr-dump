---
title: "Get-VBREntraIDTenantBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantbackupjob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantBackupJob

In this article

Short Description

Returns backup jobs that protect Microsoft Entra ID tenants.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Entra ID tenant backup jobs.

|  |
| --- |
| Get-VBREntraIDTenantBackupJob  [<CommonParameters>] |

* Get tenant backup jobs by job IDs.

|  |
| --- |
| Get-VBREntraIDTenantBackupJob -Id <Guid[]>  [<CommonParameters>] |

* Get tenant backup jobs by job names.

|  |
| --- |
| Get-VBREntraIDTenantBackupJob -Name <String[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup jobs that protect Entra ID tenants.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs of tenant backup jobs. The cmdlet will return an array of jobs with the specified IDs. | Guid[] | True | Named | True (ByPropertyName) |
| Name | Specifies an array of names of tenant backup jobs. The cmdlet will return an array of jobs with the specified names. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDTenantBackupJob](vbrentraidtenantbackupjob.md) objects that contain settings of the tenant backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Tenant Backup Jobs

|  |  |
| --- | --- |
| This example shows how to get all tenant backup jobs.  |  | | --- | | $backupJobs = Get-VBREntraIDTenantBackupJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tenant Backup Job by Name

|  |  |
| --- | --- |
| This example shows how to get the Tenant Backup backup job.  |  | | --- | | $backupJob = Get-VBREntraIDTenantBackupJob -Name "Tenant Backup" | |

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
