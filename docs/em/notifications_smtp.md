---
title: "SMTP Server with Basic Authentication"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/notifications_smtp.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# SMTP Server with Basic Authentication


For sending email notifications, you can use a custom SMTP server with basic authentication.

|  |
| --- |
| Note |
| When you add an SMTP server, Veeam Backup Enterprise Manager saves its TLS certificate thumbprint. If the SMTP server certificate is changed and the certificate is not trusted, Enterprise Manager stops sending email notifications until you validate the new certificate. |

To specify SMTP server settings, do the following:

1. Log in to Enterprise Manager using an administrative account.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. Open the Notifications section on the left of the Configuration view.
4. On the Server Settings tab, select SMTP server from the Mail server list.
5. On the Server Settings tab, specify a full DNS name or IP address of the SMTP server. If necessary, change the port number that will be used to communicate with the mail server. The default port number is 25.
6. In the Timeout field, specify a timeout for email server — this should be a value from 1 to 3600 seconds. Default is 100 seconds.
7. If the SMTP server requires SSL connection, select the Use SSL check box.
8. If the SMTP server requires authentication, select the Requires authentication check box and specify authentication credentials.
9. Click Save.

[![Email Server Settings](images/em_notifications_email_server.webp)](images/em_notifications_email_server.webp "Email Server Settings")


