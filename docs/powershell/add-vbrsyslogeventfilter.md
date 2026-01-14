---
title: "Add-VBRSyslogEventFilter"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrsyslogeventfilter.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRSyslogEventFilter

In this article

Short Description

Adds a syslog event filter for an event ID.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRSyslogEventFilter -EventId <Int64> [-FilterErrors <Boolean>] [-FilterInfos <Boolean>] [-FilterWarnings <Boolean>]  [<CommonParameters>] |

Detailed Description

The cmdlet determines which Veeam events are sent to the syslog server. Events have the following severity levels:

* Info
* Error
* Warning

By default, all events are sent to the syslog server. To exclude specific severity level events from being sent, you must set the necessary parameter to True.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EventId | Specifies an event ID. For a complete list of event IDs, see [Event IDs List](https://helpcenter.veeam.com/docs/backup/events/event_id_list.html?ver=13). | Int64 | True | Named | False |
| FilterErrors | Determines whether events with the Error severity level are excluded from being sent to the syslog server.  Default: True | Boolean | False | Named | False |
| FilterInfos | Determines whether events with the Info severity level are excluded from being sent to the syslog server.  Default: True | Boolean | False | Named | False |
| FilterWarnings | Determines whether events with the Warning severity level are excluded from being sent to the syslog server.  Default: True | Boolean | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Adding a Filter

This command adds a filter for the event ID 40700. Events with ID 40700 and the Info severity level will not be sent to the syslog server.

|  |
| --- |
| Add-VBRSyslogEventFilter -EventId 40700 -FilterErrors $false -FilterInfos $true -FilterWarnings $false |

Related Commands

* [Get-VBRSyslogEventFilters](get-vbrsyslogeventfilters.md)
* [Remove-VBRSyslogEventFilter](remove-vbrsyslogeventfilter.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
