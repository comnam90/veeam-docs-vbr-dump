---
title: "Step 2. Define Destination for Migration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/migrate_share_to_production_destination.html"
last_updated: "7/26/2024"
product_version: "13.0.1.1071"
---

# Step 2. Define Destination for Migration

In this article

At the Destination step of the wizard, specify the location where you want to migrate the selected file share to.

* Select Original location to migrate data to the location where it resided originally. This type of migration is only possible if the original device is connected to Veeam Backup & Replication and powered on.
* Select This server to migrate data to another location:

1. In the This server field, select a file share where files must be migrated to. You can select any file share added to the backup inventory. If the required file share is missing in the drop-down list, click Add and add a new file share to Veeam Backup & Replication. For more information on how to add a new file share, see [Adding Unstructured Data Source](adding_unstructured_data_source.md).
2. In the Path to folder field, specify a path to the folder on the selected file share where files must be migrated to.

To select a specific folder on the file share to migrate files to, click Browse. In the Select Folder window, select the target location for the file share.

If you want to restore the file share to a new folder, click New Folder at the bottom of the window, enter the folder name and click OK to confirm the new folder creation.

![Step 2. Define Destination for Migration](images/migrate_share_to_production_destination.webp)

Page updated 7/26/2024

Page content applies to build 13.0.1.1071
