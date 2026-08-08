---
title: "Disassembling High Availability Cluster"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disassembling High Availability Cluster


After you initiate the cluster disassembly procedure, Veeam Backup & Replication removes the configuration database from the secondary node. After you disassemble an HA cluster, Veeam Backup & Replication stops synchronizing the nodes; however, the certificates and files remain in the same state they were in before the disassembly.

|  |
| --- |
| Important |
| You cannot use the secondary node as a standalone backup server after you disassemble an HA cluster cluster. To sign in, you must use the same user accounts and MFA settings that were synchronized from the primary node — for example, if MFA is enabled for the veeamadmin and veeamso accounts on the primary node, you must use those same accounts with MFA on the secondary node after disassembly. |

To disassemble an HA cluster, do the following:

1. Open the Backup Infrastructure view.
2. In the [inventory pane](vbr_ui.md), select Managed Servers.
3. In the working area, select the Linux host and click Disassemble HA Cluster on the ribbon. Alternatively, you can right-click the necessary host and select Disassemble HA Cluster.

[![Disassembling High Availability Cluster](images/high_availability_cluster_disassemble.webp)](images/high_availability_cluster_disassemble.webp)

Page updated 2026-07-17

