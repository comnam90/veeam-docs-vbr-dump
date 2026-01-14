---
title: "set-veodsmtpsettings"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-veodsmtpsettings.html"
last_updated: "3/19/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Modifies SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft 365 7a and Veeam Backup & Replication 12.1, this cmdlet became deprecated. Use the [Set-VEODMailSettings](set-veodmailsettings.md) cmdlet to define email settings. |

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Set-VEODSmtpSettings [-ConfigureSmtpSettings] [-Server <String>] [-Port <Int32>] [-From <String>] [-UseAuthentication] [-Credentials <PSCredential>] [-UseSSL] [<CommonParameters>] |

Detailed Description

This cmdlet modifies SMTP settings for Veeam Explorer for Microsoft OneDrive for Business. These settings are required if you want to send restored items as email attachments.

To modify settings, enter the necessary parameters with new values. The parameters that you omit will remain unchanged.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ConfigureSMTPSettings | Defines that Veeam Explorer for Microsoft OneDrive for Business will use the SMTP server settings for sending restored items.  Default: False | SwitchParameter | False | Named | False |
| Server | Specifies the full DNS name or an IP address of the SMTP server. The cmdlet will use this information to send restored items in email messages. | String | False | Named | False |
| Port | Specifies a port number. The cmdlet will use this port number to connect to an SMTP server. | Int32 | False | Named | False |
| From | Specifies an email address from which Veeam Explorer for Microsoft OneDrive for Business will send restored OneDrive data.  This email account must have the rights to connect to an SMTP server if the SMTP server requires authentication. | String | False | Named | False |
| UseAuthentication | Defines that the SMTP server requires SMTP authentication for outgoing mail.  Default: False | SwitchParameter | False | Named | False |
| Credentials | Specifies the credentials. The cmdlet will use these credentials for authenticating to an SMTP server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSSL | Defines that a secure connection is required for sending emails.  If you do not provide this parameter, email messages will be sent through the connection that does not require SSL authentication.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveSmtpSettings](vboonedrivesmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft OneDrive for Business.

Example

Modifying SMTP Settings

This example shows how to change credentials that Veeam Explorer for Microsoft OneDrive for Business uses for authenticating to an SMTP server.

|  |
| --- |
| $credentials = Get-Credential  Set-VEODSmtpSettings -ConfigureSmtpSettings -Server test.support.local -Port 25 -From administrator@test.local -UseAuthentication -Credentials $credentials -UseSSL |

Perform the following steps:

1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet to create a credential object. Type Windows credentials to connect to the Veeam Backup for Microsoft 365 server. Save the result to the $credentials variable.
2. Run the Set-VEODSmtpSettings cmdlet. Specify the following settings:

* Provide the ConfigureSmtpSettings parameter.
* Specify the Server parameter value.
* Specify the Port parameter value.
* Specify the From parameter value.
* Provide the UseAuthentication parameter.
* Set the $credentials variable as the Credentials parameter value.
* Provide the UseSSL parameter.

Related Commands

[Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5)

Page updated 3/19/2025

Page content applies to build 13.0.1.1071
