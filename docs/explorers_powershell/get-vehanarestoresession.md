---
title: "Get-VEHANARestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanarestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VEHANARestoreSession


Short Description

Returns active restore sessions started to perform operations with backed-up SAP HANA databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANARestoreSession [[-SessionId] <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up SAP HANA databases. Once you select the restore session you need, you can get the backed-up SAP HANA system using the [Get-VEHANASystem](get-vehanasystem.md) cmdlet, and then you can get any database on the system with the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for SAP HANA has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target SAP HANA system.

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

The cmdlet returns the [VEHANARestoreSession](vehanarestoresession.md)[] array that contains settings of restore sessions started to explore backed-up SAP HANA databases and to perform restore operations with these databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Restore Sessions

|  |  |
| --- | --- |
| This command returns all active restore sessions. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEHANARestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Session by Session ID

|  |  |
| --- | --- |
| This command returns an SAP HANA restore session with a specific session ID. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEHANARestoreSession -SessionId "518c5a82-e6bc-4ff9-b436-fd96cc875575" | |

Related Commands

* [Start-VEHANARestoreSession](start-vehanarestoresession.md)
* [Stop-VEHANARestoreSession](stop-vehanarestoresession.md)


