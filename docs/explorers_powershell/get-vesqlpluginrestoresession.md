---
title: "Get-VESQLPluginRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlpluginrestoresession.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLPluginRestoreSession


Short Description

Returns active restore sessions started to explore and restore databases backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLPluginRestoreSession [[-SessionId] <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to explore and restore databases.

After you get the restore session, run the [Get-VESQLPluginDatabase](get-vesqlplugindatabase.md) cmdlet to get databases backed up with Veeam Plug-in for Microsoft SQL Server.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SessionId | Specifies a restore session initiated to explore databases backed up with Veeam Plug-in for Microsoft SQL Server. The cmdlet will return this session. | GUID | False | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLPluginRestoreSession](vesqlpluginrestoresession.md)[] object that contains settings of restore sessions for databases backed up with Veeam Plug-in for Microsoft SQL Server.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions for databases backed up with Veeam Plug-in for Microsoft SQL Server. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VESQLPluginRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session with Indexing

|  |  |
| --- | --- |
| This example shows how to use indexing to get a specific restore session for databases backed up with Veeam Plug-in for Microsoft SQL Server.  |  | | --- | | $session = Get-VESQLPluginRestoreSession  $session[3] |  Perform the following steps:   1. Run the Get-VESQLPluginRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in our example, it is the fourth restore session in the array).   1. Specify the necessary ordinal number of the restore session for the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Restore Session with Session Id

|  |  |
| --- | --- |
| This command returns a restore session with a specific session ID. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VESQLPluginRestoreSession -SessionId "cc0ab8b4-dd1d-439c-a168-a27a3cde6d3b" | |


