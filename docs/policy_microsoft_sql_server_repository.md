---
title: "Step 4. Specify Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_microsoft_sql_server_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Storage Settings


At the Storage step of the wizard, specify settings for the target backup repository:

1. From the Backup repository list, select a backup repository where you want to store backups. You can select from the Veeam backup repositories configured on the backup server that will manage the created backup policy.
2. In the Retention Policy field, specify the number of days for which you want to store backup files in the target location. By default, Veeam Backup & Replication keeps backup files for 7 days. After this period is over, Veeam Backup & Replication will remove the earliest restore points from the backup chain.
3. To use the GFS (Grandfather-Father-Son) retention scheme, select the Keep certain full backups longer for archival purposes check box and click Configure. In the Configure GFS window, specify how weekly, monthly and yearly full backups must be retained. To learn more, see [Configure Long-Term Retention](policy_microsoft_sql_server_gfs.md).
4. Click Advanced to specify advanced settings for the backup job. To learn more, see [Specify Advanced Backup Settings](policy_microsoft_sql_server_advanced.md).

![Step 4. Specify Storage Settings](images/plugins_policy_mssql_storage.webp)

Page updated 2026-06-30

