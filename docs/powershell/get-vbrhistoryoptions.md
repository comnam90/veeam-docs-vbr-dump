---
title: "Get-VBRHistoryOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhistoryoptions.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHistoryOptions

In this article

Short Description

Returns job sessions history settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRHistoryOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns sessions history settings for jobs that are available on a backup server.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHistoryOptions object that contains job sessions history settings.

Examples

Getting Job Sessions History Settings

This command returns history settings for jobs that are available on a backup server. The cmdlet output will contain the following details on the sessions history settings: KeepAllSessions and RetentionLimitWeeks.

|  |
| --- |
| Get-VBRHistoryOptions  KeepAllSessions RetentionLimitWeeks  --------------- -------------------           False                  13 |

Page updated 1/29/2024

Page content applies to build 13.0.1.1071
