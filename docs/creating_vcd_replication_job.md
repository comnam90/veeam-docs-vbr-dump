---
title: "Creating Cloud Director Replication Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/creating_vcd_replication_job.html"
last_updated: "6/26/2023"
product_version: "13.0.1.1071"
---

# Creating Cloud Director Replication Job

In this article

To replicate a vApp or another VM container, you must configure a VMware Cloud Director replication job. The VMware Cloud Director replication job defines a scope of VM containers to replicate, where to store replicated VM containers and how often to replicate VM containers. Every time the VMware Cloud Director replication job runs, replica snapshots are created on the VMs that are added to the target vApp. If a disaster strikes, you can fail over to the necessary restore point of your VM container. During failover, Veeam Backup & Replication shifts from the source VM container to their replicas. As a result, you have fully functional vApps within a couple of seconds, and your users can access services and applications with minimum disruption.

|  |
| --- |
| Important |
| VMware Cloud Director replication job does not support replication of a single VM that is added to a vApp. You can replicate only vApps or VM containers. |

To create a VMware Cloud Director replication job, do the following:

1. [Check prerequisites](vcdreplica_byb.md).
2. [Launch the New Replication Job wizard](cdp_replica_launch.md).
3. [Specify a job name and advanced settings](vcd_replica_job_name.md).
4. [Select vApps to replicate](vcd_replication_vapps.md).
5. [Exclude objects from a replication job](vcd_replica_exclusions.md).
6. [Specify the vApp processing order](vcd_replica_processing_order.md).
7. [Select a destination for replicas](vcd_replica_destination.md).
8. [Configure network mapping](vcd_replica_network.md).
9. [Specify replication job settings](vcd_replication_job_settings.md).
10. [Specify advanced replica settings](vcd_replica_advanced.md).
11. [Specify data transfer and replica settings](vcd_replica_data_transfer.md).
12. [Configure seeding and mapping settings](vcd_seeding_and_mapping.md).
13. [Specify guest processing settings](vcd_guest_processing.md).
14. [Define a job schedule](vcd_schedule.md).
15. [Finish working with the wizard](vcd_finish.md).

Page updated 6/26/2023

Page content applies to build 13.0.1.1071
