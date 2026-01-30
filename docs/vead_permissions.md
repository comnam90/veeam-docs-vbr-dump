---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions


The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft Active Directory and restore Microsoft Active Directory data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Microsoft Active Directory launch | The account used to run Veeam Explorer for Microsoft Active Directory must meet the following requirements:   * The account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft Active Directory is running. * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft Active Directory restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore | The account used to restore Microsoft Active Directory data must be a member of the following groups:   * Domain Admins * Exchange Organization Management   Membership in this group is required only for restore of Exchange attributes. |

Assigning Role with PowerShell

To assign the Organization Management role using PowerShell, run the following cmdlet.

|  |
| --- |
| Add-RoleGroupMember “Organization Management” –Member “<user\_name>” |


