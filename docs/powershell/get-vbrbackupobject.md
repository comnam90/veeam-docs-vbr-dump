---
title: "Get-VBRBackupObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupobject.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackupObject

In this article

Short Description

Returns backups or replicas of machines.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRBackupObject -Backup <CBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups or replicas of machines. You can scan these backups with antivirus or YARA scan.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a backup or replica object with backed-up machines. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) or [Get-VBRReplica](get-vbrreplica.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupObject](vbrbackupobject.md)

Examples

Getting Backups of Machines

This example shows how to get backups of machines.

|  |
| --- |
| $backup = Get-VBRBackup  $vmbackup = Get-VBRBackupObject -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the Get-VBRBackupObject cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $vmbackup variable.

Related Commands

[Get-VBRBackup](get-vbrbackup.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
