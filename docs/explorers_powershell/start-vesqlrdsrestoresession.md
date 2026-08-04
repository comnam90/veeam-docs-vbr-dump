---
title: "Start-VESQLRDSRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlrdsrestoresession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VESQLRDSRestoreSession


Short Description

Starts a restore session to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VESQLRDSRestoreSession [-Backup] <IVESQLRDSBackup> [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

After you create the restore session, run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet to get databases from the backed-up Amazon RDS instance for Microsoft SQL Server.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies a backup used to start a new restore session. You will be able to use the session to explore and restore Microsoft SQL Server databases that this backup contains. | Accepts the [VESQLRDSBackup](vesqlrdsbackup.md) object. To get this object, run the [Get-VESQLRDSBackup](get-vesqlrdsbackup.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSRestoreSession](vesqlrdsrestoresession.md) object that contains settings of the restore session for backed-up Microsoft SQL Server databases running on Amazon RDS.

Example

Starting Restore Session

This example shows how to start a restore session to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

|  |
| --- |
| $backup = Get-VESQLRDSBackup -Name "RDS SQL Backup"  $session = Start-VESQLRDSRestoreSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VESQLRDSBackup](get-vesqlrdsbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Start-VESQLRDSRestoreSession cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $session variable to be able to use it with other cmdlets.

Related Commands

[Get-VESQLRDSBackup](get-vesqlrdsbackup.md)

Page updated 2026-01-28

