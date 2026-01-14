---
title: "Step 9. Configure Seeding and Mapping"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_policy_seeding_mapping.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Step 9. Configure Seeding and Mapping

In this article

The Seeding step is available if you have selected the Replica seeding check box at the [Name](cdp_policy_name.md) step of the wizard.

At the Seeding step of the wizard, configure replica seeding and mapping. Seeding and mapping help reduce the amount of traffic sent during the initial replica synchronization. For more information on when to use seeding and mapping, see [Replica Seeding and Mapping](cdp_seeding.md).

|  |
| --- |
| Important |
| If the Replica seeding check box is enabled in a policy, all VMs in the policy must be covered with seeding or mapping. If a VM is neither has a seed, nor is mapped to an existing VM, it will be skipped from processing. |

Configuring Replica Seeding

To configure replica seeding:

1. Make sure that you have backups of replicated VMs in a backup repository in the DR site. If you do not have the backups, create them as described in section [Creating Replica Seeds for CDP](creating_replica_seed.md).

|  |
| --- |
| Important |
| Consider the following:   * Backups must be created by Veeam Backup & Replication.  * Backups must not reside in a scale-out backup repository. |

1. Select the Get seed from the following backup repository check box.
2. From the list of available backup repositories, select the repository where your replica seeds are stored.

|  |
| --- |
| Note |
| If a VM has a seed and is mapped to an existing replica, replication will be performed using replica mapping because mapping has a higher priority. |

Configuring Replica Mapping

To configure replica mapping:

1. Select the Map replicas to existing VMs check box.
2. If you want Veeam Backup & Replication to scan the DR site to detect existing copies of VMs that you plan to replicate, click Detect.

If any matches are found, Veeam Backup & Replication will populate the mapping table. If Veeam Backup & Replication does not find a match, you can map a VM to its copy manually.

1. If you want to map a VM manually, select a source VM from the list, click Edit and select the copy of this VM on the target host in the DR site.

To remove a mapping association, select a VM in the list and click Remove.

![Step 9. Configure Seeding and Mapping](images/cdp_policy_mapping.webp "Configure seeding and mapping")

Page updated 8/20/2025

Page content applies to build 13.0.1.1071
