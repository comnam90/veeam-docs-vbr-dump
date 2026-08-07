---
title: "Start-VBRApplicationBackupSnapshotRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrapplicationbackupsnapshotrecovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRApplicationBackupSnapshotRecovery


Short Description

Starts recovery from an application backup repository snapshot.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRApplicationBackupSnapshotRecovery -Snapshot <VBRApplicationBackupSnapshot> [-Reason <String>] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a recovery session from an application backup repository snapshot. Veeam Backup & Replication will revert the snapshot to export its data by its original NFS path.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Snapshot | Specifies the snapshot from which you want to recover the application backup repository. | Accepts the [VBRApplicationBackupSnapshot](vbrapplicationbackupsnapshot.md) object. To get this object, run the [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md) cmdlet. | True | Named | False |
| Reason | Specifies the reason for starting recovery. The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| Force | Defines that the cmdlet will start recovery without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the cmdlet will run the recovery operation asynchronously. The cmdlet returns a session object immediately without waiting for the recovery to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that contains information about the recovery session.

Examples

Starting Recovery from Application Backup Repository Snapshot

This example shows how to start recovery from an application backup repository snapshot.

|  |
| --- |
| $snapshot = Get-VBRApplicationBackupSnapshot -Name "ApplicationBackupSnapshot01"  Start-VBRApplicationBackupSnapshotRecovery -Snapshot $snapshot |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable.
2. Run the Start-VBRApplicationBackupSnapshotRecovery cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

[Get-VBRApplicationBackupSnapshot](get-vbrapplicationbackupsnapshot.md)

Page updated 2026-06-04

