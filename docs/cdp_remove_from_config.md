---
title: "Removing Replicas from Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_remove_from_config.html"
last_updated: "9/25/2025"
product_version: "13.0.1.1071"
---

# Removing Replicas from Configuration


When you remove replicas from the configuration, Veeam Backup & Replication removes records about the replicas from the configuration database, stops showing the replicas in Veeam Backup & Replication console and also stops synchronizing their state with the state of the source VMs. However, the actual replicas remain on hosts.

To remove records about replicas from the Veeam Backup & Replication console and configuration database:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), click the Replicas node.
3. In the working area, select replicas in the Ready state and click Remove from > Configuration on the ribbon. Alternatively, right-click one of the selected replicas and select Remove from configuration.

|  |
| --- |
| Note |
| Consider the following:   * You can remove records only about replicas in the Ready state. * When you remove from the configuration a VM that is replicated as a standalone object, Veeam Backup & Replication removes this VM from the initial replication job. When you remove from the configuration a VM that is replicated as part of a VM container, Veeam Backup & Replication adds this VM to the [list of exclusions](cdp_policy_exclude.md) in the CDP policy. * When you remove from the configuration a replica, Veeam Backup & Replication consolidates the replica into a regular VM. Veeam Backup & Replication removes technical files, such as transaction log and delta disk files, and commits data from them into the VM. |

[![Remove replicas from configuration](images/replica_remove_from_config.webp)](images/replica_remove_from_config.webp "Remove replicas from configuration")


