---
title: "Step 2. Specify Account Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_s3_aws_account_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Specify Account Settings


At the Account step of the wizard, specify a friendly name and connection settings of your object storage:

1. In the Friendly name field, specify a name you want to assign to your object storage. This name will be displayed in the list of your object storage repositories in the inventory of the virtual infrastructure.
2. From the Credentials drop-down list, select user credentials to access your Amazon S3 object storage.

If you already have a credentials record that was configured in advance, select such a record from the drop-down list. Otherwise, click Add and provide your access and secret keys, as described in the [Cloud Credentials Manager](https://helpcenter.veeam.com/docs/vbr/userguide/cloud_credentials.html?ver=13) section. You can also click the Manage credentials link to add, edit or remove a credentials record.

1. From the AWS region drop-down list, select the AWS region where the Amazon S3 bucket is located.
2. From the Data center drop-down list, select a region.

[![Step 2. Specify Account Settings](images/os_s3_aws_account_web.webp)](images/os_s3_aws_account_web.webp)

Page updated 2026-07-27

