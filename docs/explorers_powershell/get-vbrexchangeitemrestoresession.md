---
title: "Get-VBRExchangeItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vbrexchangeitemrestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRExchangeItemRestoreSession


Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft Exchange databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRExchangeItemRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Microsoft Exchange databases.

|  |
| --- |
| Note |
| The cmdlet returns restore sessions initiated in the PowerShell console only. The cmdlet does not return restore sessions running in the Veeam Backup & Replication console. |

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBRExchangeRestoreSession](vbrexchangerestoresession.md)[] array that contains settings of restore sessions started to explore backed-up Exchange databases and to perform operations with these databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions initiated to perform operations with Microsoft Exchange databases. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to get a specific restore session initiated to perform operations with Microsoft Exchange databases.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  $session[0] |  Perform the following steps:   1. Run the Get-VBRExchangeItemRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session.   1. Specify the necessary ordinal number of the restore session for the $session variable. In our example, it is the first restore session in the array. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Stopping Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to stop a specific restore session initiated to perform operations with Microsoft Exchange databases.  |  | | --- | | $session = Get-VBRExchangeItemRestoreSession  Stop-VBRExchangeItemRestoreSession -Session $session[0] |  Perform the following steps:   1. Run the Get-VBRExchangeItemRestoreSession cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.   1. Run the [Stop-VBRExchangeItemRestoreSession](stop-vbrexchangeitemrestoresession.md) cmdlet. Set the $session variable as the Session parameter value. |

Related Commands

[Stop-VBRExchangeItemRestoreSession](stop-vbrexchangeitemrestoresession.md)


