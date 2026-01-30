---
title: "Get-VBRFCDInstantRecoveryInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfcdinstantrecoveryinfo.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFCDInstantRecoveryInfo


Short Description

Returns details on the mounting of virtual disks that are recovered within an FCD instant recovery session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRFCDInstantRecoveryInfo -Session <VBRFCDInstantRecoverySession>  [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the mounting of virtual disks that are recovered within an FCD instant recovery session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a session that is running to perform an FCD recovery. The cmdlet will return details on mounting of the virtual disks that are recovered within this session. | Accepts the VBRFCDInstantRecoverySession object. To create this object, run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. | True | 0 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFirstClassDiskInstantRecoveryInfo object that contains details on the mounting of virtual disks that are recovered within an FCD instant recovery session.

Examples

Getting Details on the Mounting of Virtual Disks Recovered Within FCD Instant Recovery Session

This example shows how to get details on the mounting of the virtual disks that that are recovered within the 49664A5F-9C55-4A1F-8E6A-1CD5705A684B FCD instant recovery session.

|  |
| --- |
| $session = Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  Get-VBRFCDInstantRecoveryInfo -Session $session |

Perform the following steps:

1. Run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
2. Run the Get-VBRFCDInstantRecoveryInfo cmdlet. Set the $session varialbe as the Session parameter value.

Related Commands

[Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md)


