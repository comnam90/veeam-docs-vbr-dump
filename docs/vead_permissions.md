---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Permissions


The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft Active Directory and restore Microsoft Active Directory data.

Permissions

| Operation | Required Roles and Permissions |
| Veeam Explorer for Microsoft Active Directory launch | The account used to run Veeam Explorer for Microsoft Active Directory must meet the following requirements:   * [For Explorer console] The account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft Active Directory is running. * The account must have one of the following roles on the backup server:  * The Backup Administrator or Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft Active Directory restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore | The account used to restore Microsoft Active Directory data must be a member of the following groups:   * Domain Admins * Exchange Organization Management   Membership in this group is required only for restore of Exchange attributes. |

Assigning Role with PowerShell

To assign the Organization Management role using PowerShell, run the following cmdlet.

|  |
| --- |
| Add-RoleGroupMember “Organization Management” –Member “<user\_name>” |

Page updated 2026-07-13

