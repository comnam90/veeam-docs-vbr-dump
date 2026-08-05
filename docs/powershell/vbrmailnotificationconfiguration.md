---
title: "VBRMailNotificationConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmailnotificationconfiguration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRMailNotificationConfiguration


Contains global email notification settings.

VBRMailNotificationConfiguration

| Property | Type | Description |
| Enabled | Boolean | Defines whether email notifications are enabled. |
| SmtpServer | String | Specifies the IP address or DNS name of the SMTP server used to send email notifications. |
| Sender | String | Specifies the email address from which notifications are sent. |
| Recipient | String | Specifies the recipient email addresses. |
| Subject | String | Specifies the subject of email notifications. |
| DailyReportsTime | DateTime | Specifies the time when daily reports are sent. |
| Port | Int32 | Specifies the port number over which the SMTP server sends messages. |
| Timeout | Int32 | Specifies the connection timeout for the SMTP server. |
| SSLEnabled | Boolean | Defines whether SSL is enabled for the SMTP server connection. |
| Credentials | CCredentials | Specifies the user credentials used to authenticate with the SMTP server. |
| NotifyOnSuccess | Boolean | Defines whether email notifications are sent if a job completes successfully. |
| NotifyOnWarning | Boolean | Defines whether email notifications are sent if a job completes with a warning. |
| NotifyOnFailure | Boolean | Defines whether email notifications are sent if a job does not complete successfully. |
| NotifyOnLastRetryOnly | Boolean | Defines whether email notifications report only the final job status. |
| AIGenerated | Boolean | Defines whether AI-generated text is used in email notification messages. |

Related Commands

* [Get-VBRMailNotificationConfiguration](get-vbrmailnotificationconfiguration.md)
* [Set-VBRMailNotificationConfiguration](set-vbrmailnotificationconfiguration.md)

Page updated 2026-06-10

