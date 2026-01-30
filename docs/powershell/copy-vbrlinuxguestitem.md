---
title: "Copy-VBRLinuxGuestItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrlinuxguestitem.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRLinuxGuestItem


Short Description

Copies Linux-based or Unix-based guest OS files to the target host.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRLinuxGuestItem -Item <VBRFLRFsItem[]> -LinuxFlrObject <VBRLinuxFlrObject> -Server <CHost> -ShareCredentials <PSCredential> -TargetFolder <string> [-Datastore <VBRViDatastoreBase>] [-KeepPermissionsAndOwnership]  [<CommonParameters>] |

Detailed Description

This cmdlet copies Linux-based or Unix-based guest OS files to the target host. You can use the following types of servers and hosts as the target hosts:

* Microsoft Windows Server
* Linux Server
* VMware vSphere Server
* VMware Cloud Director Server

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of files and folders that are available on disks of Linux-based or Unix-based machines. The cmdlet will copy these files and folders. | Accepts the VBRFLRFsItem[] object. To create this object, run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. | True | Named | True (ByValue, |
| LinuxFlrObject | Specifies a restore session of Linux-based or Unix-based guest OS files. The cmdlet will use this session to copy guest OS files. | Accepts the VBRLinuxFlrObject object. To create this object, run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. | True | Named | False |
| Server | Specifies a target machine to which you want to copy guest OS files. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| ShareCredentials | For copying guest OS files to a shared folder.  Specifies credentials that you want to use to authenticate with the target shared folder to which you copy guest OS files. | Accepts the PSCredential object. To create this object, run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.3) cmdlet. | False | Named | False |
| TargetFolder | Specifies a folder in the target machine. The cmdlet will copy the guest OS files to this folder. | String | True | Named | False |
| Datastore | Specifies the datastore where the target machine will be located. The cmdlet will copy the guest OS files to the machine located in this datastore. | Accepts the VBRViDatastoreBase object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| KeepPermissionsAndOwnership | Defines that the cmdlet will keep custom permissions and the ownership of the copied guest OS files.  If you do not provide this parameter, the cmdlet will restore guest OS files with default permissions and ownership.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Copying Linux-Based or Unix-Based Guest OS Files to Target Host

This example shows how to copy files from the UbuntuSrv to the LinSrv07 target machine.

|  |
| --- |
| $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $items = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $targetserver = Get-VBRServer -Name "LinSrv07"  Copy-VBRLinuxGuestItem -Item $items -LinuxFlrObject $session -TargetFolder "/home/pictures" -Server $targetserver |

Perform the following steps:

1. Start the restore session:

* Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
* Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.
* Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
* Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable.

1. Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $items variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable.
3. Run the Copy-VBRLinuxGuestItem cmdlet. Specify the following settings:

* Set the $items variable as the Item parameter value.
* Set the $session variable as the LinuxFlrObject parameter value.
* Specify the TargetFolder parameter value.
* Set the $targetserver variable as the Server parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md)


