---
title: "Start-VBRViVirtualDiskRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvivirtualdiskrestore.html"
last_updated: "12/5/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViVirtualDiskRestore


Short Description

Starts VMware VM virtual disk restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViVirtualDiskRestore -RestorePoint <COib> -VirtualDeviceMapping <VBRViVirtualDeviceMappingRule[]> [-TargetVM <CViVmItem>] [-ShareCredentials <CCredentials>] [-DiskType <VBRViDiskType>] [-QuickRollback] [-Proxy <CViProxy[]>] [-Reason <String>] [-PowerOn] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-AbortRecovery] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a VMware VM virtual disk restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of VMs. The cmdlet will restore virtual disks of these VMs. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| VirtualDeviceMapping | Specifies an array of mapping settings for backed-up virtual disks. The cmdlet will attach virtual disks to the datastore according to these settings. | Accepts the VBRViVirtualDeviceMappingRule[] object. To create this object, run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. | True | Named | False |
| TargetVM | Specifies a target VM. The cmdlet will attach restored virtual disks to this VM. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| ShareCredentials | For restore to different VM.  Specifies credentials that you want to use to authenticate with the VM to which you attach restored virtual disks. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| DiskType | Specifies the virtual disk type settings. The cmdlet will set the virtual disks types to the specified type during the restore. You can specify one of the following disk types:   * AsSource * Thin * LazyZeroed * EagerZeroed   Default: AsSource | VBRViDiskType | False | Named | False |
| QuickRollback | Defines that the cmdlet will apply the quick rollback option. Use this option if you want to restore virtual disks to the original location and with original format. | SwitchParameter | False | Named | False |
| Proxy | Specifies the backup proxy that the cmdlet will use to transport the restored data to the to the target datastore. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | False | Named | False |
| Reason | Specifies a reason for performing restore of virtual disks. | String | False | Named | False |
| PowerOn | Defines that the cmdlet will start VMs immediately after the restore process is complete. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue VMs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| AbortRecovery | Defines that the cmdlet will cancel the restore session when the infection is detected. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform restore of VM virtual disks even if the geographic location of the repository where backups of VM virtual disks reside and the target host location does not match. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Starting Restore of Backed-Up Virtual Disks

This example shows how to start restore virtual disks of the VM that is backed up by the Winsrv4515 job. The cmdlet will attach virtual disks to the original VM.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $rule1 = New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice $disks[0]  $rule2 = New-VBRViVirtualDeviceMappingRule -SourceVirtualDevice $disks[1]  $mappingrules = $rule1, $rule2  Start-VBRViVirtualDiskRestore -RestorePoint $restorepoint -VirtualDeviceMapping $mappingrules |

Perform the following steps:

1. Get the backed-up VM virtual disks:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point will be used.

1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Specify the RestorePoint parameter value. Save the result to the $disks variable.

The Get-VBRViVirtualDevice cmdlet will return an array of disks. Consider that the array numbering starts with 0. In our example, the first and second disks will be used.

1. Create a list of mapping rules:

1. Run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. Specify the SourceVirtualDevice parameter value. Save the result to the $rule1 variable.
2. Run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. Specify the SourceVirtualDevice parameter value. Save the result to the $rule2 variable.
3. Save the $rule1 and $rule2 variables as a list into the $mappingrules variable.

1. Run the Start-VBRViVirtualDiskRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $mappingrules variable as the VirtualDeviceMapping parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)
* [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md)


