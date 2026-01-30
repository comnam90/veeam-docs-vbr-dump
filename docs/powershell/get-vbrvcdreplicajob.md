---
title: "Get-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdreplicajob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDReplicaJob


Short Description

Returns Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Getting Cloud Director replication jobs by their name.

|  |
| --- |
| Get-VBRvCDReplicaJob [-Name <string[]>]  [<CommonParameters>] |

* Getting Cloud Director replication jobs by their ID.

|  |
| --- |
| Get-VBRvCDReplicaJob [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Cloud Director replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Cloud Director replication jobs. The cmdlet will return a list of jobs with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of Ids for Cloud Director replication jobs. The cmdlet will return a list of jobs with the specified IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDReplicaJob object that defines settings of the VDC replication jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Director Replication Job by Name

|  |  |
| --- | --- |
| This command returns the vCD\_05j VDC replication job.  |  | | --- | | Get-VBRvCDReplicaJob -Name "vCD\_05j" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Replication Job by ID

|  |  |
| --- | --- |
| This command returns the 2a7c321c-c8cf-4aec-9332-93882e69c667 VDC replication job.  |  | | --- | | Get-VBRvCDReplicaJob -Id "2a7c321c-c8cf-4aec-9332-93882e69c667" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all Cloud Director Replication Jobs

|  |  |
| --- | --- |
| This command returns all VDC replication jobs that are added to the backup infrastructure.  |  | | --- | | Get-VBRvCDReplicaJob | |


