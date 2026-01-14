---
title: "how_k10_works"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/how_k10_works.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---


In this article

To move backups exported by Veeam Kasten policies to Veeam backup repositories, a Veeam Kasten cluster and a Veeam Backup & Replication server use Veeam Data Movers. Veeam Data Mover is a non-persistent runtime component that allows you to export application disks from the Veeam Kasten cluster to backup repositories. When you start a Veeam Kasten policy, the following Veeam Data Movers are created:

* Source Veeam Data Mover — the Veeam Data Mover that runs in the Kanister Pod added to the Veeam Kasten cluster.
* Target Veeam Data Mover — the Veeam Data Mover that runs in the Veeam backup repository added to the Veeam Backup & Replication server.

After the Veeam Kasten policy is completed, Veeam Data Movers are removed from both the Veeam Kasten and Veeam Backup & Replication infrastructure. For more information, see the [Veeam Data Mover Service](https://helpcenter.veeam.com/docs/backup/vsphere/veeam_transport_service.html?ver=120) section in the Veeam Backup & Replication User Guide.

When you launch a Veeam Kasten policy, the following happens:

1. Veeam Kasten takes a snapshot of applications and uses these snapshots to make exports.
2. Veeam Kasten copies configuration files of applications to the cloud storage of a public or private cloud provider.
3. Source Veeam Data Mover retrieves application data, compresses and deduplicates it.
4. Source Veeam Data Mover exports application data to the target Veeam Data Mover.
5. Target Veeam Data Mover forwards exported application data to the Veeam backup repository in the Veeam proprietary format.

Page updated 8/26/2024

Page content applies to build 13.0.1.1071
