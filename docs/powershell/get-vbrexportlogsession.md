---
title: "Get-VBRExportLogSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrexportlogsession.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRExportLogSession

In this article

Short Description

Returns details on sessions that were started to collect system logs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRExportLogSession [-Session <VBRExportLogSession>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns details on sessions that were started to collect system logs. Run the [Export-VBRLogs](export-vbrlogs.md) cmdlet to collect system logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a session that was started to collect system logs. The cmdlet will return details on this session. | Accepts the VBRExportLogSession object. To create this object, run the [Export-VBRLogs](export-vbrlogs.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRExportLogSession object that contains details on the sessions that were started to collect system logs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Details on all Sessions Started to Collect System Logs

|  |  |
| --- | --- |
| This command returns details on all sessions that were started to collect system logs. The cmdlet output will contain the following details on these sessions: Log, CreationTime, EndTime, JobId, Result, State and Id.  |  | | --- | | PS C:\Users\Administrator> Get-VBRExportLogSession  Log          : {1, 2, 3, 4...}  CreationTime : 1/10/2020 3:19:16 AM  EndTime      : 1/10/2020 3:20:27 AM  JobId        : cfe697c9-fd5f-4b19-a7b5-f7330a3d828b  Result       : Success  State        : Stopped  Id           : cfe697c9-fd5f-4b19-a7b5-f7330a3d828b    Log          : {1, 2, 3, 4...}  CreationTime : 1/10/2020 3:07:51 AM  EndTime      : 1/10/2020 3:09:08 AM  JobId        : 914d37df-febc-45cd-8eec-a294b30366d0  Result       : Success  State        : Stopped  Id           : 914d37df-febc-45cd-8eec-a294b30366d0 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Details on Specific Session Started to Collect System Logs

|  |  |
| --- | --- |
| This example shows how to get details on the session that was started to collect system logs for the R01 replica job.  |  | | --- | | $job = Get-VBRJob -Name R01  Export-VBRLogs -Job $job -FolderPath "C:\logs"  Log          : {1, 2, 3, 4...}  CreationTime : 1/10/2020 3:19:16 AM  EndTime      : 1/10/2020 3:20:27 AM  JobId        : cfe697c9-fd5f-4b19-a7b5-f7330a3d828b  Result       : Success  State        : Stopped  Id           : cfe697c9-fd5f-4b19-a7b5-f7330a3d828b |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job parameter value. 2. Run the Export-VBRLogs cmdlet. Set the $job variable as the Job parameter value. Specify the FolderPath parameter value.   The cmdlet output will contain the following details on these sessions: Log, CreationTime, EndTime, JobId, Result, State and Id. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 2/29/2024

Page content applies to build 13.0.1.1071
