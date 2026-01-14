---
title: "Get-VBRMongoDBComputer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrmongodbcomputer.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRMongoDBComputer

In this article

Short Description

Returns a list of all computers within specified replica sets.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRMongoDBComputer [-Name <String[]>] -Deployment <VBRMongoDBDeployment> [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of individual computers included in MongoDB replica sets.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the computer included in a specific replica set. | String | False | Named | True (ByPropertyName) |
| Deployment | Specifies the replica set. | Accepts the [VBRMongoDBDeployment](vbrmongodbdeployment.md) object. To get this object, run the [New-VBRMongoDBDeployment](new-vbrmongodbdeployment.md) cmdlet. | True | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBComputer](vbrmongodbcomputer.md#VBRMongoDBComputer) object.

Examples

Loading a List of All Computers Within Multiple Replica Sets

This example shows how to load a list of all computers in two separate replica sets $replicaSet1 and $replicaSet2.

|  |
| --- |
| $rs1Computers = Get-VBRMongoDBComputer -Deployment $replicaSet1  $rs2Computers = Get-VBRMongoDBComputer -Deployment $replicaSet2 |

Perform the following steps:

1. Run the Get-VBRMongoDBComputer cmdlet. Specify the Deployment parameter value with the name of a specific replica set $replicaSet1. Save the result to the $rs1Computers variable.
2. Run the Get-VBRMongoDBComputer cmdlet. Specify the Deployment parameter value with the name of a specific replica set $replicaSet2. Save the result to the $rs2Computers variable.

Related Commands

* [New-VBRMongoDBDeployment](new-vbrmongodbdeployment.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
