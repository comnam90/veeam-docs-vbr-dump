---
title: "Start-VEADRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/start-veadrestoresession.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Start-VEADRestoreSession


Short Description

Starts a restore session to explore backed-up Microsoft Active Directory databases and to perform operations with these databases.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VEADRestoreSession [-RestorePoint] <IVBRApplicationRestorePoint> [<CommonParameters>] |

Detailed Description

This cmdlet starts a new restore session, establishes a connection to the backup server and retrieves backed-up Microsoft Active Directory databases. Within the restore session, you can get backed-up databases using the following cmdlets:

* [Get-VEADDomain](get-veaddomain.md)

* [Get-VEADContainer](get-veadcontainer.md)
* [Get-VEADItem](get-veaditem.md)

After you get backed-up Microsoft Active Directory databases, you can restore these databases.

Run the [Restore-VEADItem](restore-veaditem.md) cmdlet to restore Microsoft Active Directory databases.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to start a new restore session. You will be able to use this session to perform operations with Microsoft Active Directory databases that this restore point contains. | Accepts the [IVBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html?ver=13) object. To get this object, run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADRestoreSession](veadrestoresession.md) object that contains settings of the restore session started to explore backed-up Microsoft Active Directory data and to perform operations with this data.

Example

Starting Restore Session

This example shows how to start a restore session to perform operations with Microsoft Active Directory databases.

|  |
| --- |
| $restorepoint = Get-VBRApplicationRestorePoint -ActiveDirectory  Start-VEADRestoreSession -RestorePoint $restorepoint[0] |

Perform the following steps:

1. Run the [Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13) cmdlet with the ActiveDirectory parameter. Save the result to the $restorepoint variable.

The cmdlet will return an array of restore points. Note the ordinal number of the necessary restore point. In our example, it is the first restore point in the array.

1. Run the Start-VEADRestoreSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value and select the necessary restore point.

Related Commands

[Get-VBRApplicationRestorePoint](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationrestorepoint.html?ver=13)


