---
title: "Mixed Scenarios"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/recovery_verification.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Mixed Scenarios

In this article

You can start VMs from different sources in the On-Demand Sandbox:

* VM backups
* VM replicas
* VMs from storage snapshots

For example, you can add VMs from backups and VMs from storage snapshots to the same application group and link a replication job to the SureBackup job.

You cannot link jobs that trigger snapshots on storage arrays to the SureBackup job. This option is not supported.

| Type of Job/Object | SureBackup | SureReplica | SureSnap |
| --- | --- | --- | --- |
| Application group | ![Mixed Scenarios](images/yes.webp) | ![Mixed Scenarios](images/yes.webp) | ![Mixed Scenarios](images/yes.webp) |
| Linked job | ![Mixed Scenarios](images/yes.webp) | ![Mixed Scenarios](images/yes.webp) | ![Mixed Scenarios](images/no.webp) |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
