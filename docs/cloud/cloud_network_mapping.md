---
title: "Network Mapping for Cloud Replicas"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_network_mapping.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

To establish a connection between a production VM and a VM replica on the cloud host after partial site failover, Veeam Backup & Replication maps the production network and the virtual network provided to tenant replicas through the hardware plan. As a part of this process, Veeam Backup & Replication applies network settings of the replicated VM to the dedicated SP network extension appliance.

|  |
| --- |
| Note |
| This mechanism applies to both snapshot-based replicas and CDP replicas. Keep in mind that for CDP replicas, automatic network mapping is available only if application-aware processing is enabled for the VM in the CDP policy settings. |

For Windows-based VMs, Veeam Backup & Replication detects network settings of replicated VMs automatically during every run of a replication job targeted at the cloud host. Veeam Backup & Replication can detect network settings of replicated VMs in the following ways:

* [For snapshot-based replication and CDP] If application-aware processing is enabled for a replication job targeted at the cloud host, Veeam Backup & Replication collects network settings of a replicated VM with the runtime process deployed on this VM for performing guest processing tasks. The runtime process collects network settings of a VM along with information required for VSS-aware restore. To learn more, see the [Application-Aware Processing](https://helpcenter.veeam.com/docs/vbr/userguide/application_aware_processing.html?ver=13) section in the Veeam Backup & Replication User Guide.
* [For snapshot-based replication only] If application-aware processing is not enabled for a replication job targeted at the cloud host, Veeam Backup & Replication collects network settings of a replicated VM within the additional step in the replication process. To do this, Veeam Backup & Replication mounts the system disk of the replicated VM to the tenant Veeam backup server, collects network settings from the registry of the VM and passes the collected settings to the SP backup server. After that, Veeam Backup & Replication transfers VM data from the source host to the cloud host.

Keep in mind that application-aware processing is a more consistent and reliable method to collect network settings of replicated VMs.

* [For snapshot-based replication only] For VM replicas created from backup files (remote replica from backup scenario), Veeam Backup & Replication applies to the replica network settings that were collected from a VM during the backup process.

If the tenant creates replicas of Windows-based VMs and the number of production networks equals the number of virtual networks on the cloud host, the tenant does not need to specify network mapping settings. Veeam Backup & Replication maps production and virtual networks automatically. After failover, a VM replica in a cloud virtual network will act as if it is connected to the original production network.

For more advanced scenarios, the tenant can create a network mapping table for the replication job targeted at the cloud host. The tenant can perform this operation when creating a replication job, at the Network step of the New Replication Job wizard.

|  |
| --- |
| Note |
| For CDP replicas, the tenant can specify network mapping rules at the Network step of the New CDP Policy wizard. |

For example, specifying network mapping settings may be required in the following cases:

* If the cloud host has fewer networks than the number of networks in the production infrastructure.
* If non-Windows VMs are included in the replication job. Automatic network mapping for non-Windows VMs is not currently supported in Veeam Cloud Connect Replication.
* If IPv6 communication is enabled in the Veeam Cloud Connect infrastructure.

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
