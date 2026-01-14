---
title: "Remove-VBRSyslogEventFilter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrsyslogeventfilter.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRSyslogEventFilter

In this article

Short Description

Removes syslog event filters for an event ID.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRSyslogEventFilter -EventId <Int64>  [<CommonParameters>] |

Detailed Description

This cmdlet removes all severity filters for an event ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EventID | Specifies an event ID. For a complete list of event IDs, see [Event IDs List](https://helpcenter.veeam.com/docs/backup/events/event_id_list.html?ver=120). | Int64 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing a Filter

This command removes all severity filters for event ID 40700.

|  |
| --- |
| Remove-VBRSyslogEventFilter -EventId 40700 |

Related Commands

* [Add-VBRSyslogEventFilter](add-vbrsyslogeventfilter.md)
* [Get-VBRSyslogEventFilters](get-vbrsyslogeventfilters.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
