---
title: "Get-VBRCDPShortTermRestoreInterval"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdpshorttermrestoreinterval.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPShortTermRestoreInterval

In this article

Short Description

Returns a list of replicated states for VM replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCDPShortTermRestoreInterval -Replica <VBRCDPReplica>  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of the replicated states for VM replicas in the date and time format. You may want to run this cmdlet to get a list of all replicated states before you perform a failover.

Run the [Start-VBRCDPReplicaFailover](start-vbrcdpreplicafailover.md) cmdlet to perform a failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a VM protected with CDP. The cmdlet will return all replicated states that are available for this replica. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPShortTermRestoreInterval object that contains a list of the replicated states for VM replicas.

Examples

Getting Replicated States of VM Replicas

This example shows how to get a list of replicated states that are available for the Win07 VM protected with CDP.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win07"  Get-VBRCDPShortTermRestoreInterval -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Get-VBRCDPShortTermRestoreInterval cmdlet. Set the $replica variable as the Replica parameter.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
