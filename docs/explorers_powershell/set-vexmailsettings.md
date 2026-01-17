---
title: "Set-VEXMailSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-vexmailsettings.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Set-VEXMailSettings


Short Description

Modifies Veeam Explorer for Microsoft Exchange email settings. Veeam Explorer for Microsoft Exchange uses these settings to send Exchange items that are located in a backup by email and deliver export reports.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify email settings to use a custom SMTP server with basic authentication.

|  |
| --- |
| Set-VEXMailSettings [-EnableSendingEmails] [-Server <String>] [-Port <Int32>] [-UseAuthentication] [-UseSSL] [-Credentials <PSCredential>] -From <String> [<CommonParameters>] |

* Modify email settings to use a Google account for authentication.

|  |
| --- |
| Set-VEXMailSettings [-EnableSendingEmails] [-GoogleGmail] [-ClientId <String>] [-ClientSecret <SecureString>] [<CommonParameters>] |

* Modify email settings to use a Microsoft 365 account for authentication.

|  |
| --- |
| Set-VEXMailSettings [-EnableSendingEmails] [-ClientId <String>] [-Microsoft365] [-MailApiUrl <String>] [-TenantId <String>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies email settings for Veeam Explorer for Microsoft Exchange. To modify settings, you need to enter the necessary parameters with new values. The parameters that you omit will remain unchanged.

|  |
| --- |
| Note |
| Email settings are global, they will be applied to all operations configured in Veeam Explorer for Microsoft Exchange. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableSendingEmails | Defines that Veeam Explorer for Microsoft Exchange will send email messages.  Default: False | SwitchParameter | False | Named | False |
| Server | Specifies the full DNS name or IP address of the SMTP server for sending email messages. | String | False | Named | False |
| Port | Specifies a port number for connecting to SMTP server. | Int32 | False | Named | False |
| UseAuthentication | Defines that the SMTP server requires authentication. Otherwise, the connection will be established to the SMTP server which does not enforce authentication.  Default: False | SwitchParameter | False | Named | False |
| UseSSL | Defines that Veeam Explorer for Microsoft Exchange will enable a secure connection for sending emails. If you do not provide this parameter, email messages will be sent through the connection that does not require SSL authentication.  Default: False | SwitchParameter | False | Named | False |
| Credentials | Specifies credentials that you want to use for authentication to the SMTP server. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.5) cmdlet. | False | Named | False |
| From | Specifies email address of the email sender. | String | False | Named | False |
| GoogleGmail | Defines that Veeam Explorer for Microsoft Exchange will send email messages on behalf of a Google account.  Default: False | SwitchParameter | True | Named | False |
| ClientId | Specifies the client ID obtained while registering an application in the Google Cloud console or Microsoft Identity platform. | String | False | Named | False |
| ClientSecret | Specifies a password.  Note: This parameter is required only for authentication with a Google account using a custom application. | SecureString | False | Named | False |
| Microsoft365 | Defines that Veeam Explorer for Microsoft Exchange will send email messages on behalf of a Microsoft 365 account.  Default: False | SwitchParameter | True | Named | False |
| MailApiUrl | Specifies the Microsoft Graph endpoint for sending mail.  Default: https://graph.microsoft.com/v1.0 | String | False | Named | False |
| TenantId | Specifies a tenant ID in Microsoft Entra ID. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXMailSettings](vexmailsettings.md) object that contains mail settings configured for Veeam Explorer for Microsoft Exchange.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Email Settings for SMTP Server with Basic Authentication

|  |  |
| --- | --- |
| This command sends email messages through the default SMTP server with basic authentication.  |  | | --- | | Set-VEXMailSettings -EnableSendingEmails -Server smtp.office365.com -Port 25 -From vex@tech.com |  Run the Set-VEXMailSettings cmdlet and specify the following settings:   * Provide the EnableSendingEmails parameter. * Specify the Server parameter value. * Specify the Port parameter value. * Specify the From parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Email Settings for Authentication with Microsoft 365 Account Using Veeam Application

|  |  |
| --- | --- |
| This command configures email messages with the following settings:   * Email messages will be sent on behalf of the Microsoft 365 account. * Authentication will be performed using an application preinstalled by Veeam.   |  | | --- | | Set-VEXMailSettings -EnableSendingEmails -Microsoft365 |  Run the Set-VEXMailSettings cmdlet and specify the following settings:   * Provide the EnableSendingEmails parameter. * Provide the Microsoft365 parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Email Settings for Authentication with Google Account Using Veeam Application

|  |  |
| --- | --- |
| This command configures email messages with the following settings:   * Email messages will be sent on behalf of the Google account. * Authentication to Google will be performed using an application preinstalled by Veeam.   |  | | --- | | Set-VEXMailSettings -EnableSendingEmails -GoogleGmail |  Run the Set-VEXMailSettings cmdlet and specify the following settings:   * Provide the EnableSendingEmails parameter. * Provide the GoogleGmail parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Modifying Email Settings for Authentication with Microsoft 365 Account Using Custom Application

|  |  |
| --- | --- |
| This command configures email messages with the following settings:   * Email messages will be sent on behalf of the Microsoft 365 account. * Authentication will be performed using a custom application registered in Microsoft Identity platform.   |  | | --- | | Set-VEXMailSettings -EnableSendingEmails -Microsoft365 -ClientId bd0xxxxx-2d90-0000-86f5-5488df12xxxx -TenantId xxxxde96-x000-4a97-8ae0-ba91c4aaxxxx |  Run the Set-VEXMailSettings cmdlet and specify the following settings:   * Provide the EnableSendingEmails parameter. * Provide the Microsoft365 parameter. * Specify values for the ClientId and TenantId parameters. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Modifying Email Settings for Authentication with Google Account Using Custom Application

|  |  |
| --- | --- |
| This example shows how to configure email messages with the following settings:   * Email messages will be sent on behalf of the Google account. * Authentication to Google will be performed using a custom application registered in the Google Cloud console.   |  | | --- | | $securepassword = Read-Host -Prompt "Enter client secret" -AsSecureString  Set-VEXMailSettings -EnableSendingEmails -GoogleGmail -ClientId 012345678901-xxxxxxxxxxxxxxxxxxxxxxxxxxxxkdgp.apps.googleusercontent.com -ClientSecret $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the Set-VEXMailSettings cmdlet. Specify the following settings:  * Provide the EnableSendingEmails parameter. * Provide the GoogleGmail parameter. * Specify the ClientId parameter value. * Set the $securepassword variable as the ClientSecret parameter value. |

Related Commands

[Read-Host](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.5)


