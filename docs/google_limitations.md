---
title: "Google Cloud Object Storage Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/google_limitations.html"
last_updated: "8/8/2025"
product_version: "13.0.1.1071"
---

# Google Cloud Object Storage Considerations and Limitations

In this article

Consider the following limitations:

* Backups stored in Google Cloud object storage must be modified neither manually nor by third-party tools, including native Google Cloud capabilities (for example, the [Autoclass feature](https://cloud.google.com/storage/docs/autoclass)). Otherwise, Veeam Backup & Replication may fail to restore the backed-up data.
* If you enable the soft delete feature for Google Cloud buckets and the objects in these buckets are deleted, do not restore the objects with the Google console or any third-party capabilities. For more information on the soft delete feature, see the [Google Cloud documentation](https://cloud.google.com/resources/storage/soft-delete-announce?hl=en).

Page updated 8/8/2025

Page content applies to build 13.0.1.1071
