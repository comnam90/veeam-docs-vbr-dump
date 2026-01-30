---
title: "How to Perform Bare Metal Restore for Clusters with Shared Disks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/how_to_failover_cluster_bare_metal.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# How to Perform Bare Metal Restore for Clusters with Shared Disks


Veeam Backup & Replication allows you to protect failover clusters in your infrastructure using Veeam Agent for Microsoft Windows. If cluster nodes fail to start for any reason, you can restore affected nodes.

This scenario describes how to perform bare metal restore for a Windows Server Failover Cluster with a shared disk after the majority of the voting nodes of the cluster fail to start.

|  |
| --- |
| NOTE |
| The entire computer backup must be created beforehand. To learn more, see [Select Backup Mode](agent_job_mode.md). |

1. Perform bare metal restore for each failed node of the failover cluster. The restore process is the same as for restore of a computer protected with Veeam Agent for Microsoft Windows operating in the standalone mode. To learn more, see the [Restoring from Veeam Recovery Media](https://helpcenter.veeam.com/docs/agentforwindows/userguide/image_boot.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.
2. Test the failover cluster configuration. For example, run failover cluster validation tests. To learn more, see [Microsoft Documentation](https://learn.microsoft.com/en-us/powershell/module/failoverclusters/test-cluster?view=windowsserver2022-ps).

Depending on the validation tests results, do the following:

* If the validation report does not contain errors, proceed to step 3.
* If the validation report contain errors, fix them or re-create the cluster. To learn more, see [Microsoft Documentation](https://learn.microsoft.com/en-us/windows-server/failover-clustering/create-failover-cluster).

1. Restore the cluster shared disk from the Veeam Backup & Replication console. To learn more, see [Restoring Volumes](integration_volume_restore.md).

|  |
| --- |
| IMPORTANT |
| Do not restore the cluster shared disk from the Veeam Agent computer side. In this case, you will be able to restore only to a local disk. |


