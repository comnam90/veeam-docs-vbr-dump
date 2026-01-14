---
title: "Connect-VBRWindowsGuestProductionMachine"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrwindowsguestproductionmachine.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRWindowsGuestProductionMachine

In this article

Short Description

Connects to the machine where original files and folders reside.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRWindowsGuestProductionMachine -FileRestore <FileRestore> [-GuestCredentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

Connects to the machine where original files and folders reside. You must launch this cmdlet before comparing files and folders using the [Compare-VBRWindowsGuestItemsAttributes](compare-vbrwindowsguestitemsattributes.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FileRestore | Specifies a restore session of Microsoft Windows guest OS files. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | True | Named | False |
| GuestCredentials | Specifies credentials for the original machine.  Note: If you do not specify credentials, the cmdlet will try to use the credentials specified in the backup job that created the backup. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Connecting to Machine Where Files to Restore Reside

This example shows how to connect to a machine whose files you restore.

|  |
| --- |
| $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint[1]  Connect-VBRWindowsGuestProductionMachine -FileRestore $session |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore session in the array).

1. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.
2. Run the Connect-VBRWindowsGuestProductionMachine cmdlet. Set the $session variable as the FileRestore parameter value.

Related Commands

* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 2/9/2024

Page content applies to build 13.0.1.1071
