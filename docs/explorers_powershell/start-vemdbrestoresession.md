---
title: "Start-VEMDBRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vemdbrestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Start-VEMDBRestoreSession


Short Description

Starts a restore session to explore and perform restore operations with backed-up MongoDB data.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEMDBRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves a backed-up MongoDB replica set. Within the restore session, you can get MongoDB databases with the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet, and MongoDB collections with the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for MongoDB has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target MongoDB deployment.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point used to start a new restore session. You will be able to use the session to perform restore operations with MongoDB data in the restore point. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBRestoreSession](vemdbrestoresession.md) object that contains settings of the started restore session. You can use this object to explore backed-up MongoDB databases and collections and to perform restore operations with MongoDB data.

Example

Starting Restore Session

This example shows how to start a restore session to perform restore operations with MongoDB data.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -MongoDB  $session = Start-VEMDBRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet and provide the MongoDB parameter. Save the result to the $restorepoint variable.
2. Run the Start-VEMDBRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point. Save the result to the $session variable to be able to use it with other cmdlets.

Related Commands

* [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)
* [Get-VEMDBRestoreSession](get-vemdbrestoresession.md)
* [Stop-VEMDBRestoreSession](stop-vemdbrestoresession.md)


