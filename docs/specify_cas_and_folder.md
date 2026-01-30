---
title: "Step 4. Specify CAS Server and Target Folder"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/specify_cas_and_folder.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify CAS Server and Target Folder


At this step of the wizard, specify a CAS server and provide a folder to which you want to restore data. You can restore your data to the original folder or specify a custom folder.

To provide a CAS server and target folder, do the following:

1. Specify a CAS server DNS name or IP address.

This field is populated automatically with the CAS server address from your domain. You can also enter a CAS server manually.

1. Select a folder to which you want to restore data. You can restore your data to the original folder or specify a custom folder.

When you select to restore to a custom folder, Veeam Explorer for Microsoft Exchange checks if the specified folder exists, if not, it creates a folder automatically. For example, if you specify a path like Folder1/Folder2/Folder3, Veeam Explorer for Microsoft Exchange will restore your data to the Folder3. You can use both the slash ("/") and the backslash ("\") characters when specifying a path.

[![Specify CAS Server and Target Folder](images/vee_restore_to_mailbox_2.webp)](images/vee_restore_to_mailbox_2.webp "Specify CAS Server and Target Folder")


