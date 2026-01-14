---
title: "Licensing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_preparation_licensing.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Licensing

In this article

To use the Veeam Plug-In functionality, you must have a valid Veeam Backup & Replication license. Licenses are installed and managed on the Veeam Backup & Replication server that is connected to the Veeam Plug-In server. If the license is not valid or out of resources, Veeam Plug-In backup jobs fail.

This guide provides information only on specifics of Veeam licenses for Veeam Plug-Ins. For terminology and general information about Veeam Licensing, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

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

Page updated 11/6/2025

Page content applies to build 13.0.1.1071
