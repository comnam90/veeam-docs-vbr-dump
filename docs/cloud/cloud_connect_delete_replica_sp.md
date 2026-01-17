---
title: "Deleting from Disk"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_delete_replica_sp.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Deleting from Disk


You can use the Delete from disk operation if you want to delete records about tenant VM replicas from the Veeam Backup & Replication console and database and, additionally, unregister the VM replica on the cloud host and delete actual replica files from the datastore or volume.

Do not delete tenant VM replicas from the cloud host manually. Use the Delete from disk option instead. If you delete VM replicas manually, subsequent replication job sessions will fail.

To remove VM replicas from the cloud host:

1. Open the Cloud Connect view.
2. In the inventory pane, click Replicas.
3. In the working area, right-click the necessary VM replica and select Delete from disk.

[![Delete Replica from Disk](images/cloud_delete_replica_from_disk_sp.webp)](images/cloud_delete_replica_from_disk_sp.webp "Delete Replica from Disk")


