---
title: "Copy-VBRWindowsGuestItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrwindowsguestitem.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRWindowsGuestItem

In this article

Short Description

Copies Microsoft Windows guest OS files to the target host.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRWindowsGuestItem -Item <VBRFLRFsItem[]> -TargetFolder <string> [-Session <CRestoreSession>] [-ShareCredentials <PSCredential>] [-FileRestore <FileRestore>] [-KeepPermissionsAndOwnership] [-GuestCredentials <CCredentials>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet copies Microsoft Windows guest OS files to the target host.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of Microsoft Windows guest OS files. The cmdlet will copy these files. | Accepts the VBRFLRFsItem[] object. To create this object, run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet. | True | Named | True (ByValue, |
| TargetFolder | Specifies a folder in the target machine. The cmdlet will copy the guest OS files to this folder. | String | True | Named | False |
| Session | Specifies a restore session of Microsoft Windows guest OS files. The cmdlet will use this session to copy guest OS files.  This parameter is required if the FileRestore parameter is not specified. | Accepts the CRestoreSession object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | Named | False |
| ShareCredentials | For copying guest OS files to a shared folder.  Specifies credentials that you want to use to authenticate with the target shared folder to which you copy guest OS files. | Accepts the PSCredential object. To create this object, run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.3) cmdlet. | False | Named | False |
| FileRestore | Specifies a restore session of Microsoft Windows guest OS files. The cmdlet will use this session to restore guest OS files.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the Session parameter is not specified. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | Named | False |
| KeepPermissionsAndOwnership | Defines that the cmdlet will keep custom permissions and the ownership of the copied guest OS files.  If you do not provide this parameter, the cmdlet will restore guest OS files with default permissions and ownership.  Default: False. | SwitchParameter | False | Named | False |
| GuestCredentials | Specifies the credentials of the target machine.  Note: If you do not specify credentials, the cmdlet will try to use the credentials from the current PowerShell session. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Copying Microsoft Windows Guest OS Files to Target Folder

This example shows how to copy files from the backup of the WinSrv25 Windows machine to the D:\Copies folder. The cmdlet will keep all custom permissions and ownership of the copied files.

|  |
| --- |
| $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint  $items = Get-VBRWindowsGuestItem -FileRestore $session -Name "Reports"  Copy-VBRWindowsGuestItem -Item $items -TargetFolder "D:\Copies" -FileRestore $session -KeepPermissionsAndOwnership |

Perform the following steps:

1. Get the restore session.

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable.
3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.

1. Run the [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md) cmdlet. Specify the $session variable as the FileRestore parameter value. Specify the Name parameter value. Save the result to the $items variable.
2. Run the Copy-VBRWindowsGuestItem cmdlet. Specify the following settings:

* Set the $items variable as the Item parameter value.
* Specify the TargetFolder parameter value.
* Set the $session variable as the FileRestore parameter value.
* Provide the KeepPermissionsAndOwnership parameter.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)
* [Get-VBRWindowsGuestItem](get-vbrwindowsguestitem.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
