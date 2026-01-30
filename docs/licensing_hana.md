---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/licensing_hana.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Licensing


To use the Veeam Plug-In functionality, you must have a valid Veeam Backup & Replication license. Licenses are installed and managed on the Veeam Backup & Replication server that is connected to the Veeam Plug-In server. If the license is not valid or out of resources, Veeam Plug-In backup jobs fail.

This guide provides information only on specifics of Veeam licenses for Veeam Plug-Ins. For terminology and general information about Veeam Licensing, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

Licensed Objects

If you are using any instance-based ([Veeam Universal Licensing](https://www.veeam.com/universal-licensing.html)) license on your Veeam Backup & Replication, you don't need to install any additional license keys.

A machine where SAP HANA is deployed is assumed protected if it has been processed by a Veeam Plug-In backup job in the last 31 days. When you back up SAP HANA databases on one host, one License Unit is consumed from the Veeam Backup & Replication license. A machine protected by both Veeam Plug-In and Veeam Backup & Replication will consume a License Unit only once. For example, you have an SAP HANA server that you back up using Veeam Plug-In. You can also back up this server using image-level backup functionality of Veeam Backup & Replication. In this case, only one License Unit will be consumed.

|  |
| --- |
| Note |
| If you are using a legacy perpetual per-socket license, a license is required for each hypervisor CPU socket occupied by protected SAP HANA servers.  A socket is consumed from the license only if the hypervisor where protected servers reside is added to the Veeam Backup & Replication infrastructure. If the hypervisor is not added to the Veeam Backup & Replication infrastructure, an instance unit will be consumed from the license. For details on how to add a hypervisor to the Veeam Backup & Replication infrastructure, see [Virtualization Servers and Hosts](setup_add_server.md). |

|  |
| --- |
| Important |
| If you have an SAP HANA Scale-Out Cluster, each node will consume one License Unit. The License Units are consumed for all cluster nodes, even if Veeam Plug-In is installed only on one of the nodes. |

Supported License Types and Packages

You can use Veeam Plug-Ins with the following license types and packages. Note that this guide contains information on specifics of Veeam license packages only for Veeam Plug-Ins. For the full list of license packages, see [this Veeam webpage](https://www.veeam.com/backup-solution-pricing.html).

* For Veeam Universal license:

You can use Veeam Plug-Ins with all license packages (Veeam Backup Essentials, Veeam Backup & Replication, Veeam Availability Suite).

Note that if you use the Rental license type, functionality of Veeam Plug-Ins is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

* For Socket license:

Functionality of Veeam Plug-Ins is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

Obtaining and Managing Licenses

For details on how to install a license and monitor licensed objects, see [Licensing](licensing.md).


