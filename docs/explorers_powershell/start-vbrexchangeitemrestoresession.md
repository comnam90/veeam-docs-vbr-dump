---
title: "Start-VBRExchangeItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-vbrexchangeitemrestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Start-VBRExchangeItemRestoreSession


Short Description

Starts restore sessions to explore backed-up Exchange databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRExchangeItemRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet establishes a connection to the Veeam Backup & Replication and retrieves Exchange databases backed up on this server. Within the restore session, you can get backed-up Exchange objects within these databases using the following cmdlets:

* [Get-VEXDatabase](get-vexdatabase.md)
* [Get-VEXMailbox](get-vexmailbox.md)
* [Get-VEXFolder](get-vexfolder.md)
* [Get-VEXItem](get-vexitem.md)

After you get backed-up Exchange objects, you can perform the following operations with these objects:

* [Export-VEXItem](export-vexitem.md)
* [Restore-VEXItem](restore-vexitem.md)
* [Send-VEXItem](send-vexitem.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use the session to perform operations with Microsoft Exchange databases that this restore point contains. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBRExchangeRestoreSession](vbrexchangerestoresession.md) object that contains settings of the restore session started to explore backed-up Exchange databases and to perform operations with these databases.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with Microsoft Exchange databases.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -Exchange  Start-VBRExchangeItemRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. Provide the Exchange parameter. Save the result to the $restorepoint variable.

The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.

1. Run the Start-VBRExchangeItemRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)


