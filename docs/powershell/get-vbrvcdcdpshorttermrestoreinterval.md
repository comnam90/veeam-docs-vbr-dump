---
title: "Get-VBRvCDCDPShortTermRestoreInterval"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcdpshorttermrestoreinterval.html"
last_updated: "7/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCDPShortTermRestoreInterval


Short Description

Returns short-term restore points of a Cloud Director CDP replica.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRvCDCDPShortTermRestoreInterval -Replica <VBRvCDCDPReplica>  [<CommonParameters>] |

Detailed Description

This cmdlet returns short-term restore points of a Cloud Director CDP replica.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica whose short-term restore point you want to get. | Accepts the VBRvCDCDPReplica object. To get this object, run the [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCDPShortTermRestoreInterval object that defines short-term restore point settings.

Examples

Getting Short-Term Restore Points of Cloud Director CDP Replica

This example shows how to get short-term restore points of a Cloud Director CDP replica.

|  |
| --- |
| $replica = Get-VBRCDPReplica  Get-VBRvCDCDPShortTermRestoreInterval -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Save the result to the $replica variable.
2. Run the Get-VBRvCDCDPShortTermRestoreInterval cmdlet. Set the $replica variable as the Replica parameter value.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)


