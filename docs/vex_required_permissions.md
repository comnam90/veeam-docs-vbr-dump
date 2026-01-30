---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_required_permissions.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Permissions


The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft Exchange and restore Microsoft Exchange data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Microsoft Exchange launch | The account used to run Veeam Explorer for Microsoft Exchange must meet the following requirements:   * The account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft Exchange is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft Exchange restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore to Microsoft 365 and on-premises Microsoft Exchange | To restore data to Microsoft 365 and on-premises Microsoft Exchange organizations, you must grant the following roles and permissions to user accounts:  Restore to Public Folder Using Basic Authentication Method   * The account must own a mailbox on a target Microsoft Exchange server. * The account must be a member of the Organization Management role group on a target Microsoft Exchange server. See [Adding User Account to Organization Management Role Group](#aomr). * [For restore of In-Place Hold Items to the original location] If the In-Place Hold Items folder already exists, make sure the account being used can create, modify and delete items. If the In-Place Hold Items folder does not exist, the account being used must be able to create folders under the All Public Folders root node.   Restore to Mailbox Using Basic Authentication Method   * If the account owns a mailbox, make sure it has Full Access. * If the account does not own a mailbox, then access must be granted through impersonation. See [Granting Full Access](#gfa).   Restore Using Modern Authentication Method  Microsoft Entra application uses a user account to log in to Microsoft 365. This user account must be assigned the following roles:   * The ApplicationImpersonation role for Exchange Online. * The Global Administrator or Exchange Administrator role in Microsoft Identity platform.   Also make sure that the required settings are specified for the Microsoft Entra application used for restore. For more information, see the [Configuring Microsoft Entra Application Settings](https://helpcenter.veeam.com/docs/vbo365/guide/ad_application_settings_configuring.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. |
| Compare Data with Production Environment | The Veeam Backup account must have a valid Exchange Online license and an active mailbox within the Microsoft 365 organization. |

Examples

Adding User Account to Organization Management Role Group

To add user account to the Organization Management role group, use the following cmdlet:

|  |
| --- |
| Add-RoleGroupMember "Organization Management" –Member "<user\_account>" |

For more information about the Add-RoleGroupMember cmdlet, see [this Microsoft article](https://learn.microsoft.com/en-us/powershell/module/exchange/add-rolegroupmember?view=exchange-ps).

Granting Full Access

To grant Full Access to the account that owns a mailbox, use the following cmdlet:

|  |
| --- |
| Add-MailboxPermission –Identity "<target\_mailbox>" -User "<user\_account>" -AccessRights FullAccess –InheritanceType All |

For more information about the Add-MailboxPermission cmdlet, see [this Microsoft article](https://learn.microsoft.com/en-us/powershell/module/exchange/add-mailboxpermission?view=exchange-ps).

To grant Full Access to the account that does not own a mailbox (in particular, through impersonation), use the following cmdlet:

|  |
| --- |
| New-ManagementRoleAssignment -Name "<role\_name>" -Role ApplicationImpersonation -User "<user\_account>" |

For more information about the New-ManagementRoleAssignment cmdlet, see [this Microsoft article](https://learn.microsoft.com/en-us/powershell/module/exchange/new-managementroleassignment?view=exchange-ps).

Recalling Given Permissions

To recall given access level, run one of the following cmdlets:

|  |
| --- |
| Remove-ManagementRoleAssignment "<role\_name>" |

|  |
| --- |
| Remove-ManagementRoleAssignment -Identity "<role\_name>" |


