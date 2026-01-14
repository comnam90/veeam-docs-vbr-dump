---
title: "get-veorrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorrestoresession.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active restore sessions started to perform operations with backed-up Oracle databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Oracle databases.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRestoreSession](veorrestoresession.md)[] array that contains settings of restore sessions started to explore backed-up Oracle databases and to perform operations with these databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all restore sessions started to perform operations with Oracle databases. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEORRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to get a specific restore session started to perform operations with Oracle databases.  |  | | --- | | $session = Get-VEORRestoreSession  $session[0] |  Perform the following steps:   1. Run the Get-VEORRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions.   1. Specify the necessary ordinal number of the restore session for the $session variable. In our example, it is the first restore session in the array. |

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
