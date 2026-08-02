---
title: "Adding SMTP Accounts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_accounts_smtp_create.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding SMTP Accounts


To add an account that will be used to connect to an SMTP server, do the following:

1. Switch to the Configuration page.
2. Navigate to Accounts > SMTP Accounts.
3. Click Add.

Complete the Add Account wizard.

1. At the Account Name step of the wizard, enter a name and provide a description for the SMTP account. The name must be unique in the backup appliance and the length of the name must not exceed 255 characters. The length must not exceed 255 characters.
2. At the Account step of the wizard, specify credentials of a user account that has permissions to access the SMTP server. The backup appliance will use the specified credentials to authenticate against the SMTP server.
3. At the Summary step of the wizard, review summary information and click Finish.

[![Adding SMTP Account](images/aws_accounts_smtp_finish.webp)](images/aws_accounts_smtp_finish.webp "Adding SMTP Account")

Page updated 2026-05-20

