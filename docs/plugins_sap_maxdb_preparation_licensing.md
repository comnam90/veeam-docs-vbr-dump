---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_preparation_licensing.html"
last_updated: "4/21/2026"
product_version: "13.0.1.2067"
---

# Licensing


If you plan to use Veeam Plug-Ins with Veeam Backup & Replication, you must install a valid license in Veeam Backup & Replication. The license must include a sufficient number of instances to protect the application servers or databases managed by Veeam Plug-Ins. To learn more about instance licensing, see [Veeam Licensing Policy](https://www.veeam.com/legal/licensing-policy.html#instance-conversion).

Veeam Plug-In checks license validity with Veeam Backup & Replication during backup operations. If a licensing issue occurs, the backup job fails. Veeam Backup & Replication tracks all licensed plug-in instances. It groups instances with the same BIOS UUID and consumes only one license for each group. Veeam Backup & Replication assigns the license to the workload with the highest value. For example, if both a VM and a plug-in use the same UUID, only one license is consumed.

Veeam Backup & Replication frees the license instance when you revoke a plug-in instance, such as after removing a backup job or deleting a host. If another Veeam product with the same UUID exists, that product may begin to use the released license.

|  |
| --- |
| Note |
| Veeam Plug-In and Veeam Backup & Replication log all license assign and revoke events for audit and troubleshooting. Veeam licensing logic ensures that only one license is consumed per host or group, even when multiple Veeam products are installed on the same host. |

Licensed Objects

An SAP MaxDB server is assumed protected if it has been processed by a Veeam Plug-In backup job in the last 31 days.

If you are using any instance-based ([Veeam Universal Licensing](https://www.veeam.com/universal-licensing.html)) license on your Veeam Backup & Replication, you don't need to install any additional licenses. A protected SAP MaxDB server consumes one instance unit from the license. SAP MaxDB servers processed by backup copy jobs are not regarded as protected VMs, these types of jobs provide an additional protection level for VMs that are already protected with Veeam Plug-In backup jobs.

A machine protected by both Veeam Plug-In and Veeam Backup & Replication will consume a license only once. For example, you have an SAP MaxDB server that you back up using Veeam Plug-In. You also back up this server using image-level backup functionality of Veeam Backup & Replication. In this case, only one license will be consumed.

|  |
| --- |
| Note |
| [For Perpetual per-socket licenses] If you are using a legacy perpetual per-socket license, a license is required for each hypervisor CPU socket occupied by protected SAP MaxDB servers.  A socket is consumed from the license only if the hypervisor where protected servers reside is added to the Veeam Backup & Replication infrastructure. If the hypervisor is not added to the Veeam Backup & Replication infrastructure, an instance unit will be consumed from the license. For details on how to add a hypervisor to the Veeam Backup & Replication infrastructure, see [Virtualization Servers and Hosts](setup_add_server.md). |

Supported License Types and Packages

You can use Veeam Plug-Ins with the following license types and packages. Note that this guide contains information on specifics of Veeam license packages only for Veeam Plug-Ins. For the full list of license packages, see [this Veeam webpage](https://www.veeam.com/backup-solution-pricing.html).

* For Veeam Universal license:

You can use Veeam Plug-Ins with all license packages (Veeam Backup Essentials, Veeam Backup & Replication, Veeam Availability Suite).

Note that if you use the Rental license type, functionality of Veeam Plug-Ins is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

* For Socket license:

Functionality of Veeam Plug-Ins is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

Obtaining and Managing Licenses

For details on how to install a license and monitor licensed objects, see the [Licensing](licensing.md) section for Veeam Backup & Replication.


