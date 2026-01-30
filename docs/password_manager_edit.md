---
title: "Editing Passwords"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/password_manager_edit.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Editing Passwords


To edit a password in the Password Manager, perform the following steps:

1. From the main menu, select Credentials & Passwords > Encryption Passwords.
2. Select the password and click Edit.
3. Update the hint or the password.
4. Click OK.

After you edit the password, you do not need to perform any other actions. Veeam Backup & Replication will start using the changed password after a job runs for the next time. Before the job run, the old password is still used. For more information on which password to use when you restore data, see [Restoring Data from Encrypted Backups](restore_encrypted.md).

![Editing Passwords](images/password_manager_edit_pass.webp)


