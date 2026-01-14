---
title: "Step 8. Specify Guest Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vss_hv_web.html"
last_updated: "12/9/2025"
product_version: "13.0.1.1071"
---

# Step 8. Specify Guest Processing Settings

In this article

At the Guest Processing step of the wizard, you can configure the following settings:

* [Enable application-aware processing](backup_job_vss_application_hv_web.md) — to create a transactionally consistent backup of VMs running VSS-aware applications. The transactionally consistent backup guarantees the proper recovery of applications on VMs without data loss.
* [Enable guest file system indexing and malware detection](backup_job_vss_indexing_hv_web.md) — to create a catalog of files located on the guest OS.The catalog allows you to browse, search and perform 1-click restores of individual files. Guest indexing data in the catalog is scanned for suspicious file system activity and malware files. For more information, see the [Preparing for File Browsing and Searching](https://helpcenter.veeam.com/docs/vbr/em/preparing_for_file_browsing.html?ver=13) section in the Enterprise Manager User Guide. For details on guest OS file indexing settings, see [VM Guest OS File Indexing](backup_job_vss_indexing_hv_web.md). For details on malware detection, see [How Guest Indexing Data Scan Works](malware_detection_guest_index_hiw.md).
* [Guest interaction proxy](backup_job_vbr_vss_proxy_choose_hv_web.md) — to specify interaction proxy settings that Veeam Backup & Replication will use to install non-persistent runtime components or use (if necessary, install) persistent agent components in each VM.
* [Guest OS credentials](backup_job_vbr_credentials_manage_hv_web.md) — to specify credentials that allow Veeam Backup & Replication to connect to the VM guest OS.

[![Click to zoom in](images/hv_backup_job_vss_web.webp)](images/hv_backup_job_vss_web.webp "Click to zoom in")

Page updated 12/9/2025

Page content applies to build 13.0.1.1071
