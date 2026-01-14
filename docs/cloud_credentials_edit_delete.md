---
title: "Editing and Deleting Credentials Records"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cloud_credentials_edit_delete.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Editing and Deleting Credentials Records

In this article

You can edit or delete existing cloud credentials records.

Editing Credentials

To edit a credentials record:

1. From the main menu, select Credentials and Passwords > Cloud Credentials.
2. Select the credentials record in the list and click Edit.
3. Edit settings of the credentials record as required.

|  |
| --- |
| Tip |
| You can use the Cloud Credentials Manager to change the password for a tenant account provided by the SP. For more information, see the [Changing Password for Tenant Account](https://helpcenter.veeam.com/docs/vbr/cloud/cc_change_password.html?ver=13) section in the Veeam Cloud Connect Guide. |

Creating New Google Service Account

If you created a Google Cloud service account using the [Create a new service account](cloud_credentials_gcp.md) option, you may need to create a new service account instead of the already created one. For example, the service account was deleted.

To cretae a new service account, do the following:

1. Edit the necessary credential as described in the Editing Credentials section.
2. At the Account step, click the Log In link.
3. In the opened window, log into your Google Cloud account.
4. Back to the Google Cloud Platform Service Account wizard, click Finish.

Veeam Backup & Replication will create a new service account and will use it to communicate with Google Cloud.

Deleting Credentials

To delete a credentials record:

1. From the main menu, select Credentials and Passwords > Cloud Credentials.
2. Select the credentials record in the list and click Remove. You cannot delete a record that is already used for any component in the backup infrastructure.

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
