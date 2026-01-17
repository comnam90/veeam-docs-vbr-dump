---
title: "Registering Application in Google Cloud Console"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/registering_google_app.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---


In this article

Before the Veeam Backup Enterprise Manager web application can obtain an access token, you need to register the application in the Google Cloud console. Upon registration you will have a client ID and client secret required for acquiring an access token.

You can register Veeam Backup Enterprise Manager in the Google Cloud console.

1. Log in to the Google Cloud console under a Google account that you want to use for sending email notifications.
2. Create a new project and enable Gmail API for the project.

You can do this with [the Google setup tool](https://console.developers.google.com/start/api?id=gmail&credential=client_key).

1. Create the OAuth client ID credentials — a client ID and client secret for the Veeam Backup Enterprise Manager application.

As an authorized redirect URI, specify the following:

|  |
| --- |
| https://<EnterpriseManagerServer>/api/Notifications/GrantPermissions |

where <EnterpriseManagerServer> is a host name of the host where the Enterprise Manager server resides.

1. Record the following data required for acquiring an access token:

* Client ID
* Client secret

Page updated 8/28/2025

Page content applies to build 13.0.1.1071
