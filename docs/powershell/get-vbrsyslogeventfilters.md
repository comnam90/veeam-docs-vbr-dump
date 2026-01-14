---
title: "Get-VBRSyslogEventFilters"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsyslogeventfilters.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSyslogEventFilters

In this article

Short Description

Returns the list of syslog event filters.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSyslogEventFilters  [<CommonParameters>] |

Detailed Description

This cmdlet returns all severity filters for event IDs.

Output Object

None.

Examples

Returning Active Filters

This command returns all severity filters for event IDs.

|  |
| --- |
| Get-VBRSyslogEventFilters |

Related Commands

* [Add-VBRSyslogEventFilter](add-vbrsyslogeventfilter.md)
* [Remove-VBRSyslogEventFilter](remove-vbrsyslogeventfilter.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
