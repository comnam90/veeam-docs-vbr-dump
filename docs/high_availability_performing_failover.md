---
title: "Performing Failover"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/high_availability_performing_failover.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Performing Failover


To initiate a failover, do the following:

1. Connect to the cluster using the cluster IP address.
2. The Veeam Backup & Replication console displays this warning: The primary cluster node is offline. The console will display information on how long the node has not been available.
3. Click Failover.

After the failover is completed, use the cluster IP address to connect to the cluster.

|  |
| --- |
| Important |
| Before you initiate a failover, ensure that the primary node is offline and will not revert to online status during the failover. Otherwise, it may lead to split-brain scenarios. |

![Performing Failover](images/high_availability_cluster_failover.webp)


