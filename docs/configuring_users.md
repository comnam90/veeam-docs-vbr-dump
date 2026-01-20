---
title: "Configuring Users"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuring_users.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Configuring Users


To perform Veeam Backup & Replication operations, you can add users and assign to them different roles, both predefined and custom ones. For the list of predefined roles, see [Configuring Roles](configure_roles.md).

You can assign several roles to the same user. For example, if you want a user to start jobs and perform restore operations, you can assign both the Veeam Backup Operator and Veeam Restore Operator roles to this user.

You can configure users and groups in one of the following ways:

* [Configuring users using the Veeam Backup & Replication console](configuring_users_console.md)
* [Configuring users using the Veeam Backup & Replication web UI](configuring_users_web.md)

Requirements and Limitations

When you configure users for Veeam Backup & Replication on Linux, consider the following requirements and limitations:

* During the installation, the veeamadmin account is automatically added to the Veeam Backup & Replication console with the Veeam Backup Administrator role.

* If multi-factor authentication (MFA) is enabled, all users including Host Administrator accounts must pass the additional verification. Also, if you do not add a local user with Host Administrator permissions or a domain member of the Administrators group in the users and roles settings, this user will not have access to the Veeam Backup & Replication console.

When you configure users for Veeam Backup & Replication on Windows, consider the following requirements and limitations:

* For security reasons, the account used to run Veeam services should be a LocalSystem account. If a Veeam service runs under a user account other than LocalSystem, this user will have full access to the Veeam Backup & Replication console even if they are not specified in the users and roles settings.
* The user account under which the Veeam Backup Service runs must have the Veeam Backup Administrator role. If you change the default settings, make sure that you assign this role to the necessary user account. It is recommended to assign the role to the user account explicitly rather than the group to which the user belongs.
* The Veeam Backup Administrator role is assigned to all members of the Administrators group on the machine where Veeam Backup & Replication is installed.
* If you need to change the password for the service account, do that by actually logging in as that user and changing the password through standard Windows user interfaces (such as pressing Ctrl+Alt+Del and selecting "Change a password" while logged in as that user), rather than resetting it through administrative tools, scripts, or the Active Directory Users and Computers (ADUC) console.

* If multi-factor authentication (MFA) is disabled, consider the following:

+ Built-in administrator accounts (Domain\Administrator and Machine\Administrator) will have full access to the Veeam Backup & Replication console.
+ Local and domain members of the Administrators group will still have full access to Veeam Backup & Replication even if you delete this group in the users and roles settings.

To protect administrator accounts from being compromised, it is strongly recommended to enable multi-factor authentication. In that case, even users with administrator privileges must pass the additional verification. For more information, see [Multi-Factor Authentication](mfa.md).

* If multi-factor authentication (MFA) is enabled, consider the following:

+ All users including built-in administrator accounts (Domain\Administrator and Machine\Administrator) must pass the additional verification.
+ If you do not add a local or domain member of the Administrators group in the users and roles settings, this user will not have access to the Veeam Backup & Replication console.
+ If you add a local or domain member of the Administrators group in the users and roles settings, this user will have full access to the Veeam Backup & Replication console regardless of the assigned role.


