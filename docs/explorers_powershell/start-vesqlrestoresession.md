---
title: "Start-VESQLRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vesqlrestoresession.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Start-VESQLRestoreSession


Short Description

Starts a restore session to explore backed-up Microsoft SQL databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VESQLRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves backed-up Microsoft SQL Server databases. Within the restore session, you can get backed-up databases using the following cmdlets:

* [Get-VESQLDatabase](get-vesqldatabase.md)
* [Get-VESQLDatabaseFile](get-vesqldatabasefile.md)

After you get backed-up Microsoft SQL Server databases, you can perform the following operations with these databases:

* [Publish-VESQLDatabase](publish-vesqldatabase.md)
* [Export-VESQLDatabase](export-vesqldatabase.md)
* [Restore-VESQLIRDatabase](restore-vesqlirdatabase.md)
* [Restore-VESQLDatabase](restore-vesqldatabase.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point used to start a new restore session. You will be able to use the session to perform operations with Microsoft SQL Server databases that this restore point contains. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRestoreSession](vesqlrestoresession.md) object that contains settings of the restore session started to explore backed-up Microsoft SQL databases and to perform operations with these databases.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with a Microsoft SQL database.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -SQL  $session = Start-VESQLRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the SQL parameter. Save the result to the $restorepoint variable.

The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.

1. Run the Start-VESQLRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point. Save the result to the $session variable to be able to use it with other cmdlets.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)


