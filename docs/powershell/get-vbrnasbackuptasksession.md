---
title: "Get-VBRNASBackupTaskSession (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackuptasksession.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupTaskSession (obsolete)


Short Description

Returns tasks for file backup sessions.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupTaskSession](get-vbrunstructuredbackuptasksession.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get file share backup session tasks by the file share names.

|  |
| --- |
| Get-VBRNASBackupSession -Name <string[]>  [<CommonParameters>] |

* Get file share backup session tasks by their IDs.

|  |
| --- |
| Get-VBRNASBackupSession -Id <guid[]>  [<CommonParameters>] |

* Get file share backup session tasks for the backup session.

|  |
| --- |
| Get-VBRNASBackupTaskSession -Session <VBRNASBackupSession>  [<CommonParameters>] |

Detailed Description

This cmdlet returns tasks for file backup sessions. Veeam Backup & Replication creates a separate task for each file share within the session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of file share names. The cmdlet will return tasks that run for file shares with these names. | String[] | True | Named | False |
| Id | Specifies an array of IDs for file share backup session tasks. The cmdlet will return tasks with these IDs. | Guid[] | True | Named | False |
| Session | Specifies the file share backup session. The cmdlet will return tasks that run within the file share backup session with this ID. | Accepts the VBRNASBackupSession object. To get this object, run the [Get-VBRNASBackupSession](get-vbrnasbackupsession.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupTaskSession](vbrunstructuredbackuptasksession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backup Session Tasks for File Share by Its Name

|  |  |
| --- | --- |
| This command returns all tasks run for the \\fileserv05\Documents file share.  |  | | --- | | Get-VBRNASBackupSession -Name "\\fileserv05\Documents" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Session Tasks by Task IDs

|  |  |
| --- | --- |
| This command returns the 49664A5F-9C55-4A1F-8E6A-1CD5705A684B and 42696B53-6FEC-4148-9354-AA9E4B52DED9 backup session tasks.  |  | | --- | | Get-VBRNASBackupSession -Id ("49664A5F-9C55-4A1F-8E6A-1CD5705A684B", "42696B53-6FEC-4148-9354-AA9E4B52DED9") | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Backup Session Tasks for Backup Session

|  |  |
| --- | --- |
| This command returns tasks that run within the 42636B53-6FEC-4148-9354-BB9E4B52DED9 backup session.  |  | | --- | | $session = Get-VBRNASBackupSession -Id "42636B53-6FEC-4148-9354-BB9E4B52DED9" Get-VBRNASBackupTaskSession -Session $session |  Perform the following steps:   1. Run the [Get-VBRNASBackupSession](get-vbrnasbackupsession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable. 2. Run the Get-VBRNASBackupTaskSession cmdlet. Set the $session variable as the Session parameter value. |

Related Commands

[Get-VBRNASBackupSession](get-vbrnasbackupsession.md)


