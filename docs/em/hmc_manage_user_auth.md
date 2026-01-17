---
title: "Managing User Authentication"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/hmc_manage_user_auth.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---


In this article

Users with Host Administrator permissions can perform the following operations related to authentication of the tocal Veeam Software Appliance users:

* Change own password
* Unlock users
* Reset multi-factor authentication
* Reset user passwords

Users with Security Officer permissions can only approve authorization requests to reset user passwords. For more information, see [Performing Security Officer Tasks](hmc_perform_so_tasks.md).

Changing Own Password

A Host Administrator can change a password in the Veeam Host Management web UI or TUI:

* In the Veeam Host Management web UI, do the following:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Change password.
5. Specify the current password and a new password and click Apply.

[![Managing User Authentication](images/hmc_web_reset_host_admin_pass.webp)](images/hmc_web_reset_host_admin_pass.webp)

* In the Veeam Host Management TUI, do the following:

1. Log in to the Veeam Host Management TUI as a Host Administrator.
2. In the main menu, select Change password.
3. Specify a new password and press [Enter].

[![Managing User Authentication](images/hmc_tui_reset_host_admin_pass.webp)](images/hmc_tui_reset_host_admin_pass.webp)

|  |
| --- |
| Note |
| If you are the only Host Administrator and have authentication issues, see [Resetting Passwords](#reset_pass). |

Unlocking Users

Users are locked after three failed login attempts. Consider the following:

* If you did not configure the Security Officer account during the Veeam Software Appliance installation, the user will be automatically unlocked in 15 minutes. Alternatively, you can unlock the user manually.
* If you configure the Security Officer account, the user will not be automatically unlocked. You can unlock the user only manually.

To unlock the user manually, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Unlock user.

[![Managing User Authentication](images/hmc_web_unlock_user.webp)](images/hmc_web_unlock_user.webp)

You can also unlock the user by resetting the password. For more information, see [Resetting Passwords](#reset_pass).

Resetting Multi-Factor Authentication

To reset multi-factor authentication for Host Administrator accounts, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Reset MFA.

[![Managing User Authentication](images/hmc_web_reset_mfa.webp)](images/hmc_web_reset_mfa.webp)

Alternatively, you can reset multi-factor authentication through the password reset operation. For more information, see [Resetting Passwords](#reset_pass).

|  |
| --- |
| Note |
| A Host Administrator cannot reset multi-factor authentication for Security Officers. To do this, a Security Officer must use a recovery token. For more information, see [Using Recovery Token](hmc_perform_so_tasks.md#use_recovery_token). |

Resetting Passwords

A Host Administrator can reset passwords for users including other Host Administrators to solve the following authentication issues:

* A user account is locked after three failed login attempts
* A user lost or forgot their password
* A user lost or change a mobile device with the mobile authentication application and does not have a code for multi-factor authentication

|  |
| --- |
| Note |
| A Host Administrator cannot reset passwords for Security Officers. To do this, a Security Officer must use a recovery token. For more information, see [Using Recovery Token](hmc_perform_so_tasks.md#use_recovery_token). |

To reset a user account password, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Change password.
5. Specify a new password and click Apply. After password reset, the user will also need to set up multi-factor authentication.

[![Managing User Authentication](images/hmc_web_reset_user_pass.webp)](images/hmc_web_reset_user_pass.webp)

If you are the only Host Administrator and you have authentication issues, you can reset your password in one of the following ways:

* If you did not configure the Security Officer account during the Veeam Software Appliance installation, you can only use Veeam LiveOS to restore access to the Veeam Host Management console. For more information, see [this KB article](https://www.veeam.com/kb4761).
* If you configured the Security Officer account, you can reset the Host Administrator password through the authorization request. To do this, perform one of the following operations:

* On the Veeam Host Management web UI sign-in page, click Forgot password?, specify your user name and click Submit.
* On the Veeam Host Management TUI logon screen, specify your user name and press [F2].

After the Security Officer approves the request, the next time you log in you will also need to set up multi-factor authentication.

[![Managing User Authentication](images/hmc_web_forgot_pass.webp)](images/hmc_web_forgot_pass.webp)

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
