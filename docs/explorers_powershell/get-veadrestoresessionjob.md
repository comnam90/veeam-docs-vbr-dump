---
title: "Get-VEADRestoreSessionJob"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veadrestoresessionjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VEADRestoreSessionJob


Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft Active Directory databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEADRestoreSessionJob [[-SessionId] <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Microsoft Active Directory databases.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| SessionId | Specifies the session ID of the necessary restore session. | Guid | False | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADRestoreSessionJob](veadrestoresessionjob.md)[] array that contains settings of restore sessions started to explore backed-up Microsoft Active Directory data and to perform operations with this data.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions started to perform operations with Microsoft Active Directory databases. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEADRestoreSessionJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to get a specific restore session started to perform operations with Microsoft Active Directory databases:  |  | | --- | | $session = Get-VEADRestoreSessionJob  $session[3] |  Perform the following steps:   1. Run the Get-VEADRestoreSessionJob cmdlet. Save the result to the $session variable.   The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session (in this example, it is the fourth restore session in the array).   1. Specify the necessary ordinal number of the restore session for the $session variable. In this example, it is the fourth restore session in the array. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Restore Session with Session Id

|  |  |
| --- | --- |
| This command returns a restore session with a specific session ID. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEADRestoreSessionJob -SessionId "132d5b9e-f309-4840-b58f-48cf13fc4c6e" | |

Page updated 2026-02-06

