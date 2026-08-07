---
title: "Step 5. Finish Working with Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_data_cloud_archive_summary_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Finish Working with Wizard


At the Summary step of the wizard, review details of the newly created object storage repository and click Finish.

If the backup repository contains backups, select the Search the repository for existing backups and import them automatically check box. Veeam Backup & Replication will scan the backup repository to detect existing backup files and display them in the Veeam Backup & Replication console under the Backups > Object Storage (Imported) node.

If the backup repository contains guest file system index files, select the Import guest file system index data to the catalog check box. Veeam Backup & Replication will import index files together with backup files, and you will be able to search for guest OS files inside imported backups. For more information, see the [Guest OS File Restore](https://helpcenter.veeam.com/docs/vbr/em/searching_restoring_vm_guest_files.html?ver=13) section of the Veeam Backup Enterprise Manager Guide.

[![Step 5. Finish Working with Wizard](images/veeam_vault_finish_web.webp)](images/veeam_vault_finish_web.webp)

Page updated 2026-07-23

