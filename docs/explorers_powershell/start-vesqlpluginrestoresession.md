---
title: "Start-VESQLPluginRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlpluginrestoresession.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Start-VESQLPluginRestoreSession


Short Description

Starts a restore session to explore and restore databases backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VESQLPluginRestoreSession [-Backup] <IVESQLPluginBackup> [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session to explore and restore databases backed up with Veeam Plug-in for Microsoft SQL Server.

After you create the restore session, run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet to get databases backed up with Veeam Plug-in for Microsoft SQL Server.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a backup used to start a new restore session. You will be able to use the session to explore and restore Microsoft SQL Server databases that this backup contains. | Accepts the [IVESQLPluginBackup](vesqlpluginbackup.md) object. To get this object, run the [Get-VESQLPluginBackup](get-vesqlpluginbackup.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginRestoreSession](vesqlpluginrestoresession.md) object that contains settings of the restore session for databases backed up with Veeam Plug-in for Microsoft SQL Server.

Example

Starting Restore Session

This example shows how to start a restore session to explore and restore databases backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| $backup = Get-VESQLPluginBackup -Name "SQL Backup"  $session = Start-VESQLPluginRestoreSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VESQLPluginBackup](get-vesqlpluginbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Start-VESQLPluginRestoreSession cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $session variable to be able to use it with other cmdlets.

Related Commands

[Get-VESQLPluginBackup](get-vesqlpluginbackup.md)


