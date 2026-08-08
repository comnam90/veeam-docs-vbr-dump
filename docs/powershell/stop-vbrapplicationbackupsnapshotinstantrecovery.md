---
title: "Stop-VBRApplicationBackupSnapshotInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrapplicationbackupsnapshotinstantrecovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VBRApplicationBackupSnapshotInstantRecovery


Short Description

Stops snapshot instant recovery session for an application backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRApplicationBackupSnapshotInstantRecovery -Session <VBRSession>  [<CommonParameters>] |

Detailed Description

This cmdlet stops a running instant recovery session from an application backup repository snapshot. Veeam Backup & Replication will unmount the snapshot and release all resources that were allocated for the instant recovery session.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Session | Specifies the instant recovery session that you want to stop. | Accepts the [VBRSession](vbrsession.md) object. To create this object, run the [Get-VBRSession](get-vbrsession.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Instant Recovery from Application Backup Repository Snapshot

This example shows how to stop an instant recovery session started from an application backup repository snapshot.

|  |
| --- |
| $session = Get-VBRSession -Id "0814a9b4-5fba-4f20-86dd-4790a5b659ab"  Stop-VBRApplicationBackupSnapshotInstantRecovery -Session $session |

Perform the following steps:

1. Run the [Get-VBRSession](get-vbrsession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
2. Run the Stop-VBRApplicationBackupSnapshotInstantRecovery cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRSession](get-vbrsession.md)

Page updated 2026-06-04

