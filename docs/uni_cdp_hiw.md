---
title: "How Universal CDP Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_hiw.html"
last_updated: "10/29/2025"
product_version: "13.0.1.1071"
---

# How Universal CDP Works


This section describes how universal CDP works during replication. To learn how universal CDP works during data recovery, see [Failover and Failback for Universal CDP](uni_cdp_failover_failback.md).

Universal CDP workflow during replication is divided into two parts: backup infrastructure component configuration and data transfer.

During the configuration, Veeam Backup & Replication configures the [required backup infrastructure components](uni_cdp_infrastructure.md). Veeam Backup & Replication also reconfigures the components if something changes in the infrastructure. During data transfer, Veeam Backup & Replication creates short-term and long-term restore points by sending disk data blocks and changes made to them. For more information on restore points, see [CDP Replication Chain](uni_cdp_replica_chain.md).

Backup infrastructure component configuration and data transfer are constant processes.

Component Configuration Algorithm

The following steps apply during the initial configuration, that is, when a [universal CDP policy](uni_cdp_policy_create.md) starts for the first time or after the policy is enabled:

1. Veeam CDP Coordinator Service reads policy settings from the configuration database and creates a list of workload tasks to process. For every workload added to the universal CDP policy, Veeam Backup & Replication creates a new task.
2. Veeam CDP Coordinator Service checks that required backup infrastructure components are available.
3. Veeam CDP Coordinator Service queries information about workloads from the Veeam CDP Agent Service. The information contains data about the guest OS, hardware, network adapters and storage layout.
4. Veeam CDP Agent Service transforms the storage layout information into a synthetic disk layout. This is required to create a similar disk structure on the target host.
5. Veeam CDP Coordinator Service queries information about virtualization hosts from the target vCenter Server.
6. Veeam CDP Coordinator Service requests vCenter Server to create replicas with empty disks on the target host. They are created based on the synthetic disk layout. The volumes (disk layout) are created during the data transfer process.
7. vCenter Server registers the created replicas.
8. Veeam CDP Coordinator Service selects which CDP proxies will be used for data transfer and sets a number of rules for data transfer, such as network traffic throttling rules and so on.

If you select automatic proxy selection when configuring the CDP policy, Veeam Backup & Replication analyzes the current workload on CDP proxies and selects a CDP proxy according to the following priority rules (starting from the most preferable one):

* CDP proxy on a physical machine.
* CDP proxy on a VM located in the same cluster — that is, the source proxy in the cluster where source VMs are located (on any host), the target proxy in the cluster where VM replicas are located (on any host).
* Other CDP proxies.

For more information on how to specify the proxy selection mode, see [Specify Data Transfer and Replica Settings](uni_cdp_policy_data_transfer.md).

1. Veeam CDP Coordinator Service sends to the backup infrastructure components configurations required for CDP. This configuration includes such information as RPO, short-term and long-term retention settings.
2. Veeam CDP Coordinator Service gets information about the volumes (disk layout).
3. Veeam CDP Coordinator Service requests Veeam CDP Agent Service to attach the Veeam CDP Volume Filter Driver to each volume on the source workload. This driver intercepts I/O operations.

After the initial configuration finishes, Veeam Backup & Replication starts monitoring the backup infrastructure. If something changes in the infrastructure or CDP policy settings, Veeam Backup & Replication reconfigures the components. Consider the following examples:

* If a CDP proxy becomes unavailable, Veeam CDP Coordinator Service on the backup server gets a notification that this proxy is no longer available. Then, the service selects another proxy.

|  |
| --- |
| Note |
| If you add new proxies to the backup infrastructure, Veeam Backup & Replication does not use these proxies for the already created CDP policies — that is, Veeam Backup & Replication does not reconfigure the infrastructure. If you have selected automatic proxy selection for a CDP policy and want to use the newly added proxies, disable and then enable the CDP policy. If you have selected the proxies manually, edit the CDP policy settings and add the required proxies. |

* If disks are added to source workload, Veeam CDP Coordinator Service requests vCenter to create the disks on the target host and selects CDP proxies to transfer disk data. Veeam CDP Coordinator Service also gets information about volumes and requests the Veeam CDP Agent Service to attach the Veeam CDP Volume Filter Driver to this volume.
* If disk layout is changed on the source workload, Veeam CDP Coordinator Service also gets information about volumes and requests the Veeam CDP Agent Service to attach the Veeam CDP Volume Filter Driver to this volume. The Veeam CDP Agent Service initiates disk mapping: calculates the differences between the source workload and replica, and send the differences to the replica.
* If new workloads are added to the CDP policy, Veeam CDP Coordinator Service requests vCenter to create replicas with empty disks, and selects which CDP proxies to use for data transfer. Veeam CDP Coordinator Service also gets information about volumes and requests the Veeam CDP Agent Service to attach the Veeam CDP Volume Filter Driver to this volume.

