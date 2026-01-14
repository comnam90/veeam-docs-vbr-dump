---
title: "Start-VBRWindowsFileRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrwindowsfilerestore.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Start-VBRWindowsFileRestore

In this article

Short Description

Starts Windows VM guest OS file restore session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRWindowsFileRestore -RestorePoint <COib> [-Host <CHost>] [-ResourcePool <CViResourcePoolItem>] [-Folder <CViFolderItem>] [-Reason <string>] [-Credentials <CCredentials>] [-ShareCredentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session of Windows VM guest OS files.

The cmdlet mounts disks of a machine from the backup or replica to the mount server. After that you can perform the following actions:

1. Run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet to get details on the files and folders that are available for restore.
2. Run the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet to restore the necessary files and folders.

After you restore the necessary files, you must stop the restore session. After you stop the session, Veeam Backup & Replication will unmount disks from the mount server. Run the [Stop-VBRWindowsFileRestore](stop-vbrwindowsfilerestore.md) cmdlet to stop the restore session.

|  |
| --- |
| Tip |
| To start a restore session for a CDP replica, use the [Start-VBRCDPWindowsFileRestore](start-vbrcdpwindowsfilerestore.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to start a restore session. You will be able to use the session to perform operations with machine guest OS files. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| Host | Specifies the mount server to which machine disks will be mounted.  Note: This parameter works only if you start a restore session of machine disks located on storage that use the Direct SAN access transport mode.  If you start a restore session of machine disks located on storage that use the other transport mode methods, the cmdlet will mount machine disks to the source storage. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | 2 | False |
| MountHost | Specifies the mount server to which machine disks will be mounted. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ResourcePool | Specifies a resource pool. The cmdlet will register the mount server to this resource pool. | Accepts the CViResourcePoolItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | 3 | False |
| Folder | Specifies a folder on the mount server. The cmdlet will place the machine disks under this folder. | Accepts the CViFolderItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md)  cmdlet. | False | 4 | False |
| Reason | Specifies the reason for starting a restore session of machine guest OS files.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| ShareCredentials | Specifies the credentials that will be used to access the shared folder. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Credentials | Note: This parameter is obsolete. Use the ShareCredentials paramter instead,  Specifies the credentials to authenticate with the backup share folder. | Accepts the CCredentials object. To create this object, run the  [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the FileRestore object that contains settings of a restore session of Windows guest OS files.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session for Windows Guest OS Files

|  |  |
| --- | --- |
| This example shows how to start a restore session for Windows guest OS files of the WinSrv25 machine.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1] |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore session in the array).   1. Run the Start-VBRWindowsFileRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session for Windows Guest OS Files from Latest Restore Point [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start a restore session for Windows guest OS files of the WinSrv25 machine. The cmdlet will use the latest restore point to start restore of Windows guest OS files.  |  | | --- | | Get-VBRBackup -Name "WinSrv25" | Get-VBRRestorePoint | Sort-Object –Property CreationTime –Descending | Select-Object -First 1 | Start-VBRWindowsFileRestore |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set the 1 number as the First parameter value. 5. Pipe the cmdlet output to the Start-VBRWindowsFileRestore cmdlet. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
