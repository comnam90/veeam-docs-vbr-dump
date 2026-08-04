---
title: "Configuring Users"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hmc_configure_users.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Users


Users with Host Administrator permissions can perform the following operations related to configuring local Veeam appliance users:

* Create, edit, and remove user accounts
* Assign roles
* Enable and disable multi-factor authentication

Users with Security Officer permissions cannot configure local users.

|  |
| --- |
| Note |
| When configuring users, consider the following:   * If you have multi-factor authentication enabled, you must enter a one-time password before you can perform the following operations on Host Administrator accounts: create, edit, or remove users, assign roles, or reset multi-factor authentication. Authentication remains valid for 15 minutes. * A Host Administrator can enable or disable multi-factor authentication for other users at any time. If multi-factor authentication was disabled during initial configuration, it can be re-enabled here. After you enable MFA, users are prompted to set it up at their next login. |

User Roles

The following table describes roles you can assign to the local users.

User Roles

| Role | Description |
| Host Administrator | Can perform all administrative activities in the Veeam Host Management web UI and TUI:   * Configure network settings * Configure server time settings * Configure remote access settings * Manage users and roles * Configure backup infrastructure integrations * Manage software updates * Perform maintenance tasks   The default Host Administrator account is veeamadmin. |
| Security Officer | Can perform the following operations in the Veeam Host Management web UI:   * Reset user passwords * Reset user multi-factor authentication * Manage authorization requests * Manage password recovery tokens  * Manage configuration backups * Export events   Security Officer does not have access to the Veeam Host Management TUI.  The default Security Officer account is veeamso. |
| User | Manages backup and restore operations in accordance with the assigned backup server role. Use this role to create backup console users when the Veeam Software Appliance is not joined to a domain.  User must reset their password at first sign-in.  Has limited permissions to the system and no access to the Veeam Host Management console. |
| Service Account | Provides credentials for standalone backup agents and plug-ins to authenticate with the backup server.  Service Account cannot be used for interactive logons to management consoles and does not require password rotation.  Has limited permissions to the system and no access to the Veeam Host Management console. |

|  |
| --- |
| Note |
| You can add local Veeam Software Appliance users to the Veeam Backup & Replication console and assign a Veeam Backup & Replication role to them. Multi-factor authentication for the Veeam Backup & Replication console is disabled by default and is enabled separately from the Veeam Host Management console. When you enable it, the same authenticator code used for the Veeam Host Management console also works for the Veeam Backup & Replication console.  Users with the Service Account role can be used in Veeam Backup & Replication by applications and backup infrastructure components for non-interactive connections. |

Creating Users

To create a new user, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Click Add.
4. At the User step of the wizard, specify the name of the user, a password, and a description.

|  |
| --- |
| Note |
| Consider the following:   * The password must meet the following requirements:  * 15 characters minimum. * 1 upper case character. * 1 lower case character. * 1 numeric character. * 1 special character. * No more than 4 characters of the same class in a row. For example, more than 4 lowercase or 4 numerical characters in sequence.  * By default, passwords stay valid for 60 days, after which a user must set a new one that meets these requirements. A Host Administrator can change this interval or disable password expiration. For more information, see [Managing User Authentication](hmc_manage_user_auth.md). * After you add the user, you cannot change its name. |

1. Click Next.
2. At the Role step of the wizard, select a role and click Next. You can assign only one role to the user.
3. At the MFA step of the wizard, enable or disable multi-factor authentication for the user and click Next.

|  |
| --- |
| Note |
| Consider the following:   * If you add a user with the Security Officer role, you cannot disable MFA on that account. * If you add a user with the User or Service Account role, this step will be skipped. |

1. At the VBR Role step of the wizard, select a role, and specify if the user will be a Veeam Backup & Replication service account. Then, click Next.

|  |
| --- |
| Note |
| When assigning a Veeam Backup & Replication role to a new user, consider the following:   * Accounts with the Host Admin role can only be assigned the Backup Administrator Veeam Backup & Replication role. * Accounts with the Service Account or Security Officer role cannot be assigned a Veeam Backup & Replication role. |

1. At the Summary step of the wizard, review the data and click Finish.

[![Configuring Users](images/hmc_web_add_user.webp)](images/hmc_web_add_user.webp)

Editing Users

To edit a user, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Click Edit.
4. Change the description and roles if necessary. For Host Administrator accounts, you can also enable or disable multi-factor authentication.
5. Review the data and click Finish.

[![Configuring Users](images/hmc_web_edit_user.webp)](images/hmc_web_edit_user.webp)

Removing Users

To remove a user, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user, click Remove and confirm the operation.

|  |
| --- |
| Note |
| You cannot remove the default veeamadmin and veeamso user accounts. |

[![Configuring Users](images/hmc_web_remove_user.webp)](images/hmc_web_remove_user.webp)

Enabling Multi-Factor Authentication

To enable multi-factor authentication for Host Administrator accounts, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Enable MFA.

For Security Officer accounts, multi-factor authentication is always enabled.

[![Configuring Users](images/hmc_web_enable_mfa.webp)](images/hmc_web_enable_mfa.webp)

Disabling Multi-Factor Authentication

To disable multi-factor authentication for Host Administrator accounts, perform the following steps:

1. Log in to the Veeam Host Management web UI as a Host Administrator.
2. In the management pane, click Users and Roles.
3. Select the user.
4. Click Settings > Disable MFA.

For Security Officer accounts, multi-factor authentication cannot be disabled.

[![Configuring Users](images/hmc_web_disable_mfa.webp)](images/hmc_web_disable_mfa.webp)

Page updated 2026-07-28