Component reconfiguration requires Veeam CDP Coordinator Service to be working. If the coordinator goes down, existing CDP policies still work, create and remove short-term restore points. Long-term restore points are not created and removed because it is the coordinator who manages them. However, if any of the components goes out of service, for example, CDP proxy goes offline or VMware vSphere vMotion changes the infrastructure, CDP policies start failing until Veeam CDP Coordinator Service is repaired.

Data Transfer Algorithm

Data transfer starts right after Veeam Backup & Replication configures the backup infrastructure components (performs the initial configuration). Data transfer differs during the initial synchronization and during the incremental synchronization.

As a rule, the initial synchronization is performed when disk data is sent to the target host for the first time. During the initial synchronization, Veeam Backup & Replication sends data for full copies of disks and creates the very first restore points.

During the incremental synchronization, Veeam Backup & Replication mainly sends data for incremental changes made to disks and creates short-term and long-term restore points. For more information on restore points and files created for replicas, see [CDP Replication Chain](cdp_replica_chain.md).

Data Transfer Algorithm During Initial Synchronization

The following steps apply to data transfer during the initial synchronization:

1. On the source workload, the Veeam CDP Volume Filter Driver intercepts all data from volumes and sends it to the Veeam CDP Agent Service.

As the source VMs are still running, data for the already transferred data blocks can change. The driver intercepts these changes and sends them to the Veeam CDP Agent Service. Sending changes instead of whole changed data blocks helps minimize traffic sent over the network.

1. Veeam CDP Agent Service sends data to the source proxy.
2. Veeam CDP Proxy Service on the source proxies compresses the received data and sends it to the target proxy.
3. Veeam CDP Proxy Service on the target proxies decompresses the received data. Then sends data to the target host.
4. I/O filter on the target host saves the received data to virtual disks. The saved data relates to the very first long-term restore point. This restore point is crash-consistent.

If traffic encryption is configured and the IP addresses of components fall under the rules, these components also encrypt data before sending it. They also decrypt the received data before performing any operations with data if it was encrypted. For more information, see [Enabling Traffic Encryption](enable_network_encryption.md).

After the initial synchronization finishes, Veeam Backup & Replication starts the incremental synchronization.

Data Transfer Algorithm During Incremental Synchronization

During the incremental synchronization, Veeam Backup & Replication creates short-term and long-term restore points. To create short-term restore points, Veeam Backup & Replication intercepts changes made by transactions on workload volumes and sends these changes to the target host. Changes are constantly transferred and are saved to transaction logs on the target datastore. To create long-term restore points, Veeam Backup & Replication uses data of short-term restore points and saves the restore points to delta disks. Long-term restore points are created by schedule.

The following steps apply when Veeam Backup & Replication transfers data for short-term restore points:

1. On the source workload, the Veeam CDP Volume Filter Driver intercepts data of all I/O operations and sends this data to the Veeam CDP Agent Service.
2. Veeam CDP Agent Service sends data to the source proxy.
3. Once in the RPO, the Veeam CDP Proxy Service on the source proxies prepares data required for a short-term restore point. For this, Veeam CDP Proxy Service gets the latest state of the data that the source CDP proxies have accumulated.
4. Source Veeam CDP Proxy Service compresses data and sends it to the target proxy.
5. Target Veeam CDP Proxy Service decompresses the received data. Then sends data to the target host.
6. I/O filter on the target host saves the received data to transaction logs.

When the time for the creation of a long-term restore point comes, the I/O filter forms a long-term restore point using data of short-term restore points created since the creation of the previous long-term restore point. Data for the new long-term restore point is saved to a delta disk.

|  |
| --- |
| Note |
| If traffic encryption is configured and the IP addresses of components fall under the rules, these components also encrypt data before sending it. They also decrypt the received data before performing any operations with data if it was encrypted. For more information, see [Enabling Traffic Encryption](enable_network_encryption.md). |

CDP Policy Statuses

Based on the workflow, CDP policies can have the following statuses:

* Initial sync — the initial synchronization is in process.
* Syncing — the incremental synchronization is in process.
* CBT mode — the replica data on the target host is not actual. This status can be shown, for example, if a CDP proxy is overloaded and cannot receive or send data. The status can change for Syncing after the workload decreases and replica data on the target host is updated to the current VM state on the source host. For more information on how Veeam Backup & Replication behaves in case of data delivery issues, see [Guaranteed Delivery](cdp_guaranteed_delivery.md).
* Success, Warning or Error — the CDP process was successful, had warnings or failed. These statuses are shown for the disabled CDP policies.


