---
title: "Stop-VBRLinuxGuestItemRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrlinuxguestitemrestore.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRLinuxGuestItemRestore


Short Description

Stops Linux guest OS file restore session initiated with the [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) cmdlet.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRLinuxGuestItemRestore -ItemSession <VBRItemSession>  [<CommonParameters>] |

Detailed Description

This cmdlet stops Linux-based or Unix-based guest OS file restore session initiated with the [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ItemSession | Specifies the running Linux guest OS file restore session that you want to stop. | Accepts the VBRItemSession object. To get this object, run the [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) cmdlet with the RunAsync parameter set. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Restore Session

This example shows how to stop a restore session. During the session Unix-based guest OS files of the UbuntuSrv VM are restored to the original host with the following settings:

* The cmdlet will overwrite existing files and folders.
* The cmdlet will use the LinSrv05 machine as a helper appliance.

|  |
| --- |
| $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  $child = Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root  $restoresession = Start-VBRLinuxGuestItemRestore -LinuxFlrObject $session -Item $child[3] -RunAsync  Stop-VBRLinuxGuestItemRestore -ItemSession $restoresession |

Perform the following steps:

1. Mount the disk and get the OS files:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.
3. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
4. Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as MountServer parameter value. Save the result to the $session variable.
5. Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable the LinuxFlrObject parameter value. Save the result to the $root variable.
6. Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as ParentItem parameter value. Save the result to the $child variable.

The Get-VBRLinuxGuestItem cmdlet will return an array of files and folders. Mind the ordinal number of the necessary item (in our example, it is the fourth item in the array).

1. Run the [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) cmdlet. Specify the LinuxFlrObject and Item parameter values. Specify the RunAsync parameter. Save the result to the $restoresession variable.
2. Run the Stop-VBRLinuxGuestItemRestore. Set the $restoresession variable as the ItemSession parameter value.


