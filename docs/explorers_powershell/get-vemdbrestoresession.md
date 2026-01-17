---
title: "Get-VEMDBRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbrestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active restore sessions started to perform restore operations with backed-up MongoDB data.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEMDBRestoreSession [[-SessionId] <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up MongoDB data. Once you select the restore session you need, you can either get backed-up MongoDB databases using the [Get-VEMDBDatabase](get-vemdbdatabase.md) cmdlet, or backed-up MongoDB collections using the [Get-VEMDBCollection](get-vemdbcollection.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for MongoDB has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target MongoDB deployment.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SessionId | Specifies the session ID of the necessary restore session. | GUID | False | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBRestoreSession](vemdbrestoresession.md)[] array that contains settings of the started restore sessions. You can use this object to explore backed-up MongoDB databases and collections and to perform restore operations with MongoDB data.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Restore Sessions

|  |  |
| --- | --- |
| This command returns all active restore sessions. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEMDBRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Session by Session ID

|  |  |
| --- | --- |
| This command returns a MongoDB restore session with a specific session ID. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEMDBRestoreSession -SessionId "b7ced612-1259-4221-810b-f62c21b1c159" | |

Related Commands

* [Start-VEMDBRestoreSession](start-vemdbrestoresession.md)
* [Stop-VEMDBRestoreSession](stop-vemdbrestoresession.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
