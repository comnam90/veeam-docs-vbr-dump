---
title: "Network Mapping"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_replica_network_mapping.html"
last_updated: "8/2/2023"
product_version: "13.0.1.1071"
---

# Network Mapping


To establish a connection between a production VM and its replica, Veeam Backup & Replication uses network mapping.

Network mapping is implemented with the help of a network mapping table. This table contains networks in the production site and suitable networks in the disaster recovery (DR) site. When the replication session starts, Veeam Backup & Replication checks the network mapping table. Then Veeam Backup & Replication updates replica configuration to replace the production networks with the specified networks in the DR site.

Veeam Backup & Replication supports the following types of network mapping:

* Manual network mapping.

During manual network mapping, Veeam Backup & Replication uses the network mapping table that a user creates when [configuring a replication job](vcd_replica_network.md).

* Automatic network mapping.

During automatic network mapping, Veeam Backup & Replication analysis networks in the DR site and searches for the networks with the same names as in the production site. If such networks are found, Veeam Backup & Replication tries to configure network connections similar to the production site. This mapping applies to networks for which manual mapping is not configured.

|  |
| --- |
| Note |
| Cloud Director replication jobs do not support network mapping of vApp networks. You can configure a mapping table for organization VDC networks only. |

Replica Network Settings Configuration

How Veeam Backup & Replication configures replica network settings depends on how IP addresses are allocated for the source VM NICs.

DHCP Allocation Mode

If DHCP allocation mode is used on the source VM, replica NIC settings are the following:

* If mapping (manual or automatic) was performed — NIC is connected, the IP mode is DHCP and new MAC address is assigned.
* If mapping (manual or automatic) was not performed — NIC is disconnected, the IP mode is not set and new MAC address is assigned.

Static-Manual IP Allocation Mode

If static-manual IP allocation mode is used on the source VM, replica NIC settings are the following:

* If mapping (manual or automatic) was performed — NIC is disconnected, the IP mode is not set and new MAC address is assigned.
* If mapping (manual or automatic) was not performed — NIC is disconnected, the IP mode is not set and new MAC address is assigned.

If manual mapping is used, you can connect a replica NIC after the first replication job run. However, note that to stay connected the following NIC settings must be the same as on the source VM: connection state, primary NIC value and network adapter type. Also, the replica NIC network must be the same as the mapped network (the target network from the mapping table). If any of these parameters differs, the NIC will be disconnected after the next job run.

Static IP Pool Allocation Mode

If static IP pool allocation mode is used on the source VM, Veeam Backup & Replication assigns replica NIC settings in the following way:

* If mapping (manual or automatic) was performed — NIC is connected, the IP mode is DHCP and new MAC address is assigned.
* If mapping (manual or automatic) was not performed — NIC is disconnected, the IP mode is not set and new MAC address is assigned.


