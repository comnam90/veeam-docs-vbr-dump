---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ad_forest_restore_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you restore a Microsoft Active Directory forest, consider the following:

* You can use only backups created with Veeam Backup & Replication version 13.1. Backups created with earlier versions cannot be used for forest recovery, even if metadata was collected after the upgrade to 13.1. Forest recovery requires this metadata for every domain controller that you select for restore. Veeam Backup & Replication also validates the Active Directory schema and requires that the schema version of the forest root domain is not lower than the schema version of any child domain.
* You cannot retry or resume a failed recovery session. To try again, you must restart the wizard from the beginning. Veeam Backup & Replication does not clean up after a failed session: any restored VMs, agent binaries and certificates remain on the target machines and must be removed manually.
* Veeam Backup & Replication supports forest recovery only for domain controllers that were backed up as VMware vSphere or Microsoft Hyper-V VMs, and restores them to VMware vSphere or Microsoft Hyper-V. Domain controllers backed up from other hypervisors are not supported.
* Each domain in the forest must have a backup of at least one domain controller. If a domain has no domain controller backup, you cannot run forest restore.
* Veeam Backup & Replication restores only one domain controller per domain, and this domain controller receives all FSMO roles, even if the domain originally had several domain controllers with the roles distributed among them. You must redeploy any additional domain controllers manually after the forest is restored.
* The forest structure is taken from the restore point that you select for the forest root domain controller. You can restore only the domains and domain controllers that are present in that restore point, and you must have backups that match it. If a domain controller was reconfigured, or a domain was added or removed after its last backup, the configuration may not match and the affected domain cannot be restored.
* Some post-restore actions may need to be performed manually. For more information, see [Post-Restore Actions](restore_ad_forest_post_restore.md).
* Domain controllers must run Windows Server 2016 or later, and the forest functional level must be Windows Server 2016 or higher. Veeam Backup & Replication does not support restore points with an Active Directory schema version earlier than Windows Server 2016.
* Veeam Backup & Replication does not support read-only domain controllers (RODCs). Only writable domain controllers are backed up and restored.
* It is recommended that you select restore points that are close together in time and not older than the shortest tombstone lifetime (TSL) configured in the forest. Otherwise, lingering objects or strict replication consistency failures may occur, halting Active Directory replication.

Permissions

To launch the Microsoft Active Directory Forest Recovery wizard, the account must have one of the following roles on the backup server:

* The Backup Administrator or Restore Operator default roles.
* A custom role with at least the Manage restores permission, with access to the target servers and the backups. For more information, see [Configuring Roles](configure_roles.md#custom_roles).

To connect to each domain controller during recovery, forest recovery requires an account with Domain Admin privileges. Only standard credentials with a user name and password are supported. Other credential types cannot be used.

Network Isolation

In case the original forest is compromised or out of date, you must restore the domain controllers to a network that is isolated from your production environment. This keeps the recovered forest from communicating with the production forest while it is brought back online. Make sure to prepare the isolated network before you start the recovery.

Whether the target must be isolated depends on the recovery scenario:

* In a full disaster recovery, when the production forest is completely down, you can restore the domain controllers to the original location, and a separate isolated network is not required.
* In test restores, migrations and similar scenarios, when the production forest is still running, the target must have no link to production. Otherwise, two copies of the same forest can contact each other and cause conflicts.

To isolate the target environment, do the following:

* On VMware vSphere, use a standard switch and port group with no uplinks and no network adapters.
* On Microsoft Hyper-V, use a private or internal virtual switch.
* Make sure that NAT and routing are not configured on the backup server, so that the isolated network cannot reach the production environment through it.

Page updated 2026-07-28

