---
title: "NDMP Servers Backup to Tape"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ndmp_servers_backup_to_tape.html"
last_updated: "2/5/2026"
product_version: "13.0.1.1071"
---

# NDMP Servers Backup to Tape


If your NAS device supports the NDMP protocol, you can back up data from it to tape. For this, you need to utilize the file to tape job.

|  |
| --- |
| Note |
| The availability of the feature depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf). |

To back up data from NAS devices by the NDMP protocol, you need to add the device as an NDMP server. For details, see [Adding NDMP Servers](adding_ndmp_servers.md).

|  |
| --- |
| Important |
| Even if the NAS device supporting NDMP protocol is already added to Veeam Backup & Replication, you need to add the NDMP server as a separate procedure. Otherwise you will not be able to perform file backup to tape. |

Requirements for NDMP Servers

NDMP version 4 or higher is supported.

Number of Restore Points

For all NDMP devices, the backup chain stored on tapes will consist of 10 restore points maximum. On the 11th run, Veeam Backup & Replication will force an active full.

Limitations for NDMP Servers

* Only backup of whole volume is supported.
* Both the NetApp node-scoped NDMP mode and the NetApp Cluster Aware Backup (CAB) extension of the NDMP protocol are supported:

* In node-scoped configuration, add each cluster node to the backup user interface specifying a data LIF IP/DNS address associated with the node.
* To support backup of NetApp CAB extension, add the NDMP server with IP address of the cluster management interface or with the NAS server name resolving to this IP address.

* Only in-direct NDMP backup is supported. Veeam Backup & Replication moves the backup data from the NDMP server via the backup proxy server and tape server directly to the tape drive.
* The NDMP server performs its own backup consistency check for the NDMP volumes. To ensure the correct calculation of the delta of changes and the backup chain integrity, Veeam Backup & Replication does not allow adding one NDMP volume to more than one file to tape job.
* For the NDMP server backup to a media pool with the Process independent data sources simultaneously option enabled, Veeam Backup & Replication processes NDMP volumes in parallel, with each volume written by a separate drive. For more information, see [Tape Parallel Processing](parallel_processing.md).

See Also

[File Restore from Tape](file_restore_from_tape.md)


