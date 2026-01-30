---
title: "Registering Application in Google Cloud Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vet_register_app_google.html"
last_updated: "9/24/2024"
product_version: "13.0.1.1071"
---

# Registering Application in Google Cloud Console


To register an application in the Google Cloud console, do the following:

1. Sign in to the Google Cloud console under a Google account that you want to use for sending emails.
2. Create a new project and enable Gmail API for the project.

You can do this with [the Google setup tool](https://console.developers.google.com/start/api?id=gmail&credential=client_key).

1. Configure OAuth consent screen for your project.
2. Create the OAuth 2.0 client ID credentials — a client ID and client secret for the custom application.
3. Record the following data required for acquiring an access token:

* Client ID
* Client secret


