---
title: "Get-VBRvCDCDPLongTermRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcdplongtermrestorepoint.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCDPLongTermRestorePoint


Short Description

Returns long-term restore points of a Cloud Director CDP replica.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRvCDCDPLongTermRestorePoint -Replica <VBRvCDCDPReplica> [-ApplicationConsistent] [-Last]  [<CommonParameters>] |

Detailed Description

This cmdlet returns long-term restore points of a Cloud Director CDP replica.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica whose long-term restore point you want to get. | Accepts the VBRvCDCDPReplica object. To get this object, run the [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ApplicationConsistent | Defines that the cmdlet will return only application-consistent restore points. | SwitchParameter | False | Named | False |
| Last | Defines that the cmdet will return only the latest long-term restore points. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCDPLongTermRestorePoint object that defines long-term restore point settings.

Examples

Getting Long-Term Restore Points of Cloud Director CDP Replica

This cmdlet returns long-term restore points of a Cloud Director CDP replica.

|  |
| --- |
| $replica = Get-VBRCDPReplica  Get-VBRvCDCDPLongTermRestorePoint -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Save the result to the $replica variable.
2. Run the Get-VBRvCDCDPLongTermRestorePoint cmdlet. Set the $replica variable as the Replica parameter value.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)


