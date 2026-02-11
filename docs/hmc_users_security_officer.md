---
title: "Performing Initial Security Officer Login"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hmc_users_security_officer.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Performing Initial Security Officer Login


When you first log in to the Veeam Host Management as a Security Officer, perform the following steps:

1. Log in to the Veeam Host Management web UI.
2. Specify a new password that meets the following requirements:

* 15 characters minimum.
* 1 upper case character.
* 1 lower case character.
* 1 numeric character.
* 1 special character.
* No more than 3 characters of the same class in a row. For example, more than 3 lowercase or 3 numerical characters in sequence.

[![Performing Initial Security Officer Login](images/hmc_so_intial_setup_new_pass.webp)](images/hmc_so_intial_setup_new_pass.webp)

1. Click Next.
2. Configure multi-factor authentication:

1. Open your authentication application. Enter the code or scan the QR code.
2. Specify the one-time code provided by the application.

[![Performing Initial Security Officer Login](images/hmc_so_intial_setup_mfa.webp)](images/hmc_so_intial_setup_mfa.webp)

1. Copy the recovery token and save it in a secure place.

[![Performing Initial Security Officer Login](images/hmc_so_intial_setup_recovery_token.webp)](images/hmc_so_intial_setup_recovery_token.webp)

1. Specify a passphrase and a hint to additionally protect sensitive data stored in encrypted configuration backups. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md) and [Restoring Configuration Database on Linux-Based Backup Server](vbr_config_restore_linux.md).

You can change the passphrase later if required. For more information, see [Managing Configuration Backup Passphrases](hmc_perform_so_tasks.md#manage_bco_passphrase).

[![Performing Initial Security Officer Login](images/hmc_so_intial_setup_config_backup_pass.webp)](images/hmc_so_intial_setup_config_backup_pass.webp)

1. Click Finish.


