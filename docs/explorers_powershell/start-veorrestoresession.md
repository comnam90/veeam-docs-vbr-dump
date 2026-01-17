---
title: "Start-VEORRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-veorrestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Start-VEORRestoreSession


Short Description

Starts a restore session to explore backed-up Oracle databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEORRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves backed-up Oracle databases. Within the restore session, you can get backed-up databases using the following cmdlets:

* [Get-VEORDatabase](get-veordatabase.md)
* [Get-VEORDatabaseFile](get-veordatabasefile.md)

After you get backed-up Oracle databases, you can restore, publish, export or perform instant recovery with these databases.

* Run the [Restore-VEORDatabase](restore-veordatabase.md) cmdlet to restore Oracle databases.
* Run the [Publish-VEORDatabase](publish-veordatabase.md) cmdlet to publish Oracle databases.
* Run the [Export-VEORDatabase](export-veordatabase.md) cmdlet to export Oracle databases.
* Run the [Restore-VEORIRDatabase](restore-veorirdatabase.md) cmdlet to perform instant recovery of Oracle databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with Oracle databases that this restore point contains. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRestoreSession](veorrestoresession.md) object that contains settings of the restore session started to explore backed-up Oracle databases and to perform operations with these databases.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with Oracle databases.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -Oracle  Start-VEORRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the Oracle parameter. Save the result to the $restorepoint variable.

The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.

1. Run the Start-VEORRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)


