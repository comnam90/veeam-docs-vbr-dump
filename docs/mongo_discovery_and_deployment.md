---
title: "Computer Discovery and Veeam Components Deployment"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_discovery_and_deployment.html"
last_updated: "11/21/2024"
product_version: "13.0.1.1071"
---

# Computer Discovery and Veeam Components Deployment

In this article

Veeam Backup & Replication supports automated deployment of Veeam components on computers with MongoDB in your infrastructure.

To deploy Veeam components, Veeam Backup & Replication needs to discover MongoDB replica sets whose data you want to back up. To enable discovery, you must organize your MongoDB replica sets into one or more protection groups. Protection group settings define what computers Veeam Backup & Replication will discover and how the discovery process will run. To learn more, see [Protection Group for MongoDB](mongo_protection_group_hiw.md).

For automated discovery of protected computers, Veeam Backup & Replication uses the rescan job that runs on the backup server. To learn more, see [Rescan Job](mongo_rescan_job.md).

Page updated 11/21/2024

Page content applies to build 13.0.1.1071
