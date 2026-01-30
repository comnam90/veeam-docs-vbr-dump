---
title: "Stop-VBRInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrinstantrecovery.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRInstantRecovery


Short Description

Stops running Instant Recovery sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRInstantRecovery -InstantRecovery <InstantRecovery[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops publishing a workload within Instant Recovery processes (including Instant Recovery for first class disks, file shares and so on; does not include Instant Recovery to Microsoft Azure).

With instant recovery technology, Veeam Backup & Replication starts a workload directly from a backup, incremental or full, without copying it to production storage. You need to finalize the successful instant recovery by either migrating the recovered workload to production or by stopping publishing the recovered workload.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies an array of IDs of the running Instant Recovery sessions that you want to stop. | Accepts the InstantRecovery[] object. To create this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Stopping Last Instant Recovery Session

|  |  |
| --- | --- |
| This command stops the last instant recovery session. The needed session object is obtained with [Get-VBRInstantRecovery](get-vbrinstantrecovery.md), selected by order and piped down.  |  | | --- | | Get-VBRInstantRecovery | Select -Last 1 | Stop-VBRInstantRecovery |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Select the last instant recovery session. 2. Pipe the cmdlet output to the Stop-VBRInstantRecovery cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Stopping Specific Instant Recovery Session

|  |  |
| --- | --- |
| This command stops a specific instant recovery session.  |  | | --- | | $RecoverySession = Get-VBRInstantRecovery -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  Stop-VBRInstantRecovery -InstantRecovery $RecoverySession |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $RecoverySession variable. 2. Run the Stop-VBRInstantRecovery cmdlet. Set the $RecoverySession variable as the InstantRecovery parameter value. |

Related Commands

[Get-VBRInstantRecovery](get-vbrinstantrecovery.md)


