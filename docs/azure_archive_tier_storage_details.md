---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_archive_tier_storage_details.html"
last_updated: "8/12/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Object Storage Settings


At the Container step of the wizard, specify the container and folder that will be used to store data:

1. From the Container drop-down list, select a container.

Make sure that the container where you want to store your backup data was created in advance.

1. To the right of the Folder field, click Browse and either select an existing folder or click New Folder.

1. Select the Make backups immutable for the entire duration of their retention policy check box to prohibit deletion of blocks of data from object storage. The immutability period will be equal to the retention period (if any) of the data blocks. All the types of files that are eligible for archive storage can be made immutable. For more information on the immutability feature and the retention policy for each file type, see [Immutability for Archive Tier](immutability_archive_tier.md).

![Step 4. Specify Object Storage Settings ](images/azure_archive_container.webp)

Specifying Azure Access Tier Settings

To specify the the access tier that you want assign to data blocks that you keep in Azure Blob object storage, click the Archive link to the right of the Access tier field. In the Access Tier Settings window, select one of the following:

* Select the Archive option to assign the archive access tier to data blocks. Use this option if you plan to access your data rarely and store it at least for 180 days.
* Select the Cold option to assign the cold access tier to data blocks. Use this option if you plan to access your data more frequently and store it at least for 90 days.

![Step 4. Specify Object Storage Settings ](images/azure_archive_acess_tier.webp)


