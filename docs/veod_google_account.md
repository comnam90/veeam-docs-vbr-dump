---
title: "Google Account"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veod_google_account.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Google Account


You can authorize Veeam Explorer for Microsoft OneDrive for Business to send Microsoft OneDrive items as attachments on behalf of your Google account. To send email messages, Veeam Explorer for Microsoft OneDrive for Business communicates with the Gmail API. For authentication, Veeam Explorer for Microsoft OneDrive for Business uses an access token issued by Google Authorization Server. To acquire an access token, you can either use an application preinstalled by Veeam Backup & Replication or specify OAuth 2.0 client credentials of the custom application registered in the Google Cloud console. For more information on obtaining client credentials, see [Registering Application in Google Cloud Console](veod_register_app_google.md).

To configure sending email messages on behalf of your Google account, do the following:

1. In the main menu, click General Options.
2. Open the Mail Settings tab.
3. Select the Enable sending emails check box.
4. From the Mail server drop-down list, select Google Gmail (modern authentication).
5. Do one of the following:

* To use an application preinstalled by Veeam Backup & Replication, click Sign in with Google and enter credentials of your Google account to complete authentication.

* To use the custom application, click Advanced to specify [the advanced settings](#advanced), then click Sign in with Google and enter credentials of your Google account to complete authentication.

1. In the From field, review the email address to be shown as a sender.

|  |
| --- |
| Note |
| You can change the sender email address. To send email notifications on behalf of another Google account, click Sign in with Google and use another email address to sign in. |

1. In the Send a test email to field, specify the email address to which Veeam Explorer for Microsoft OneDrive for Business sends a test email message.
2. Click Send to send a test email message.
3. Click OK.

[![Configuring Mail Settings](images/veod_google_acc.webp)](images/veod_google_acc.webp "Configuring Mail Settings")

Configuring Advanced Settings

In the Google Gmail Application Settings window, select the Use custom application registration settings check box and specify the following:

1. In the Application client ID field, specify specify the obtained client ID.
2. In the Client secret field, specify the client secret.

[![Configuring Google Gmail Application Settings](images/google_gmail.png)](images/google_gmail.png "Configuring Google Gmail Application Settings")


