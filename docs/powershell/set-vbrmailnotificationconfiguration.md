---
title: "Set-VBRMailNotificationConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmailnotificationconfiguration.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRMailNotificationConfiguration


Short Description

Modifies global email notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMailNotificationConfiguration [-SmtpServer <String>] [-Sender <String>] [-Recipient <String>] [-Subject <String>] [-DailyReportsTime <DateTime>] [-Port <Int32>] [-Timeout <Int32>] [-EnableSSL] [-EnableAuth] [-Credentials <CCredentials>] [-NotifyOnSuccess] [-NotifyOnWarning][-NotifyOnFailure] [-NotifyOnLastRetryOnly] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies global email notification settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SmtpServer | Specifies a full DNS name or an IP address of the SMTP server. The cmdlet will use this server to send email notifications. | String | False | Named | False |
| Sender | Specifies an email address. The cmdlet will send email notifications from this address. | String | True | Named | False |
| Recipient | Specifies the recipient addresses. | String | False | Named | False |
| Subject | Specifies the subject of the email notifications. | String | False | Named | False |
| DailyReportsTime | Specifies the time when Veeam Backup & Replication will send daily reports.  Default: 1/1/2019 10:00:00 PM | DateTime | False | Named | False |
| Port | Specifies the port number. The SMTP server will send messages over this port.  Default: 25 | Int | False | Named | False |
| Timeout | Specifies the connection timeout for the SMTP server.  Default: 100000 | Int | False | Named | False |
| EnableSSL | Enables SSL. If you provide this parameter, Veeam Backup & Replication will send email notifications over secure connection.  Default: Disabled | SwitchParameter | False | Named | False |
| EnableAuth | Defines that Veeam Backup & Replication will use user credentials to connect to the SMTP server.  Default: Disabled | SwitchParameter | False | Named | False |
| Credentials | Specifies the user credentials that Veeam Backup & Replication will use connect to the SMTP server. | CCredentials | False | Named | False |
| NotifyOnSuccess | Defines that Veeam Backup & Replication will send email notifications if a job runs successfully.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnWarning | Defines that Veeam Backup & Replication will send email notifications if a job completes with a warning.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnFailure | Defines that Veeam Backup & Replication will send email notifications if a job does not complete successfully.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnLastRetryOnly | Defines that Veeam Backup & Replication will send  email notifications about the final job status.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | Falseqnb |
| Force | Defines that the cmdlet will modify global email notification settings without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMailNotificationConfiguration object that contains global email notification settings.

Examples

Modifying Global Email Notification Settings

This command modifes the global notification settings. Veeam Backup & Replication will send notification settings with the following options:

* The IP address of the SMTP server that Veeam Backup & Replication will use to send messages is 172.17.53.12.
* The messages are sent from the backup@tech.com email address.
* The messages are sent to the administrator@tech.com email address.
* The subject of the messages is %BackupJobs%.
* Veeam Backup & Replication will send messages if the backup job fails.

|  |
| --- |
| Set-VBRMailNotificationConfiguration -SmtpServer 172.17.53.12 -Sender backup@tech.com -Recipient administrator@tech.com -Subject %BackupJobs% -NotifyOnFailure |

Related Commands

[Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


