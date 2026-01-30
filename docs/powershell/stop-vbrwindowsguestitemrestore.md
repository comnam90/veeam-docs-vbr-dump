---
title: "Stop-VBRWindowsGuestItemRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrwindowsguestitemrestore.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRWindowsGuestItemRestore


Short Description

Stops Windows guest OS file restore session initiated with the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRWindowsGuestItemRestore -ItemSession <VBRItemSession>  [<CommonParameters>] |

Detailed Description

Stops Windows guest OS file restore session initiated with the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ItemSession | Specifies the running Windows guest OS file restore session that you want to stop. | Accepts the VBRItemSession object. To get this object, run the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet with the RunAsync parameter set. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Restore Session for Windows VM Guest OS Files

This example shows how to stop a restore session for Windows VM guest OS files. During the session, files are restored to the specified folder.

|  |
| --- |
| $backup = Get-VBRBackup  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint  $restoresession = Start-VBRWindowsGuestItemRestore -Path "C:\Files\" -FileRestore $session -RestorePolicy Keep -RunAsync  Stop-VBRWindowsGuestItemRestore -ItemSession $restoresession |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable.
3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.
4. Run the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet. Save the result to the $restoresession variable. Specify the following settings:

* Specify the Path parameter value.
* Set the $session variable as the FileRestore parameter value.
* Set the Keep option for the RestorePolicy parameter.
* Provide the RunAsync parameter.

1. Run the Stop-VBRWindowsGuestItemRestore cmdlet. Set the $restoresession variable as the ItemSession parameter value.


