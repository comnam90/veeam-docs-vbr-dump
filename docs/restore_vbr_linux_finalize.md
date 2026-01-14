---
title: "Step 4. Finalize Restore Process"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_linux_finalize.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Step 4. Finalize Restore Process

In this article

After the restore process has finished, consider the following:

* If you have not enabled encryption for configuration backups, Veeam Backup & Replication will not restore passwords for credentials records. You need to re-enter passwords for all credentials records to make sure that backup infrastructure components and jobs work correctly after you complete configuration restore.

* If you have not enabled encryption for configuration backups, Veeam Backup & Replication will not restore passwords for cloud credentials records. You need to re-enter passwords for all cloud credentials records to make sure that cloud services and jobs work correctly after you complete configuration restore.
* You can edit credentials of Microsoft Azure Compute, Google Cloud service account and Microsoft Azure storage (Entra ID) accounts only in Cloud Credentials Manager. For details, see [Editing and Deleting Credentials Records](cloud_credentials_edit_delete.md).
* Veeam Backup & Replication does not restore credentials records of Google Cloud service accounts that were created automatically using the Cloud Credentials Manager. For details, see [Google Cloud Service Accounts](cloud_credentials_gcp.md).
* After the configuration restore, you may need to perform the components upgrade. For more information, see [Upgrading Infrastructure Components](components_update.md).

Page updated 11/26/2025

Page content applies to build 13.0.1.1071
