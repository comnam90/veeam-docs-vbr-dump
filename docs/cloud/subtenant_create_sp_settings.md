---
title: "Step 2. Specify Subtenant Settings"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/subtenant_create_sp_settings.html"
last_updated: "4/15/2026"
product_version: "13.0.1.2067"
---

# Step 2. Specify Subtenant Settings


At the Account step of the wizard, specify settings for the created subtenant account:

1. In the Username field, specify a name for the created subtenant account. The user name must meet the following requirements:

* The maximum length of the user name is 128 characters. To avoid problems with long paths to backup files on the cloud repository, it is recommended to create user names not longer than 50 characters.
* The user name may contain space characters.
* The user name must not contain the following characters: ,\/:\*?\"<>|=;@ as well as Unicode characters.
* The user name must not end with the period character [.].

1. In the Password field, provide the password for the subtenant account. You can enter your own password or click the Generate new link at the bottom of the field. In the latter case, Veeam Backup & Replication will generate a safe password. To get a copy the generated password, click the Copy to clipboard link at the bottom of the window.
2. In the Description field, specify a description for the created subtenant account.
3. If you want the subtenant account to be created in the disabled state, select the Subtenant is disabled check box. In this case, Veeam Backup & Replication will create the subtenant account, but the subtenant will not be able to connect to the SP and create backups on the cloud repository.

![Step 2. Specify Subtenant Settings](images/add_subtenant_name.webp)


