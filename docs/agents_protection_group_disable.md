---
title: "Disabling Protection Group"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protection_group_disable.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disabling Protection Group


You can temporary disable a protection group configured in the inventory. When you disable a protection group, you disable scheduled discovery of protected computers added to this protection group. This may be required, for example, if a new version of Veeam Agent appears on the Veeam Backup & Replication server, and you do not want to deploy Veeam Agent to all protected computers at once. Instead, you can disable the protection group, test the deployment process on a specific computer in this group, and then enable the protection group to let Veeam Backup & Replication deploy Veeam Agent to remaining computers.

When you disable a protection group, Veeam Backup & Replication does not start the rescan job upon schedule defined in the protection group settings. However, you can start the discovery process manually if needed. To learn more, see [Rescanning Protection Group](agents_protection_group_rescan.md).

Disabling a protection group does not affect processing of Veeam Agent computers included in this protection group. If a protected computer is added to a Veeam Agent backup job, and the backup job is scheduled to start at the time when the protection group is in the disabled state, the backup job will run as usual.

|  |
| --- |
| NOTE |
| You cannot disable default protection groups that act as filters used to display protected computers of a specific type: Unmanaged, Out of Date, Offline and Untrusted. |

You can disable or enable a protection group in the following ways:

* [Disabling Protection Group Using Console](#console)
* [Disabling Protection Group Using Web UI](#webui)

Disabling Protection Group Using Veeam Backup & Replication Console

To disable or enable automatic discovery for the protection group in the Veeam Backup & Replication console:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical and Cloud Infrastructure node.
3. In the inventory pane, select the necessary protection group and click Disable or Enable on the ribbon.

Alternatively, right-click the protection group and select Disable or Enable.

|  |
| --- |
| ![Disabling Protection Group](images/icon_tip.webp) TIP |
| After you disable a protection group for pre-installed , Veeam Backup & Replication does not add new members to this protection group. If the Veeam Agent computer user tries to connect to the Veeam backup server with the configuration file, the user will get an error message. To learn more about protection group types, see [Protection Group Types](agents_protection_groups_types.md). |

[![Disable Protection Group](images/protection_group_disable.webp)](images/protection_group_disable.webp "Disable Protection Group")

Disabling Protection Group Using Veeam Backup & Replication Web UI

To disable or enable automatic discovery for the protection group in the Veeam Backup & Replication web UI:

1. In the management pane, click Protection Groups.
2. Right-click the necessary protection group, or select the protection group and select Disable or Enable from the Other drop-down list.

[![Disable Protection Group](images/protection_group_disable_web.webp)](images/protection_group_disable_web.webp "Disable Protection Group")

Page updated 2026-07-03

