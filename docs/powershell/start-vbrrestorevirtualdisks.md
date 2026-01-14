---
title: "Start-VBRRestoreVirtualDisks"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrrestorevirtualdisks.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Start-VBRRestoreVirtualDisks

In this article

Short Description

Restores disks from backups of physical or virtual machines and converts them to the VMDK, VHD or VHDX formats.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRRestoreVirtualDisks -RestorePoint <COib> -Server <CHost> -Path <string> -RestoreDiskType {Vmdk | Vhd | Vhdx} [-Datastore <VBRViDatastoreBase>] [-StorageFormat {Thin | Thick | EagerZeroedThick | Fixed | Dynamic}] [-Files <COIBFileInfo[]>] [-SourceShareCredentials <CCredentials>] [-TargetShareCredentials <CCredentials>] [-Reason <string>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-ProceedToRecoveryIfThreatFound] [-RunAsync] [-Proxy <CViProxy[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet restores disks from backups of physical or virtual machines and converts them to the VMDK, VHD or VHDX formats.

The cmdlet allows you to scan the disks that you want to restore with the antivirus.

Run the [Start-VBRRestoreVMFiles](start-vbrrestorevmfiles.md) cmdlet to restore VM configuration files.

|  |
| --- |
| Note |
| In case the antivirus detects the virus threat, Veeam Backup & Replication will cancel the restore session. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point from which you want to restore the disks.  You must select restore points only from Veeam Agent for Microsoft Windows volume-level backups. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Server | Specifies the Windows host to which the disks should be restored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| Path | Specifies the path to the folder on the target server. The cmdlet will register virtual disks in this folder. | String | True | 3 | False |
| RestoreDiskType | Specifies the format to which you want to convert the resulting virtual disk:   * VHD * VHDX * VMDK | EVirtualDiskRestoreType | False | Named | False |
| StorageFormat | Specifies the format that will be used to convert the resulting virtual disk:   * Thin: the resulting vmdk virtual disk will be thin. * Thick: the restresulting vmdk virtual disk will be thick lazy zeroed. * EagerZeroedThick: resulting vmdk virtual disk will be eager lazy zeroed. * Fixed: resulting vhd/vhdx virtual disk will be thick fixed. * Dynamic: resulting vhd/vhdx virtual disk will be dynamic.   Default: Source. | VBRStorageFormatType | False | Named | False |
| Datastore | Specifies a target datastore. The cmdlet will register converted disks to this datastore.  Note: You must provide the Path parameter to specify the path to the folder in the datastore where you want to keep the converted disks. You must create the necessary folder beforehand. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Files | Specifies the disks from the backup that you want to restore.  Default: all. | Accepts the COIBFileInfo[] object. To get this object, run the [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md) cmdlet. | False | Named | True (ByProperty Name) |
| SourceShareCredentials | Specifies the credentials for the backup repository. The cmdlet will export the backup from this repository. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TargetShareCredentials | Specifies the credentials for the shared folder. The cmdlet will add the exported files to that folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for performing the disk restore. | String | False | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected machines before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the option for the antivirus to continue physical discs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| ProceedToRecoveryIfThreatFound | For secure restore.  Defines that if antivirus detects malware, the cmdlet will restore physical disks. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Proxy | Specifies an array of VMware proxies. The cmdlet will use these proxies during the restore. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring All Physical Disks from Volume-Level Backups by Veeam Agent

|  |  |
| --- | --- |
| This example shows how to restore all physical disks from volume-level backups created by Veeam Agent operating in the standalone mode. The cmdlet will restore disks to a Veeam backup server. The disks are restored to the latest restore point. The resulting format is VMDK.  |  | | --- | | $server = Get-VBRLocalhost  $restorepoint = Get-VBRBackup -Name "Backup Job SRV03" | Get-VBRRestorePoint | Sort-Object -Property CreationTime | Select-Object -First 1  Start-VBRRestoreVirtualDisks -RestorePoint $restorepoint -Server $server -Path "C:\SRV03\_Restored" -RestoreDiskType Vmdk -RunAsync |  Perform the following steps:   1. Run the [Get-VBRLocalhost](get-vbrlocalhost.md) cmdlet. Save it to the $server variable. 2. Get the most recent restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet.  * Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value. * Pipe the cmdlet output to the Select-Object cmdlet. Specify the First parameter value.  * Save the result to the $restorepoint variable.  1. Run the Start-VBRRestoreVirtualDisks cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Set the Vmdk option for the RestoreDiskType parameter. * Provide the RunAsync parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Specified Disks to Windows Server

|  |  |
| --- | --- |
| This example shows how to restore specified disks to a Windows server added to Veeam Backup & Replication. The disks are restored to the latest restore point. The resulting format is VHDX.  |  | | --- | | $restorepoint = Get-VBRBackup -Name "Backup Job SRV03" | Get-VBRRestorePoint | Sort-Object -Property CreationTime | Select-Object -First 1  $server = Get-VBRServer -Type Windows -Name "Veeam\_Remote"  $disks = Get-VBRFilesInRestorePoint -RestorePoint $restorepoint  Start-VBRRestoreVirtualDisks -RestorePoint $restorepoint -Server $server -Path "C:\SRV03\_Restored" -RestoreDiskType Vhdx -Files $disks[1,3] -RunAsync |  Perform the following steps:   1. Get the most recent restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. * Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet.  * Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value. * Pipe the cmdlet output to the Select-Object cmdlet. Specify the First parameter value.  * Save the result to the $restorepoint variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the Windows option for the Type parameter. Specify the Name parameter value. Save it to the $server variable. 2. Run the [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disks variable. In this example, disks 1 and 3 will be restored. 3. Run the Start-VBRRestoreVirtualDisks cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value.  * Specify the Path parameter value. * Set the Vhdx option for the RestoreDiskType parameter.  * Set the $disks variable as the Files parameter value.   The Get-VBRFilesInRestorePoint cmdlet will return an array. Mind the ordinal number of the necessary item (in our example, it is the second and fourth items in the array).   * Provide the RunAsync parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Specified Disks to ESXi Host

|  |  |
| --- | --- |
| This example shows how to restore selected disks to the 172.17.42.11 ESXi host and register them on the srv07-DAS1 datastore.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  $rp = Get-VBRRestorePoint -Name \*MSExchange02\* -Backup $backup                  $server = Get-VBRServer -Name "172.17.42.11"  $datastore = Find-VBRViDatastore -Server "172.17.42.11" -Name "srv07-DAS1"  Start-VBRRestoreVirtualDisks -RestorePoint $rp -Server $server -Path "C:\MSEx02\_Restored" -Datastore $datastore -RestoreDiskType Vmdk -StorageFormat Thin |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. Save the result to the $rp variable. 3. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable. 5. Run the Start-VBRRestoreVirtualDisks cmdlet. Specify the following settings:  * Set the $rp variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value.  * Specify the Path parameter value.  * Set the $datastore variable as the Datastore parameter value.  * Set the Vmdk option for the RestoreDiskType parameter. * Set the Thin option for the StorageFormat parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
