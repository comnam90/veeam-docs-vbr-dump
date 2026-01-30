---
title: "Step 4. Specify Oracle Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_restore_multiple_tas_specify_oracle_settings.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Oracle Settings


At this step of the wizard, select a location to which you want to restore the databases.

1. Choose a target location:

* Restore to the original location: Veeam Explorer for Oracle checks if the target server has any Oracle home directories. If these home directories exist, the databases are restored. If they do not exist, the databases are not restored and Veeam Explorer for Oracle issues an error that suitable home directories have not been found.
* Restore to a different location: Veeam Explorer for Oracle restores all databases to a custom location. To specify the Oracle home directory, click Browse and select a folder that you want to use. Alternatively, you can manually enter the target location.

1. Click Restore.

[![Specifying Oracle Settings](images/veor_multiple_oracle.webp)](images/veor_multiple_oracle.webp "Specifying Oracle Settings")

[For Windows-based Oracle servers] If the account specified in the previous step is not the Oracle home user, you must provide a password to access the target Oracle home. Applicable to Oracle 12c and later versions.

[![Specifying Oracle Home User Password](images/veor_restore_oracle_home_password.webp)](images/veor_restore_oracle_home_password.webp "Specifying Oracle Home User Password")


