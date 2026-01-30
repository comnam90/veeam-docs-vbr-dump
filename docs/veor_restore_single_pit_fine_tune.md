---
title: "Step 3. Fine-Tune Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_restore_single_pit_fine_tune.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 3. Fine-Tune Restore Point


At this step of the wizard, select an operation prior to which you want to restore your database and click Restore.

|  |
| --- |
| Note |
| This step is available only if you have selected the Perform restore to the specific transaction check box at the [Specify Restore Point](veor_restore_single_pit_specify_restore_point.md) step of the wizard. |

Before the restore process begins, you will be prompted to enter the source machine credentials.

[![Specifying Restore Point](images/veo_rest_wiz_finetuning_pit.webp)](images/veo_rest_wiz_finetuning_pit.webp "Specifying Restore Point")

[For Windows-based Oracle servers] If the user specified in the job is not the Oracle home user, you must provide a password to access the target Oracle home. Applicable to Oracle 12c and later versions.

You can enter the Oracle home user password when you configure the staging server. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md#staging_windows).

[![Specifying Oracle Home User Password](images/veor_restore_oracle_home_password.webp)](images/veor_restore_oracle_home_password.webp "Specifying Oracle Home User Password")


