---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ad_objects_before.html"
last_updated: "8/12/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before creating a protection group, consider the following prerequisites and limitations:

* When Veeam Backup & Replication performs discovery of protected computers, Veeam Backup & Replication connects to every computer added to the protection group. If you instruct Veeam Backup & Replication to perform discovery immediately after the protection group is created, make sure that all computers added to the protection group are powered on and may be accessed over the network. Otherwise, Veeam Backup & Replication will be unable to connect to a protected computer and perform the required operations on this computer.
* A protection group that includes Microsoft Active Directory objects can include objects from one domain only. To add to the inventory computers that reside in another domain, you need to create a separate protection group and include in this protection group the necessary objects from that domain.
* Veeam Backup & Replication automatically excludes from the protection scope Active Directory objects of the Group type that exist in a parent Active Directory object (organizational unit, container or entire domain) specified in the protection group settings. To instruct Veeam Backup & Replication to process a group, you must select this group explicitly in the protection group settings.
* You cannot add or exclude universal and domain local groups to/from protection groups that include Microsoft Active Directory objects. Only global groups are supported.
* When you configure a protection group for a failover cluster, do not exclude nodes of this cluster from a protection scope. Otherwise, Veeam Backup & Replication will not have complete information about all clustered servers.

Page updated 8/12/2025

Page content applies to build 13.0.1.1071
