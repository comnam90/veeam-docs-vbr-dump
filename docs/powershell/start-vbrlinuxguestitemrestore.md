---
title: "Start-VBRLinuxGuestItemRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrlinuxguestitemrestore.html"
last_updated: "12/11/2024"
product_version: "13.0.1.1071"
---

# Start-VBRLinuxGuestItemRestore


Short Description

Restores Linux-based or Unix-based guest OS files.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRLinuxGuestItemRestore -LinuxFlrObject <VBRLinuxFlrObject> -Item <VBRFLRFsItem[]> [-TargetDirectory <String>] [-Overwrite] [-GuestCredentials <CCredentials>] [-TargetViVm <CViVmItem>] [-TargetVcdVm <CVcdVmItem>] [-TargetHvVm <CHvVmItem>] [-TargetAgentMachine <VBRDiscoveredComputer>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores Linux-based or Unix-based guest OS files to the original or new location.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinuxFlrObject | Specifies a restore session of Linux-based or Unix-based guest OS files. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session. | Accepts the VBRLinuxFlrObject object. To create this object, run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. | True | Named | True (ByValue, |
| Item | Specifies the array of files and folders that are available on disks of Linux-based or Unix-based machines. The cmdlet will restore these files and folders. | Accepts the VBRFLRFsItem[] object. To get this object, run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. | True | Named | False |
| TargetDirectory | Specifies the path to a folder on the target VM to which you want to restore files. | String | False | Named | False |
| Overwrite | Defines that the cmdlet will overwrite existing files and folders with files and folders from a backup.  If you set this parameter to the $false value, the cmdlet will not replace exiting files and folders. It will add the restored files and folders with the \_restored postfix to the target machine. | SwitchParameter | True | Named | False |
| GuestCredentials | Specifies the credentials to authenticate against the target machine. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TargetViVm | For performing restore to the VMware platform.  Specifies the target machine to which the cmdlet will restore guest OS files.  Note: This parameter will work only if source machine is restored or deleted. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| TargetVcdVm | For performing restore to the Cloud Director platform.  Specifies the target machine to which the cmdlet will restore guest OS files.  Note: This parameter will work only if source machine is restored or deleted. | Accepts the CVcdVmItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| TargetHvVm | For performing restore to the Hyper-V platform.  Specifies the target machine to which the cmdlet will restore guest OS files.  Note: This parameter will work only if source machine is restored or deleted. | Accepts the CHvVmItem object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| TargetAgentMachine | For performing restore to a Veeam Agent computer.  Specifies the target computer to which the cmdlet will restore guest OS files. | Accepts the VBRDiscoveredComputer object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CRestoreTaskSession object that contains setting of an operation that you perform to restore Linux-based or Unix-based guest OS files to the source machine.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Linux-Based or Unix-Based Guest OS Files to Original Location

|  |  |
| --- | --- |
| This example shows how to restore Linux-based or Unix-based guest OS files of the UbuntuSrv VM to the original host with the following settings:   * The cmdlet will overwrite existing files and folders. * The cmdlet will use the LinSrv05 machine as a helper appliance.   |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $creds = Get-VBRCredentials  Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -GuestCredentials $creds -Overwrite |  Perform the following steps:   1. Mount the disk and get the OS files:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. Save the result to the $child variable.   The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Consider that the array numbering starts with 0. In our example, the fourth item in the array is used.   * Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable.  1. Run the Start-VBRLinuxGuestItemRestore cmdlet. Specify the following settings:  * Set the $session variable as the LinuxFlrObject parameter value. * Set the $child variable as the Item parameter value. * Set the $creds variable as the GuestCredentials parameter value. * Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Linux-Based or Unix-Based Guest OS Files to VMware Platform

|  |  |
| --- | --- |
| This example shows how to restore Linux-based or Unix-based guest OS files of the UbuntuSrv VM to the UbuntuSrv07 that is located on the VMware platform with the following settings:   * The cmdlet will add the restored files and folders with the \_restored postfix to the UbuntuSrv VM. * The cmdlet will use the LinSrv05 machine as a helper appliance.   |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $targetvm = Find-VBRViEntity -Name UbuntuSrv07  Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -TargetViVm $targetvm -Overwrite |  Perform the following steps:   1. Mount the disk and get the OS files:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. Save the result to the $child variable.   The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Consider that the array numbering starts with 0. In our example, the fourth item is used.   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $targetvm variable.  1. Run the Start-VBRLinuxGuestItemRestore cmdlet. Specify the following settings:  * Set the $session variable as the LinuxFlrObject parameter value. * Set the $child variable as the Item parameter value. * Set the $targetvm variable as the TargetViVm parameter value. * Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Linux-Based or Unix-Based Guest OS Files to Cloud Director Platform

|  |  |
| --- | --- |
| This example shows how to restore Linux-based or Unix-based guest OS files of the UbuntuSrv VM to the UbuntuSrv04 that is located on the Cloud Director platform. The cmdlet will add the restored files and folders with the \_restored postfix to the UbuntuSrv04 VM.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $mountserver = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $mountserver  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $targetvm = Find-VBRvCloudEntity -Name "UbuntuSrv04"  Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -TargetVcdVm $targetvm -Overwrite:$false |  Perform the following steps:   1. Start the restore session and get the OS files:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $mountserver variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. Save the result to the $child variable.   The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Consider that the array numbering starts with 0. In our example, the fourth item is used.   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $targetvm variable.  1. Run the Start-VBRLinuxGuestItemRestore cmdlet. Specify the following settings:  * Set the $session variable as the LinuxFlrObject parameter value. * Set the $items variable as the Item parameter value. * Set the $targetvm variable as the TargetVcdVm parameter value. * Set the Overwrite parameter value to $false. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restoring Linux-Based or Unix-Based Guest OS Files to Hyper-V Platform

|  |  |
| --- | --- |
| This example shows how to restore Linux-based or Unix-based guest OS files of the UbuntuSrv VM to the UbuntuSrv07 that is located on the Hyper-V platform. The cmdlet will add the restored files and folders with the \_restored postfix to the UbuntuSrv VM.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $targetvm = Find-VBRHvEntity -HostsAndVMs -Name "UbuntuSrv07"  Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -TargetHvVm $targetvm -Overwrite:$false |  Perform the following steps:   1. Start the restore session and get the OS files:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable.   The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Consider that the array numbering starts with 0. In our example, the fourth item is used.   * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. Save the result to the $child variable.  1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $targetvm variable.  1. Run the Start-VBRLinuxGuestItemRestore cmdlet. Specify the following settings:  * Set the $session variable as the LinuxFlrObject parameter value. * Set the $items variable as the Item parameter value. * Set the $targetvm variable as the TargetHvVm parameter value. * Set :$false as the Overwrite parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Restoring Veeam Agent Files to Another Veeam Agent Computer

|  |  |
| --- | --- |
| This example shows how to restore Linux-based or Unix-based guest OS files of an UbuntuSrv computer to the computer in the UbuntuAgent protection group.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $group = Get-VBRProtectionGroup -Name "UbuntuAgent"  $targetmachine = Get-VBRDiscoveredComputer -ProtectionGroup $group  Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -TargetAgentMachine $targetmachine -Overwrite |  Perform the following steps:   1. Start the restore session and get the OS files:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable.   The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Consider that the array numbering starts with 0. In our example, the fourth item is used.   * Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. Save the result to the $child variable.  1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. 3. Run the Start-VBRLinuxGuestItemRestore cmdlet. Specify the following settings:  * Set the $session variable as the LinuxFlrObject parameter value. * Set the $child[3] variable as the Item parameter value. * Set the $targetmachine variable as the TargetAgentMachine parameter value. * Specify the Overwrite parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrrestorepoint.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [Find-VBRHvEntity](find-vbrhventity.md)


