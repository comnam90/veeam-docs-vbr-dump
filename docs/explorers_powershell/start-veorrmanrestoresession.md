---
title: "Start-VEORRMANRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-veorrmanrestoresession.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts a restore session to explore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEORRMANRestoreSession -Backup <IVEORRMANBackup> [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session for Oracle databases backed up with Veeam Plug-in for Oracle RMAN. Within the restore session, you can get backed-up databases and restore these databases.

Run the [Get-VEORRMANDatabase](get-veorrmandatabase.md) cmdlet to get Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Run the [Restore-VEORRMANDatabase](restore-veorrmandatabase.md) cmdlet to restore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an RMAN plug-in backup. The cmdlet will start a restore session from this backup. | Accepts the [IVEORRMANBackup](veorrmanbackup.md) object. To get this object, run the [Get-VEORRMANBackup](get-veorrmanbackup.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRMANRestoreSession](veorrmanrestoresession.md) object that contains settings of the restore session for Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Example

Starting Restore Session

This example shows how to start a restore session for an Oracle database backed up with Veeam Plug-in for Oracle RMAN.

|  |
| --- |
| $backup = Get-VEORRMANBackup -Name "Oracle RMAN\*"  Start-VEORRMANRestoreSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VEORRMANBackup](get-veorrmanbackup.md) cmdlet. Specify the Name parameter value. Use the wildcard \* character to get all backups whose names begin with "Oracle RMAN". Save the result to the $backup variable.
2. Run the Start-VEORRMANRestoreSession cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

[Get-VEORRMANBackup](get-veorrmanbackup.md)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
