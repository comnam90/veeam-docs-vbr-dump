---
title: "Get-VESQLRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrestoresession.html"
last_updated: "3/26/2026"
product_version: "13.0.1.2067"
---

# Get-VESQLRestoreSession


Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions for Microsoft SQL Server databases.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRestoreSession](vesqlrestoresession.md)[] array that contains settings of restore sessions started to explore backed-up Microsoft SQL Server databases and to perform operations with these databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions started to perform operations with Microsoft SQL Server databases. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VESQLRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to get a specific restore session started to perform operations with Microsoft SQL Server databases.  |  | | --- | | $session = Get-VESQLRestoreSession  $session[3] |  Perform the following steps:   1. Run the Get-VESQLRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Specify the necessary ordinal number of the restore session for the $session variable. In this example, it is the fourth restore session in the array. |


