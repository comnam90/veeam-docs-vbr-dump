---
title: "Step 2. Specify Account Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_add_azure_blob_account.html"
last_updated: "11/3/2023"
product_version: "13.0.1.1071"
---

# Step 2. Specify Account Settings

In this article

At the Account step of the wizard, specify a friendly name and connection settings of your object storage:

1. In the Friendly name field, specify a name you want to assign to your object storage. This name will display in the list of you object storage repositories in the inventory of the virtual infrastructure.
2. From the Credentials drop-down list, select user credentials to access your Microsoft Azure Blob storage.

If you already have a credentials record that was configured in advance, select such a record from the drop-down list. Otherwise, click Add and provide your access and secret keys, as described in section [Cloud Credentials Manager](https://helpcenter.veeam.com/docs/backup/vsphere/cloud_credentials.html?ver=120). You can also click the Manage cloud accounts link to add, edit or remove a credentials record.

1. From the Region drop-down list, select an Azure region.

![Step 2. Specify Account Settings](images/snippet_os_azure_account.webp)

Page updated 11/3/2023

Page content applies to build 13.0.1.1071
