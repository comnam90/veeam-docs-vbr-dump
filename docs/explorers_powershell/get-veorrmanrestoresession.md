---
title: "get-veorrmanrestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorrmanrestoresession.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active restore sessions started to explore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORRMANRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to explore Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

|  |
| --- |
| Note |
| * You can only get an array of restore sessions that are started in PowerShell. The cmdlet does not return restore sessions started in the Veeam Backup & Replication console. * The cmdlet only returns an array of restore sessions started within the same PowerShell session. |

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORRMANRestoreSession](veorrmanrestoresession.md)[] array that contains settings of restore sessions for Oracle databases backed up with Veeam Plug-in for Oracle RMAN.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Running Restore Sessions

|  |  |
| --- | --- |
| This command gets all running restore sessions for Oracle databases backed up with Veeam Plug-in for Oracle RMAN. Save the result to the $session variable to be able to use it with other cmdlets.  |  | | --- | | $session = Get-VEORRMANRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Restore Session

|  |  |
| --- | --- |
| This example shows how to get a specific restore session for Oracle databases backed up with Veeam Plug-in for Oracle RMAN.  |  | | --- | | $session = Get-VEORRMANRestoreSession  $session[0] |  Perform the following steps:   1. Run the Get-VEORRMANRestoreSession cmdlet. Save the result to the $session variable. 2. Specify the necessary ordinal number of the restore session for the $session variable. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array. |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
