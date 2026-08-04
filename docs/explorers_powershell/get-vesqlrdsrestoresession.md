---
title: "Get-VESQLRDSRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsrestoresession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSRestoreSession


Short Description

Returns active restore sessions started to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRDSRestoreSession [[-SessionId] <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS.

After you get the restore session, run the [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) cmdlet to get backed-up Microsoft SQL Server databases running on Amazon RDS.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| SessionId | Specifies a restore session initiated to explore backed-up Microsoft SQL Server databases running on Amazon RDS. The cmdlet will return this session. | Guid | False | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSRestoreSession](vesqlrdsrestoresession.md)[] object that contains settings of restore sessions for backed-up Microsoft SQL Server databases running on Amazon RDS.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions for backed-up Microsoft SQL Server databases running on Amazon RDS. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VESQLRDSRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session with Indexing

|  |  |
| --- | --- |
| This example shows how to use indexing to get a specific restore session for backed-up Microsoft SQL Server databases running on Amazon RDS.  |  | | --- | | $session = Get-VESQLRDSRestoreSession  $session[3] |  Perform the following steps:   1. Run the Get-VESQLRDSRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Specify the necessary ordinal number of the restore session for the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Restore Session with Session Id

|  |  |
| --- | --- |
| This command returns a restore session with a specific session ID. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VESQLRDSRestoreSession -SessionId "cc0ae8b4-dehd-439c-a168-a37a3cde6f3b" | |

Page updated 2026-04-10

