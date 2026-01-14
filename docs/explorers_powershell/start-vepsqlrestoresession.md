---
title: "start-vepsqlrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vepsqlrestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Starts a restore session to explore backed-up PostgreSQL instances and to perform operations with these instances.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEPSQLRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves backed-up PostgreSQL databases.

Within the restore session, you can get information about the backed-up PostgreSQL instances using the following cmdlets:

* [Get-VEPSQLInstance](get-vepsqlinstance.md)
* [Get-VEPSQLTablespace](get-vepsqltablespace.md)

After you get backed-up PostgreSQL instances, you can restore, publish, or perform instant recovery with these instances.

* Run the [Start-VEPSQLInstanceRestore](start-vepsqlinstancerestore.md) cmdlet to restore PostgreSQL instances.
* Run the [Start-VEPSQLInstancePublish](start-vepsqlinstancepublish.md) cmdlet to publish PostgreSQL instances.
* Run the [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md) cmdlet to perform instant recovery of PostgreSQL instances.

Within the restore session you can also get information about the backed-up PostgreSQL databases with the [Get-VEPSQLDatabase](get-vepsqldatabase.md) cmdlet. After you get the backed-up PostgreSQL databases, you can export these databases with the [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with PostgreSQL instances that this restore point contains. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLRestoreSession](vepsqlrestoresession.md) object that contains settings of the restore session started to explore and recover backed-up PostgreSQL data.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with PostgreSQL instances.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -PostgreSQL  Start-VEPSQLRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the PostgreSQL parameter. Save the result to the $restorepoint variable.

The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.

1. Run the Start-VEPSQLRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)

Page updated 3/17/2025

Page content applies to build 13.0.1.1071
