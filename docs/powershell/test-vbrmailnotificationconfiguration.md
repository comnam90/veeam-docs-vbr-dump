---
title: "Test-VBRMailNotificationConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/test-vbrmailnotificationconfiguration.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Test-VBRMailNotificationConfiguration


Short Description

Tests global email notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Test-VBRMailNotificationConfiguration  [<CommonParameters>] |

Detailed Description

This cmdlet tests global email notification settings. After you run the cmdlet, it sends a test email to check if global email notification settings have been configured correctly.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Testing Global Email Notification Settings

This command sends a test email to check if global email notification settings have been configured correctly.

|  |
| --- |
| Test-VBRMailNotificationConfiguration |


