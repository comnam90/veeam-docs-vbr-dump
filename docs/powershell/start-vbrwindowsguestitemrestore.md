---
title: "Start-VBRWindowsGuestItemRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrwindowsguestitemrestore.html"
last_updated: "7/24/2024"
product_version: "13.0.1.1071"
---

# Start-VBRWindowsGuestItemRestore

In this article

Short Description

Starts restore of Microsoft Windows guest OS files and folders to the original or new location.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore files and folders from a backup to another machine in your infrastructure. Files and folders are specified using an array of file paths.

|  |
| --- |
| Start-VBRWindowsGuestItemRestore -Path <String[]> [-Session <CRestoreSession>] [-FileRestore <FileRestore>] -RestorePolicy <VBRWindowsGuestItemRestorePolicy> [-GuestCredentials <CCredentials>] [-TargetViVm <CViVmItem>] [-TargetVcdVm <CVcdVmItem>] [-TargetHvVm <CHvVmItem>] [-TargetAgentMachine <VBRDiscoveredComputer>] [-TargetDirectory <String>] [-PermissionsOnly] [-ChangedItemsOnly] [-RunAsync] [<CommonParameters>] |

* Restore files and folders from a backup to another machine in your infrastructure. Files and folders are specified using the Get-VBRWindowsGuestItem cmdlet.

|  |
| --- |
| Start-VBRWindowsGuestItemRestore -Item <VBRFLRFsItem[]> [-Session <CRestoreSession>] [-FileRestore <FileRestore>] -RestorePolicy <VBRWindowsGuestItemRestorePolicy> [-GuestCredentials <CCredentials>] [-TargetViVm <CViVmItem>] [-TargetVcdVm <CVcdVmItem>] [-TargetHvVm <CHvVmItem>] [-TargetAgentMachine <VBRDiscoveredComputer>] [-TargetDirectory <String>] [-PermissionsOnly] [-ChangedItemsOnly] [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet starts to restore Microsoft Windows guest OS files and folders to the original or new location.

|  |
| --- |
| Note |
| To restore guest OS files, you need to start the restore session by running the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies an array of file paths to files and folders that you want to restore.  Note: The parameter does not accept the mount server path. | String[] | True | Named | True (ByValue, |
| Item | Specifies an array of files and folders that you want to restore. The cmdlet will restore these files and folders. | Accepts the VBRFLRFsItem[] object. To create this object, run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RestorePolicy | Specifies the file restore policy:   * Keep: Use this option if you want to restore the files with the \_restored postfix next to the original file. * Overwrite: Use this option if you want to replace the original files with the restored files. | VBRWindowsGuestItemRestorePolicy | True | Named | False |
| Session | Specifies a session of Microsoft Windows guest OS file restore. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the FileRestore parameter is not specified. | Accepts the CRestoreSession object. To create this object, run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. | False | Named | False |
| FileRestore | Specifies a session of Microsoft Windows guest OS file restore. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the Session parameter is not specified. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | Named | False |
| GuestCredentials | Specifies credentials for the target machine.  Note: If you do not specify credentials, the cmdlet will try to use the credentials from the current PowerShell session. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TargetViVm | For restoring files and folders from a backup of a VMware vSphere VM.  Specifies a VMware vSphere VM (target VM) to which you want to restore files and folders. | Accepts the CViVmItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | False |
| TargetVcdVm | For restoring files and folders from a backup of a VMware Cloud Director VM.  Specifies a VMware Cloud Director VM (target VM) to which you want to restore files and folders. | Accepts the CVcdVmItem object. To create this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| TargetHvVm | For restoring files and folders from a backup of a Microsoft Hyper-V VM.  Specifies a Microsoft Hyper-V VM (target VM) to which you want to restore files and folders. | Accepts the CHvVmItem object. To create this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | False | Named | False |
| TargetAgentMachine | For performing restore to a Veeam Agent computer.  Specifies the target computer to which the cmdlet will restore guest OS files. | Accepts the VBRDiscoveredComputer object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | False |
| TargetDirectory | Specifies the path to a folder on the target VM to which you want to restore files. | String | False | Named | False |
| PermissionsOnly | Defines whether to restore only permissions of files and folders.  Note: This functionality is included in the Veeam Universal License. When using a legacy socket-based license, the Enterprise or Enterprise Plus editions of Veeam Backup & Replication are required. | SwitchParameter | False | Named | False |
| ChangedItemsOnly | Defines whether to restore changed files and folders only. Before restoring changes, you must launch [Compare-VBRWindowsGuestItemsAttributes](compare-vbrwindowsguestitemsattributes.md) for files and folders that youplan to restore.  Note: This functionality is included in the Veeam Universal License. When using a legacy socket-based license, the Enterprise or Enterprise Plus editions of Veeam Backup & Replication are required. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Windows Guest OS File to Original Windows Machine

|  |  |
| --- | --- |
| This example shows how to restore the January.xlsx file by specifying the C:\Projects\2020\January.xlsx file path. The cmdlet will restore the file to the original WinSrv25 Windows machine.  |  | | --- | | $session = Get-VBRRestoreSession -Name "Winserver\_restore"  Start-VBRWindowsGuestItemRestore -Path "C:\Projects\2020\January.xlsx" -Session $session[0] -RestorePolicy Overwrite |  Perform the following steps:   1. Run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. Specify the Name parameter value. Save the result to the $session variable. 2. Run the Start-VBRWindowsGuestItemRestore cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $session[0] variable as the Session parameter value.   The Get-VBRRestoreSession cmdlet will return an array of active restore sessions. Mind the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).   * Set the Overwrite option for the RestorePolicy parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Windows Guest OS File to Another Server

|  |  |
| --- | --- |
| This example shows how to restore the January.xlsx file to the winsrv27 VM.  |  | | --- | | $vm = Find-VBRViEntity -Name "winsrv27" -DatastoresAndVMs  $creds = Get-VBRCredentials -Name \*Administrator\*  $session = Get-VBRRestoreSession  Start-VBRWindowsGuestItemRestore -Path "C:\New Text Document.txt" -Session $session[0] -RestorePolicy Keep -GuestCredentials $creds -TargetViVm $vm -TargetDirectory "C:\" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Provide the DatastoresAndVMs parameter. Save the result to the $vm variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 3. Run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. Save the result to the $session variable. 4. Run the Start-VBRWindowsGuestItemRestore cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $session[0] variable as the Session parameter value.   The Get-VBRRestoreSession cmdlet will return an array of active restore sessions. Mind the ordinal number of the necessary restore session (in our example, it is the first restore session in the array).   * Set the Keep option for the RestorePolicy parameter. * Set the $creds variable as the GuestCredentials parameter value. * Set the $vm variable as the TargetViVm parameter value. * Specify the TargetDirectory parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)
* [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md)

Page updated 7/24/2024

Page content applies to build 13.0.1.1071
