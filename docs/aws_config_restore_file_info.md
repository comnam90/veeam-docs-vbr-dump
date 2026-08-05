---
title: "Step 3. Review Backup File Info"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_config_restore_file_info.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Review Backup File Info


The backup appliance will analyze the content of the selected backup file and display the following information:

* File information — the date and time when the backup file was created.
* Product information — the version of the backup appliance that was installed on the initial backup appliance and the version of the File-Level Recovery service that was running on the appliance.

|  |
| --- |
| Note |
| Consider that if the current version of the backup appliance is later than the version saved in the configuration backup file, the configuration restore operation will not downgrade the backup appliance version. |

* Product configuration — configuration data saved in the file (such as number of existing backup policies, added IAM roles and repositories, logged session records and so on).

At the File Content step of the wizard, review the provided information and click Next to confirm that you want to use the selected file to restore the configuration data.

[![Restoring Configuration Data](images/aws_config_restore_file.webp)](images/aws_config_restore_file.webp "Restoring Configuration Data")

Page updated 2026-05-20

