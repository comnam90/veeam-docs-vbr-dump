---
title: "Step 3. Fine-Tune Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_finetune.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 3. Fine-Tune Restore Point


At this step of the wizard, select an operation prior to which you want to publish your database and click Publish.

|  |
| --- |
| Note |
| This step is available only if you have selected the Perform restore to the specific transaction check box at the [Specify Restore Point](veor_srp.md) step of the wizard. |

[![Fine-Tuning Restore Point](images/veor_fine_tune_pit.webp)](images/veor_fine_tune_pit.webp "Fine-Tuning Restore Point")

[For Windows-based Oracle servers] If the user specified in the job is not the Oracle home user, you must provide a password to access the target Oracle home. Applicable to Oracle 12c and later versions.

You can enter the Oracle home user password when you configure the staging server. For more information, see [Configuring Staging Oracle Server](veor_staging_server.md#staging_windows).

[![Specifying Oracle Home User Password](images/veor_publish_oracle_home_password.webp)](images/veor_publish_oracle_home_password.webp "Specifying Oracle Home User Password")


