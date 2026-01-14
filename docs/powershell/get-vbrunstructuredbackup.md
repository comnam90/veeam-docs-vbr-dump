---
title: "Get-VBRUnstructuredBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackup.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackup

In this article

Short Description

Returns backup files created by file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get backup files created by file backup jobs and object storage backup jobs using job IDs.

|  |
| --- |
| Get-VBRUnstructuredBackup -Id <guid[]>  [<CommonParameters>] |

* Get backup files created by file backup jobs and object storage backup jobs using job names.

|  |
| --- |
| Get-VBRUnstructuredBackup -Name <string[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup files created by file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for file backup jobs and object storage backup jobs. The cmdlet will return an array of backup files that are created by these jobs. | Guid[] | True | Named | False |
| Name | Specifies an array of names for file backup jobs and object storage backup jobs. The cmdlet will return an array of backup files that are created by these jobs. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRUnstructuredBackup](vbrunstructuredbackup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backup Files Created by File Backup Job

|  |  |
| --- | --- |
| This command gets backup files that are created by the Reports backup file backup job. The cmdlet output will contain settings of the backup file created by the Reports backup file backup job.  |  | | --- | | Get-VBRUnstructuredBackup -Name "Reports backup" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Files by Object Storage Backup Job

|  |  |
| --- | --- |
| This command gets backup files that are created by the e5559d89-ca63-48dc-a53b-d9c54b7f2482 object storage backup job. The cmdlet output will contain settings of the backup file crated by the e5559d89-ca63-48dc-a53b-d9c54b7f2482 object storage backup job.  |  | | --- | | Get-VBRUnstructuredBackup -ID e5559d89-ca63-48dc-a53b-d9c54b7f2482 | |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
