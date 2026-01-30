---
title: "Predefined Protection Groups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_default.html"
last_updated: "3/27/2025"
product_version: "13.0.1.1071"
---

# Predefined Protection Groups


In addition to protection groups created by a user, the Veeam Backup & Replication inventory may contain one or more predefined protection groups.

Unmanaged

The Unmanaged protection group acts as a filter to display computers with unmanaged Veeam Plug-Ins, that is, computers that meet the following conditions:

1. Have Veeam Agent and Veeam Plug-In deployed and configured directly from a computer side.

|  |
| --- |
| Important |
| If Veeam Plug-In only is installed on the computer, this computer will not be displayed in the Unmanaged protection group. |

1. Run a backup job targeted at a backup repository managed by Veeam Backup & Replication.

You cannot perform any operations with the Unmanaged protection group, as well as add computers included in this group to an application backup policy. However, you can move such computers to a protection group that you created. To learn more, see [Moving Unmanaged Computer to Protection Group](protected_computers_move.md).

After you move an unmanaged computer to a protection group, Veeam Backup & Replication will start managing Veeam Agent and Veeam Plug-In running on this computer according to discovery settings specified in the properties of the protection group. If the protection group is added to an application backup policy, Veeam Backup & Replication will add the new computer to the policy too. You will no longer be able to manage Veeam Agent and Veeam Plug-In directly on the computer.

Out of Date

The Out of Date protection group is displayed when Veeam Backup & Replication discovers protected computers on which an outdated version of Veeam Plug-In is installed. For example, this may happen in a situation where you configure a protection group with Veeam Plug-In deployment options disabled, and Veeam Backup & Replication detects a newer version of Veeam Plug-In on the distribution server during discovery.

The Out of Date protection group lets you update Veeam Plug-In on multiple computers at once. To learn more, see [Upgrading Plug-In](protected_computers_upgrade.md#upgrade).

Offline

The Offline protection group acts as a filter to display computers to which Veeam Backup & Replication could not connect during the latest rescan session.

Untrusted

The Untrusted protection group acts as a filter to display Linux-based computers whose fingerprints were not verified in Veeam Backup & Replication. For computers included in this protection group, you need to check and validate SSH fingerprints. To learn more, see [Adding Computers to Trusted Hosts List](security_settings_ssh_trust.md).


