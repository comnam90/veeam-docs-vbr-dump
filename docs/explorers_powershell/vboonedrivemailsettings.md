---
title: "VBOOneDriveMailSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vboonedrivemailsettings.html"
last_updated: "7/15/2025"
product_version: "13.0.1.1071"
---

# VBOOneDriveMailSettings


Contains Veeam Explorer for Microsoft OneDrive for Business mail settings.

| Property | Type | Description |
| --- | --- | --- |
| IsSendingEmailsEnabled | Bool | If True, Veeam Explorer for Microsoft OneDrive for Business is configured to send email messages. |
| AuthenticationType | PSAuthenticationType | Type of mail server used for sending emails. Possible values:   * CustomSmtp * Microsoft365 * GoogleGmail |
| ClientId | String | Client ID obtained while registering an application in the Google Cloud console or Microsoft Identity platform. |
| TenantId | String | Tenant ID in Microsoft Entra ID. |
| UserId | String | User ID. |
| MailApiUrl | String | Microsoft Graph endpoint for sending mail. Default: https://graph.microsoft.com/v1.0 |
| IsAuthenticated | Bool | If True, the user is successfully authenticated. |
| ConfigureSmtpSettings | Bool | If True, Veeam Explorer for Microsoft OneDrive for Business uses a SMTP server for sending email messages. |
| Server | String | DNS name or IP address of the SMTP server used for sending email messages. |
| Port | Int32 | Used port number. |
| From | String | Email address of the email sender. |
| UseAuthentication | Bool | If True, the SMTP server requires authentication. Otherwise, the connection is established to a SMTP server which does not enforce authentication. |
| User | String | Account used to authenticate to the SMTP server. |
| UseSSL | Bool | If True, Veeam Explorer for Microsoft OneDrive for Business uses a secure connection for sending emails. |

Related Commands

* [Get-VEODMailSettings](get-veodmailsettings.md)
* [Set-VEODMailSettings](set-veodmailsettings.md)


