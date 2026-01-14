---
title: "set-vexsmtpsettings"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-vexsmtpsettings.html"
last_updated: "3/19/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Modifies SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft 365 7a and Veeam Backup & Replication 12.1, this cmdlet became deprecated. Use the [Set-VEXMailSettings](set-vexmailsettings.md) cmdlet to define email settings. |

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VEXSmtpSettings [-ConfigureSmtpSettings] [-Server <String>] [-Port <Int32>] [-From <String>] [-UseAuthentication] [-Credentials <PSCredential>] [-UseSSL] [<CommonParameters>] |

Detailed Description

This cmdlet modifies SMTP settings of Veeam Explorer for Microsoft Exchange. You may want to get information on these settings before you send restored mailbox items as email attachments.

To modify settings, enter the necessary parameters with new values. The parameters that you omit will remain unchanged.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ConfigureSMTPSettings | Defines that Veeam Explorer for Microsoft Exchange will use the SMTP server settings for sending restored mailbox items.  Default: False | SwitchParameter | False | Named | False |
| Server | Specifies the full DNS name or an IP address of the SMTP server for sending restored mailbox items as email attachments. | String | False | Named | False |
| Port | Specifies a port number. The cmdlet will use this port to connect to the SMTP server.  Default: 25 | Int32 | False | Named | False |
| From | Specifies the email address from which Veeam Explorer for Microsoft Exchange will send restored mailbox data.  This email account must have the rights to connect to an SMTP server if the SMTP server requires authentication. | String | False | Named | False |
| UseAuthentication | Defines that the SMTP server requires authentication. Otherwise, the connection will be established to the SMTP server which does not enforce authentication.  Default: False | SwitchParameter | False | Named | False |
| Credentials | Specifies the credentials. The cmdlet will use these credentials for authenticating to an SMTP server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| UseSSL | Defines that a secure connection is required for sending emails. If you do not provide this parameter, email messages will be sent through the connection that does not require SSL authentication.  Default: False | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXSmtpSettings](vexsmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft Exchange.

Example

Modifying SMTP Settings

This command modifies SMTP settings of Veeam Explorer for Microsoft Exchange for sending restored mailbox items as email attachments.

|  |
| --- |
| Set-VEXSmtpSettings -ConfigureSmtpSettings -Server smtp01.support.local -Port 25 -From j.smith@support.com |

Page updated 3/19/2025

Page content applies to build 13.0.1.1071
