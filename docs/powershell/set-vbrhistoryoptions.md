---
title: "Set-VBRHistoryOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhistoryoptions.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Set-VBRHistoryOptions


Short Description

Modifies job sessions history settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify session history settings to keep all sessions information in the database.

|  |
| --- |
| Set-VBRHistoryOptions [-KeepAllSessions]  [<CommonParameters>] |

* Modify session history settings to keep session information in the database for a specific period of time.

|  |
| --- |
| Set-VBRHistoryOptions [-RetentionLimitWeeks <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies job sessions history settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| KeepAllSessions | Defines that Veeam Backup & Replication will not delete the session information from the database.  Default: False. | SwitchParameter | False | Named | False |
| RetentionLimitWeeks | Specifies a period in weeks. Veeam Backup & Replication will keep the session information from the database for this period of time.  Default: 13. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHistoryOptions object that contains job sessions history settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Session History Settings to Keep all Sessions

|  |  |
| --- | --- |
| This command modifies history settings. According to these settings, Veeam Backup & Replication will keep all sessions information in the database.  |  | | --- | | Set-VBRHistoryOptions -KeepAllSessions  KeepAllSessions RetentionLimitWeeks  --------------- -------------------            True                  -1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Session History Settings to Keep Sessions for Several Weeks

|  |  |
| --- | --- |
| This command modifies history settings.  According to these settings, Veeam Backup & Replication will keep session information in the database for 7 weeks.  |  | | --- | | Set-VBRHistoryOptions -RetentionLimitWeeks 7  KeepAllSessions RetentionLimitWeeks  --------------  -------------------          False                    8 | |


