---
title: "Restart-VBRInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/restart-vbrinstantrecovery.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Restart-VBRInstantRecovery

In this article

Short Description

Restarts a failed Hyper-V Instant Recovery session.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VBRInstantRecovery -InstantRecovery <InstantRecovery[]>  [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed Hyper-V Instant Recovery session started with the [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) cmdlet.

Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet to get the status of the Instant Recovery session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the array of the instant recovery sessions. The cmdlet will restart these sessions. | Accepts the InstantRecovery[] object. To get this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restarting Last Instant Recovery Session [Using Pipeline]

|  |  |
| --- | --- |
| This command restarts the last instant recovery session.  |  | | --- | | Get-VBRInstantRecovery | Select -Last 1 | Restart-VBRInstantRecovery |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Select the last instant recovery session. 2. Pipe the cmdlet output to the Restart-VBRInstantRecovery cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restarting Specific Instant Recovery Session [Using Variable]

|  |  |
| --- | --- |
| This command restarts a specific instant recovery session.  |  | | --- | | $RecoverySession = Get-VBRInstantRecovery -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  Restart-VBRInstantRecovery -InstantRecovery $RecoverySession |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $RecoverySession variable. 2. Run the Restart-VBRInstantRecovery cmdlet. Set the $RecoverySession variable as the InstantRecovery parameter value. |

Related Commands

[Get-VBRInstantRecovery](get-vbrinstantrecovery.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
