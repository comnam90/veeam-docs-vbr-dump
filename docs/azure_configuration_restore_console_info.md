---
title: "Step 3. Review Backup File Info"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_restore_console_info.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 3. Review Backup File Info


At the Backup Contents step of the wizard, Veeam Backup & Replication will analyze the content of the selected backup and display the following information:

* Backup file — the data and time when the backup file was created, the size of the file, the file location and so on.
* [Applies if the configuration backup file selected at [step 2](azure_configuration_restore_console_file.md) is not stored on the backup server] Downloaded backup file — the temporary location of the configuration backup file on the backup server.
* Product — the name of the product and its version that was installed on the initial appliance.
* Catalogs — configuration data saved in the file (such as the number of configured backup policies, added user accounts, created repositories, logged session records an so on).

At the Backup Contents step of the wizard, review the provided information and click Next to confirm that you want to use the selected file to restore the configuration data.

![Step 3. Review Backup File Info](images/azure_restore_config_info.webp)

Page updated 2025-07-11

