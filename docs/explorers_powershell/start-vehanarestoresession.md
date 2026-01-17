---
title: "Start-VEHANARestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vehanarestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts a restore session to explore backed-up SAP HANA databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEHANARestoreSession [-Backup] <IVEHANABackup> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves backed-up SAP HANA databases. Within the restore session, you can get the backed-up SAP HANA system using the [Get-VEHANASystem](get-vehanasystem.md) cmdlet, and then you can get any database on the system with the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for SAP HANA has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target SAP HANA system.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a backup used to start a new restore session. You will be able to use the session to perform restore operations with the SAP HANA databases in the backup. | Accepts the [IVEHANABackup](vehanabackup.md) object. To get this object, run the [Get-VEHANABackup](get-vehanabackup.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANARestoreSession](vehanarestoresession.md) object that contains settings of the restore session started to explore backed-up SAP HANA databases and to perform restore operations with these databases.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with SAP HANA databases.

|  |
| --- |
| $backup = Get-VEHANABackup -Name "SAP HANA\*"  $session = Start-VEHANARestoreSession -Backup $backup |

Perform the following steps:

1. Run the [Get-VEHANABackup](get-vehanabackup.md) cmdlet and specify the Name parameter value. Use the wildcard \* character to get all backups whose names begin with "SAP HANA". Save the result to the $backup variable.
2. Run the Start-VEHANARestoreSession cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $session variable to be able to use it with other cmdlets.

Related Commands

* [Get-VEHANABackup](get-vehanabackup.md)
* [Get-VEHANARestoreSession](get-vehanarestoresession.md)
* [Stop-VEHANARestoreSession](stop-vehanarestoresession.md)

Page updated 3/17/2025

Page content applies to build 13.0.1.1071
