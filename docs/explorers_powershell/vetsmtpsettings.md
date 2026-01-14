---
title: "vetsmtpsettings"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vetsmtpsettings.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains Veeam Explorer for Microsoft Teams SMTP settings. Note that [Get-VETSmtpSettings](get-vetsmtpsettings.md), the cmdlet used to get this object, is deprecated.

| Property | Type | Description |
| --- | --- | --- |
| ConfigureSmtpSettings | Bool | If True, Veeam Explorer for Microsoft Teams uses the SMTP server settings for sending restored items. |
| Server | String | DNS name or IP address of the SMTP server used for sending restored data. |
| Port | Int32 | Port number. Default: 25 |
| From | String | Email address from which Veeam Explorer for Microsoft Teams sends restored data. |
| UseAuthentication | Bool | If True, the SMTP server requires authentication. Otherwise, the connection is established to a SMTP server which does not enforce authentication. |
| User | String | User to connect to the SMTP server. |
| UseSSL | Bool | If True, a secure connection is required for sending emails. Otherwise, email messages are sent through a connection that does not require SSL authentication. |

Related Commands

* [Get-VETSmtpSettings](get-vetsmtpsettings.md)
* [Set-VETSmtpSettings](set-vetsmtpsettings.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
