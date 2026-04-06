---
title: "Licensing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_plan_and_manage_licensing.html"
last_updated: "4/1/2026"
product_version: "13.0.1.2067"
---

# Licensing


To use the MongoDB Backup functionality, you must have a valid Veeam Backup & Replication license. Licenses are installed and managed on the Veeam Backup & Replication server that is connected to the MongoDB server. If the license is not valid or out of resources, application backup policies fail.

This guide provides information only on specifics of Veeam licenses for MongoDB Backup. For terminology and general information about Veeam Licensing, see [Veeam Licensing Policy](https://www.veeam.com/licensing-policy.html).

Licensed Objects

All nodes of a MongoDB replica set are assumed protected if the replica set has been processed by an application backup policy in the last 31 days.

If you use any instance-based ([Veeam Universal Licensing](https://www.veeam.com/universal-licensing.html)) license in Veeam Backup & Replication, you do not need to install any additional licenses. Each computer including nodes of the replica set consumes one instance unit from the license. Protected computers consume instances from the license in the following way:

* In case of replica sets each server included in the replica set consumes one instance unit from the license.
* In case of shared clusters each server of each shard in the cluster consumes one instance unit from the license.

Servers processed by backup copy jobs are not regarded as protected machines, these types of jobs provide an additional protection level for machines that are already protected with application backup policies.

A computer protected on both application-level and image-level will consume a license only once. For example, you create application-level backups of the MongoDB replica set with MongoDB Backup. You also create image-level backups of Linux servers included as nodes in the replica set with Veeam Agent for Linux. In this case, only one license per server will be consumed.

|  |
| --- |
| Note |
| [For Perpetual per-socket licenses] If you are using a legacy perpetual per-socket license, a license is required for each hypervisor CPU socket occupied by protected servers.  A socket is consumed from the license only if the hypervisor where protected servers reside is added to the Veeam Backup & Replication infrastructure. If the hypervisor is not added to the Veeam Backup & Replication infrastructure, an instance unit will be consumed from the license. For details on how to add a hypervisor to the Veeam Backup & Replication infrastructure, see [Virtualization Servers and Hosts](setup_add_server.md). |

Supported License Types

You can use MongoDB Backup with the following license types and packages. Note that this guide contains information on specifics of Veeam license packages only for MongoDB Backup. For the full list of license packages, see [this Veeam webpage](https://www.veeam.com/backup-solution-pricing.html).

* For Veeam Universal license:

You can use MongoDB Backup with all license packages (Veeam Backup Essentials, Veeam Backup & Replication, Veeam Availability Suite).

Note that if you use the Rental license type, functionality of MongoDB Backup is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

* For Socket license:

Functionality of MongoDB Backup is supported only for the Enterprise Plus edition of Veeam Backup & Replication.

Obtaining and Managing Licenses

For details on how to install a license and monitor licensed objects, see [Licensing](licensing.md) for Veeam Backup & Replication.

Managing Veeam Plug-In Instance License Consumption

Veeam Backup & Replication automatically assigns a license instance to each computer added to a protected MongoDB Backup cluster. You cannot modify license use manually. However, you can restrict license consumption for specific machines to ensure only intended instances consume licenses.

|  |
| --- |
| Note |
| To run MongoDB backup jobs, select the Allow unlicensed agents to consume instances check box. When this option is enabled, Veeam Backup & Replication renews agent licenses during each backup job run by removing and reassigning them. This renewal logic ensures that licenses are correctly updated when the license is renewed on the Veeam Backup & Replication server. |

Restricting License Consumption for All Instances

To restrict instance consumption by all managed installed instances, do the following:

1. From the main menu, select License.
2. In the License Information window, click the Instances tab.
3. On the Instances tab, clear the Allow unlicensed agents to consume instances check box.
4. Click Close.

Restricting License Consumption for a Specific Instance

To restrict license use for a specific machine in a MongoDB Backup cluster, do the following:

1. From the main menu, select License.
2. In the License Information window, click the Instances tab.
3. In the Instances tab, click Manage.
4. In the Licensed Instances tab, select the installed instance and click Revoke.
5. Click Close.

![Licensing](images/mongo_license_management.webp)


