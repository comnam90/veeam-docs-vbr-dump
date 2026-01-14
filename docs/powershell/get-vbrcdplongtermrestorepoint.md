---
title: "Get-VBRCDPLongTermRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdplongtermrestorepoint.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPLongTermRestorePoint

In this article

Short Description

Returns a long-term restore point of VM replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCDPLongTermRestorePoint -Replica <VBRCDPReplica> [-ApplicationConsistent] [-Last]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a long-term restore point of VM replicas.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a VM protected with CDP which long-term restore points you want to get. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ApplicationConsistent | Defines that the cmdlet will return only application-consistent restore points. If you do not provide this parameter, the cmdet will also return crash-consistent restore points. | SwitchParameter | False | Named | False |
| Last | Defines that the cmdlet will return only the last restore point. If you do not provide this parameter, the cmdet will return all restore points. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPLongTermRestorePoint object that returns a long-term restore point of VM replicas.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all VM Replicas Long-Term Restore Points

|  |  |
| --- | --- |
| This command returns all long-term restore points that are available for the WinK0t VM protected with CDP.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "WinK0t"  Get-VBRCDPLongTermRestorePoint -Replica $replica |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Get-VBRCDPLongTermRestorePoint cmdlet. Set the $replica variable as the Replica parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Application-Consistent Restore Points for VM Protected with CDP

|  |  |
| --- | --- |
| This command returns all application-consistent restore points that are available for the WinK0t VM protected with CDP.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "WinK0t"  Get-VBRCDPLongTermRestorePoint -Replica $replica -ApplicationConsistent |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Get-VBRCDPLongTermRestorePoint cmdlet. Set the $replica variable as the Replica parameter. Provide the ApplicationConsistent parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Last Long-Term Restore Points for VM Protected with CDP

|  |  |
| --- | --- |
| This command returns the last restore point that is available for the WinK0t VM protected with CDP.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "WinK0t"  Get-VBRCDPLongTermRestorePoint -Replica $replica -Last |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Get-VBRCDPLongTermRestorePoint cmdlet. Set the $replica variable as the Replica parameter. Provide the Last parameter. |

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
