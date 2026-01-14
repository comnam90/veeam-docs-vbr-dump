---
title: "Get-VBRWindowsGuestItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrwindowsguestitem.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBRWindowsGuestItem

In this article

Short Description

Returns Microsoft Windows guest OS files.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get top-level disks of the Microsoft Windows machines.

|  |
| --- |
| Get-VBRWindowsGuestItem [-Session <CRestoreSession>] [-FileRestore <FileRestore>] [-ChangedOnly] [-CompareWithOriginal] [-RunAsync]  [<CommonParameters>] |

* Get an array of guest OS files of the Microsoft Windows machines by specifying their file paths.

|  |
| --- |
| Get-VBRWindowsGuestItem [-Session <CRestoreSession>] [-FileRestore <FileRestore>] [-Path <string[]>] [-ChangedOnly] [-CompareWithOriginal] [-RunAsync]  [<CommonParameters>] |

* Get guest OS files and folders of the Microsoft Windows machines.

|  |
| --- |
| Get-VBRWindowsGuestItem [-Session <CRestoreSession>] [-FileRestore <FileRestore>] [-ParentItem <VBRFLRItem>] [-Name <string[]>] [-RecursiveSearch] [-ChangedOnly] [-CompareWithOriginal] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet returns guest OS files and folders of the Microsoft Windows machines.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a running restore session of Microsoft Windows VMs guest OS files. The cmdlet will return disks of Microsoft Windows machines for which you run a restore session.  This parameter is required if the FileRestore parameter is not specified. | Accepts the CRestoreSession object. To create this object, run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| FileRestore | Specifies a restore session of Microsoft Windows guest OS files. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the Session parameter is not specified. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Path | Specifies an array of file paths to the items that you want to restore. | String[] | False | Named | True (ByPropertyName) |
| ParentItem | For getting child items from disks.  Returns child guest OS files of Microsoft Windows machines. | Accepts the VBRFLRItem object. To create this object, run the Get-VBRWindowsGuestItem cmdlet. | False | Named | True (ByPropertyName) |
| Name | Specifies an array of names for guest OS files of Microsoft Windows machines. The cmdlet will return guest OS files with these names. | String[] | False | Named | True (ByPropertyName) |
| RecursiveSearch | Defines that the cmdlet will look for guest OS files that are added to the specified folders and to all child folders.  If you provide this parameter, the cmdlet will return an array of all guest OS files of Microsoft Windows machines. Otherwise, the cmdlet will return an array of guest OS that are added to the parent folder in Microsoft Windows machines. | SwitchParameter | False | Named | False |
| ChangedOnly | For the CompareWithOriginal parameter.  Defines that the cmdlet will return files and folders with changed attributes only. | SwitchParameter | False | Named | False |
| CompareWithOriginal | For the ChangedOnly parameter.  Note: Before comparing attributes, you must establish connection with the original machine using the [Connect-VBRWindowsGuestProductionMachine](connect-vbrwindowsguestproductionmachine.md) cmdlet.  Defines that Veeam Backup & Replication compares attributes of files and folders from the current restore session with attributes of original files and folders. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFLRItem object that contains files and folders that are available for restore in Microsoft Windows machines.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Disks of Microsoft Windows Machine

|  |  |
| --- | --- |
| This example shows how to get all top-level disks of the WinSrv25 Microsoft Windows machine.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  Get-VBRWindowsGuestItem -FileRestore $session |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter values. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Set the $session variable as the FileRestore parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting File Available in Microsoft Windows Machine by Providing File Path

|  |  |
| --- | --- |
| This example shows how to get the SummerTraining2020.pdf file by providing the C:\Documents\Training\SummerTraining.pdf file path. The cmdlet will get this file from a backup of the WinSrv25 Microsoft Windows machine.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  Get-VBRWindowsGuestItem -FileRestore $session -Path "C:\Documents\Training\SummerTraining2020.pdf" |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter values. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Set the $session variable as the FileRestore parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific File Available in Folder of Microsoft Windows Machine

|  |  |
| --- | --- |
| This example shows how to get the CyclingTripJuly file from a backup of the WinSrv25 Microsoft Windows machine. The cmdlet will look for this file in the Vacation folder.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  $items = Get-VBRWindowsGuestItem -FileRestore $session -Name "Vacation"  Get-VBRWindowsGuestItem -FileRestore $session -ParentItem $items[1] -Name "CyclingTripJuly" |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter values. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Set the $session variable as the FileRestore parameter value. Specify the Name parameter value. Save the result to the $items variable. 2. Run the Get-VBRWindowsGuestItem cmdlet. Specify the following settings:  * Set the $session variable as the FileRestore parameter value. * Set the $items variable as the ParentItem parameter value. * Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Specific File Available in Folder and Its Subfolders in Microsoft Windows Machine

|  |  |
| --- | --- |
| This example shows how to get the AutumnReport file from a backup of the WinSrv25 Microsoft Windows machine. The cmdlet will look for this file in the Reports folder and its subfolders.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  $items = Get-VBRWindowsGuestItem -FileRestore $session -Name "Reports"  Get-VBRWindowsGuestItem -FileRestore $session -ParentItem $items[1] -Name "AutumnReport" -RecursiveSearch |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter values. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Set the $session variable as the FileRestore parameter value. Specify the Name parameter values. Save the result to the $items variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Specify the following settings:  * Set the $session variable as the FileRestore parameter value. * Set the $items variable as the ParentItem parameter value. * Specify the Name parameter value. * Provide the RecursiveSearch parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Specific File or Folder in Microsoft Windows Machine

|  |  |
| --- | --- |
| This example shows how to search for the file or folder named SummerTraining2020. The cmdlet will get this file from a backup of the WinSrv25 Microsoft Windows machine.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint  Get-VBRWindowsGuestItem -FileRestore $session -Name "SummerTraining2020" |  Perform the following steps:   1. Get the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter values. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Get-VBRWindowsGuestItem cmdlet. Set the $session variable as the FileRestore parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
