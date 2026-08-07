---
title: "Start-VBRTapeRestore (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtaperestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBRTapeRestore (obsolete)


Short Description

Starts VM or database plug-in backups restore from tape.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but it is recommended to perform the tape restore operation with Veeam Backup & Replication UI for full functionality. |

Applies to

Platform: VMware, Hyper-V

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a restore session for database plug-in backups stored on tape.

|  |
| --- |
| Start-VBRTapeRestore -DbPluginRestorePoint <VBRTapeDbPluginRestorePoint[]> -Repository <CBackupRepository> [-Reason <String>] [-RunAsync] [<CommonParameters>] |

* Start a restore session to restore VMs to a chosen folder on a server.

|  |
| --- |
| Start-VBRTapeRestore -Path <String> -RestorePoint <COib[]> [-Reason <String>] [-RunAsync] -Server <CHost> [<CommonParameters>] |

* Start a restore session to restore VMs to a chosen backup repository.

|  |
| --- |
| Start-VBRTapeRestore -Repository <CBackupRepository> -RestorePoint <COib[]> [-Reason <String>] [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet starts restoring VMs from backup copied to tape.

You can restore VMs to a chosen backup repository or to a folder on the server you specify. Choose an appropriate syntax for each option.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies the particular restore points of the VM.  You can assign multiple restore points to this object. | Accepts the COib[] object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Repository | Specifies the backup repository where you want to restore the VM. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| DbPluginRestorePoint | Specifies the restore points of database plug-in backups stored on tape. | Accepts the VBRTapeDbPluginRestorePoint[] object. To get this object, run the [Get-VBRTapeDbPluginRestorePoint](get-vbrtapedbpluginrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Reason | Specifies the reason for restore. | String | False | Named | False |
| Server | Specifies the server where you want to restore the VM. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder where you want to restore the VM. | String | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting VM Restore from Tape to Specific Backup Repository

|  |  |
| --- | --- |
| This example shows how to start restoring the VM01 VM to a specified backup repository.  |  | | --- | | $backup = Get-VBRBackup -Id "d6b08a78-f405-400a-bb02-a132cf1778fa"  $repository = Get-VBRBackupRepository -Name "Backups Vol2"  Get-VBRRestorePoint -Backup $backup | Where {$\_.Name -eq "VM01"} | Select -First 1 | Start-VBRTapeRestore -Repository $repository -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Id parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. 4. Pipe the cmdlet output to the Where cmdlet to filter restore points by the Name property. 5. Pipe the cmdlet output to the Select cmdlet and specify the First parameter value. 6. Run the Start-VBRTapeRestore cmdlet. Set the $repository variable as the Repository parameter value. Specify the Reason parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting VM Restore from Tape to Specific Server

|  |  |
| --- | --- |
| This example shows how to start restoring the VM01 VM to a specified server.  |  | | --- | | $rpoint = Get-VBRRestorePoint -Id 2ee79fec-9aa8-4058-a147-ff6b76ef2924  $server = Get-VBRServer -Name "srv001"  Start-VBRTapeRestore -RestorePoint $rpoint -Server $server -Path "c:\Restored' -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $rpoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Start-VBRTapeRestore cmdlet. Specify the following settings:  * Set the $rpoint variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Provide the RunAsync parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 2026-06-05

