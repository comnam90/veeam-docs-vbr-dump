---
title: "Mount-VBRWindowsFileRestoreItems"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/mount-vbrwindowsfilerestoreitems.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Mount-VBRWindowsFileRestoreItems

In this article

Short Description

Mounts disks of VMs for which restore is launched to the Veeam Backup & Replication console.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Mount-VBRWindowsFileRestoreItems [-Session <CRestoreSession>] [-FileRestore <FileRestore>]  [<CommonParameters>] |

Detailed Description

This cmdlet mounts disks of VMs for which restore is launched to the Veeam Backup & Replication console. After the disks are mounted, you can use Microsoft Windows File Explorer to work with restored files and folders. By default, the disks are mounted to the C:\VeeamFLR\ folder.

|  |
| --- |
| Note |
| It is recommended that you use Microsoft Windows File Explorer only to view file content, not to restore files. For guest OS file restore, use the [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a session of Microsoft Windows guest OS file restore. The cmdlet will mount disks of the VMs for which the restore sessions was launched to the Veeam Backup & Replication console.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the FileRestore parameter is not specified. | Accepts the CRestoreSession object. To create this object, run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. | False | Named | False |
| FileRestore | Specifies a session of Microsoft Windows guest OS file restore. The cmdlet will mount disks of the VMs for which the restore sessions was launched to the Veeam Backup & Replication console.  Note: The restore session must be started within the current PowerShell session.  This parameter is required if the Session parameter is not specified. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Mounting Disks of the VMs

This example shows how to mount disks of the Hv\_DNS and Hv\_DC VMs for which restore is launched.

|  |
| --- |
| $restore = Get-VBRRestoreSession -Name "Hv\_DNS", "Hv\_DC"  Mount-VBRWindowsFileRestoreItems -Session $restore |

Perform the following steps:

1. Run the [Get-VBRRestoreSession](get-vbrrestoresession.md) cmdlet. Specify the Name parameter value. Save the result to the $restore variable.
2. Run the Mount-VBRWindowsFileRestoreItems cmdlet. Set the $restore variable as the Session parameter value.

Related Commands

* [Get-VBRRestoreSession](get-vbrrestoresession.md)
* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
