---
title: "Get-VBRvCDReplica"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdreplica.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRvCDReplica


Short Description

Returns Cloud Director replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return Cloud Director replicas by their names.

|  |
| --- |
| Get-VBRvCDReplica [-Name <String[]>]  [<CommonParameters>] |

* Action Cloud Director replicas by their ID.

|  |
| --- |
| Get-VBRvCDReplica [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Cloud Director replicas.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Cloud Director replicas. The cmdlet will return a list of Cloud Director replicas with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of Ids for Cloud Director replicas. The cmdlet will return a list of Cloud Director replicas with the specified IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDReplica object that contains Cloud Director replicas settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Director Replicas by Name

|  |  |
| --- | --- |
| This command returns the vCD\_05j Cloud Director replicas.  |  | | --- | | Get-VBRvCDReplica -Name "vCD\_05j" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Replicas by ID

|  |  |
| --- | --- |
| This command returns the 2a7c321c-c8cf-4aec-9332-93882e69c667 Cloud Director replicas.  |  | | --- | | Get-VBRvCDReplica -Id "2a7c321c-c8cf-4aec-9332-93882e69c667" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all Cloud Director Replicas Jobs

|  |  |
| --- | --- |
| This command returns all Cloud Director replicas that are added to the backup infrastructure.  |  | | --- | | Get-VBRvCDReplica | |


