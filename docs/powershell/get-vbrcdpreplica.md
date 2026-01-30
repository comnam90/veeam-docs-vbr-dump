---
title: "Get-VBRCDPReplica"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdpreplica.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPReplica


Short Description

Returns CDP replicas created by CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get replicas by names of the workloads protected by CDP.

|  |
| --- |
| Get-VBRCDPReplica [-Name <string[]>] [-Type {Local | Cloud | Tenant | CloudvCD}]  [<CommonParameters>] |

* Get replicas by IDs of the workloads protected by CDP.

|  |
| --- |
| Get-VBRCDPReplica [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns CDP replicas created by CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of workloads protected by CDP. The cmdlet will return a list of replicas of the workloads with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Type | Specifies which type of replicas to get:   * Local: use this option to get local CDP and Cloud Director CDP replicas. The cmdlet will return replicas created not using Cloud Connect. * Tenant: use this option to get CDP replicas available on the tenant side. The cmdlet will return replicas created using Cloud Connect. * Cloud: use this option to get CDP replicas available on the Service Provider side. The cmdlet will return replicas created using Cloud Connect during the CDP to VMware scenario. * CloudvCD: use this option to get CDP replicas available on the Service Provider side. The cmdlet will return replicas created using Cloud Connect during the CDP to VMware Cloud Director scenario. | VBRReplicaType | False | Named | False |
| Id | Specifies an array of IDs of workloads protected by CDP. The cmdlet will return a list of replicas of the workloads with these IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPReplicaBase object that contains a list of replicas.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting VM Protected with CDP by Name

|  |  |
| --- | --- |
| This command returns the Win07 VM protected with CDP.  |  | | --- | | Get-VBRCDPReplica -Name "Win07" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VM Protected with CDP by ID

|  |  |
| --- | --- |
| This command returns the 13744fce-e8ea-4b77-9092-26e3f09e6a6e VM protected with CDP.  |  | | --- | | Get-VBRCDPReplica -Id "13744fce-e8ea-4b77-9092-26e3f09e6a6e" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all VM Replicas Available in Backup Infrastructure

|  |  |
| --- | --- |
| This command returns all VM replicas that are available in the backup Infrastructure  |  | | --- | | Get-VBRCDPReplica | |


