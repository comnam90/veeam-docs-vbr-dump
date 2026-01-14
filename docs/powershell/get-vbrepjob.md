---
title: "Get-VBREPJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrepjob.html"
last_updated: "2/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBREPJob

In this article

Short Description

Returns backup jobs run by Veeam Agent operating in the standalone mode.

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all backup jobs run by Veeam Agent:

|  |
| --- |
| Get-VBREPJob  [<CommonParameters>] |

* Look for backup jobs run by Veeam Agent by a job name:

|  |
| --- |
| Get-VBREPJob [-Name <string[]>]  [<CommonParameters>] |

* Look for backup jobs run by Veeam Agent by a job ID:

|  |
| --- |
| Get-VBREPJob [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup jobs run by Veeam Agent operating in the standalone mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of  backup job names. The cmdlet will return jobs with these names. | String[] | False | Named | False |
| Id | Specifies the array of job IDs. The cmdlet will return the backup jobs with these IDs. | Accepts GUID[] or string[]. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBREPJob](vbrepjob.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backup Jobs by Veeam Agent in Standalone Mode

|  |  |
| --- | --- |
| This command returns all backup jobs run by Veeam Agent operating in the standalone mode.  |  | | --- | | Get-VBREPJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Backup Job by Veeam Agent in Standalone Mode

|  |  |
| --- | --- |
| This command gets a backup job run by Veeam Agent operating in the standalone mode by a job name.  |  | | --- | | Get-VBREPJob -Name "Backup Job Mediaserver" | |

Page updated 2/7/2025

Page content applies to build 13.0.1.1071
