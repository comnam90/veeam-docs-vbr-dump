---
title: "Step 8. Specify User Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_deploying_guest_os_credentials.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Specify User Credentials


At the Guest OS step of the wizard, do the following:

1. From the Create the following administrator credentials drop-down list, select a user whose credentials will be used by Veeam Backup & Replication to create the Default Admin account on the backup appliance.

For a user to be displayed in the Create the following administrator credentials drop-down list, it must be added to the Credentials Manager as described in [Standard Accounts](credentials_manager_windows.md). If you have not added the necessary user to the Credentials Manager beforehand, you can do it without closing the New Veeam Backup for Microsoft Azure Appliance wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

|  |
| --- |
| Note |
| When you specify user credentials, Veeam Backup & Replication automatically verifies the provided password. If the password does not meet the [Microsoft security requirements](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/faq#what-are-the-password-requirements-when-creating-a-vm-), or if the password is present in any of the [Ubuntu 22.04 LTS cracklib dictionaries](https://manpages.ubuntu.com/manpages/jammy/en/man8/cracklib-format.8.html), you will get an error message notifying you that the password cannot be verified. |

1. In the Use the following key pair field, select a key pair that will be used to authenticate against the backup appliance.

For a key pair to be displayed in the list of available key pairs, it must be created in Microsoft Azure as described in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/ssh-keys-portal). If you have not created the necessary key pair beforehand, you can do it without closing the New Veeam Backup for Microsoft Azure wizard. To do that, click Add and specify the key pair name and folder path to the pair in the New Key Pair window.

|  |
| --- |
| Note |
| Consider the following:   * If you choose to create a new key pair, the key pair will be stored in the resource group specified at [step 4](azure_deploying_appliance_subscription.md). However, if you have selected the (create new) option when specifying the resource group, Veeam Backup & Replication will store the created key pair in the VeeamSSHKeys resource group. * If you change the password of the Default Admin account on the backup appliance, you must also change this user password in the Veeam Backup & Replication console as described in [Editing and Deleting Credentials Records](credentials_edit_delete.md). Otherwise, the connection will not be established. |

![Step 8. Specify User Credentials](images/azure_add_new_azure_apl_credentials.webp)

Page updated 2026-06-26

