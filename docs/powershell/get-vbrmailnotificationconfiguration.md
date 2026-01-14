---
title: "Get-VBRMailNotificationConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrmailnotificationconfiguration.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRMailNotificationConfiguration

In this article

Short Description

Returns global email notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRMailNotificationConfiguration  [<CommonParameters>] |

Detailed Description

This cmdlet returns global email notification settings.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMailNotificationConfiguration object that contains global email notification settings.

Examples

Getting Global Email Notification Settings

This command returns global email notification settings. The cmdlet output will contain details on notification settings.

|  |
| --- |
| Get-VBRMailNotificationConfiguration  Enabled               : False  SmtpServer            :  Sender                :  Recipient             :  Subject               : [%JobResult%] %JobName% (%ObjectCount% objects) %Issues%  DailyReportsTime      : 3/8/2021 10:00:00 PM  Port                  : 25  Timeout               : 100000  SSLEnabled            : False  AuthEnabled           : False  Credentials           :  NotifyOnSuccess       : True  NotifyOnWarning       : True  NotifyOnFailure       : True  NotifyOnLastRetryOnly : True |

Page updated 1/29/2024

Page content applies to build 13.0.1.1071
