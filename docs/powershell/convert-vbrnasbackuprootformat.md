---
title: "Convert-VBRNASBackupRootFormat"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackuprootformat.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Convert-VBRNASBackupRootFormat

In this article

Short Description

Converts backups created by one file backup job for separate non-root shared folders residing on the same server into the backup created for the server single root folder.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Convert-VBRNASBackupRootFormat -Backup <VBRNASBackup> -Server <VBRNASServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

The cmdlet converts backups created by one file backup job for separate non-root shared folders residing on the same server into the backup created for the server single root folder with all the non-root shared folders of the same type under it.

When converting the backups, you can specify a single root folder added to the inventory using one protocol (for example, SMB or NFS). If the initial backup protects shared folders accessed by different protocols (for example, the file backup job has both SMB and NFS shared folders residing on the same server as a source), you should run the Convert-VBRNASBackupRootFormat cmdlet for each of the protocols. Later on, you can add these separate root folders (for SMB and NFS shares) as sources to get the converted file backup job.

Note: Running the cmdlet is a single step in the procedure of converting backups from protecting multiple non-root shared folders to protecting single root folders. For more information, see [Converting Backups from Non-Root to Root Shared Folders](https://helpcenter.veeam.com/docs/vbr/userguide/convert_backups_nonroot_to_root.html?ver=13) in the Veeam Backup & Replication User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a file share backup. The cmdlet will convert this backup to replace the file share source: instead of separate non-root shared folders residing on the same server and protected by the same backup, the backup will protect the root folder in which these non-root shared folders are located. | Accepts the VBRNASBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True |
| Server | Specifies the file share server. The cmdlet will convert backups to have this server as the root shared folder protected by the backup. | Accepts the VBRNASServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackup object that defines results of converting the backups.

Examples

Converting Backup Source from Non-Root to Root Folder

The example shows how to convert a backup to replace the file share source: instead of separate non-root shared folders residing on the same server and protected by the same backup, the backup will protect the root folder in which these non-root shared folders are located.

|  |
| --- |
| $nasBackup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasServer = Get-VBRUnstructuredServer -Name "\\WinSRV2020"  Convert-VBRNASBackupRootFormat -Backup $nasBackup -Server $nasServer |

1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasBackup variable.
2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value.  Save the result to the $nasServer variable.
3. Run the Convert-VBRNASBackupRootFormat cmdlet. Set the $nasBackup variable as the Backup parameter value. Set the $nasServer variable as the Server parameter value.

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
