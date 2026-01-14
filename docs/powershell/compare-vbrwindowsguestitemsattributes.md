---
title: "Compare-VBRWindowsGuestItemsAttributes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/compare-vbrwindowsguestitemsattributes.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Compare-VBRWindowsGuestItemsAttributes

In this article

Short Description

Compares attributes of files and folders from a backup with attributes of original files and folders.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Compare-VBRWindowsGuestItemsAttributes -FileRestore <FileRestore> -Item <VBRFLRFsItem>  [<CommonParameters>] |

Detailed Description

This cmdlet compares attributes of files and folders from a backup with attributes of original files and folders.

When Veeam Backup & Replication compares files, it compares their attributes. When Veeam Backup & Replication compares folders, it compares folder attributes and file attributes inside the folder recursively. Once a file with changed attributes is found, Veeam Backup & Replication stops comparing files and marks the folder as changed. If you further browse the folder in the compared state, Veeam Backup & Replication continues comparing non-compared files and folders. Veeam Backup & Replication compares the following attributes: Date Created, Date Modified, Size (only for files), Read-Only, Hidden, Archive, NTFS Encryption.

|  |
| --- |
| Note |
| Before comparing attributes, you must establish connection with the original machine using the [Connect-VBRWindowsGuestProductionMachine](connect-vbrwindowsguestproductionmachine.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FileRestore | Specifies a restore session of Microsoft Windows guest OS files. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | True | Named | False |
| Item | An array of files and folders whose attributes you want to compare. | Accepts the VBRFLRFsItem[] object. To create this object, run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRWindowsGuestItemAttributesView object that contains attributes of the compared files or folders.

Examples

Comparing Attributes of Files and Folders from Backup with Attributes of Original Files and Folders

This example shows how to compare attributes of files and folders.

|  |
| --- |
| $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  Connect-VBRWindowsGuestProductionMachine -FileRestore $session  $file = Get-VBRWindowsGuestItem -FileRestore $session -Path "C:\Documents\Training\SummerTraining2020.pdf"  Compare-VBRWindowsGuestItemsAttributes -FileRestore $session -Item $file |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore session in the array).

1. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.
2. Run the [Connect-VBRWindowsGuestProductionMachine](connect-vbrwindowsguestproductionmachine.md) cmdlet. Set the $session variable as the FileRestore parameter value.
3. Run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet. Set the $session variable as the FileRestore parameter value. Specify the Path parameter. Save the result to the $file variable.
4. Run the Compare-VBRWindowsGuestItemsAttributes cmdlet. Set the $session variable as the FileRestore parameter value. Set the $file variable as the Item parameter value.

Related Commands

* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)
* [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md)

Page updated 2/9/2024

Page content applies to build 13.0.1.1071
