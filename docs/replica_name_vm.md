---
title: "Step 2. Specify Job Name and Description"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_name_vm.html"
last_updated: "5/1/2025"
product_version: "13.0.1.1071"
---

# Step 2. Specify Job Name and Description

In this article

At the Name step of the wizard, specify a job name and description, and configure advanced settings for the replication job:

1. In the Name field, enter a name for the replication job.
2. In the Description field, provide a description for future reference.
3. If a network between your production and disaster recovery (DR) sites has low bandwidth, and you want to reduce the amount of traffic sent during the first run of the replication job, select the Replica seeding (for low bandwidth DR sites) check box.

When selected, this check box enables the Seeding step where you will have to configure replica seeding and mapping.

1. If your DR site networks do not match your production site networks, select the Network remapping (for DR sites with different virtual networks) check box.

When selected, this check box enables the Network step where you will have to configure a network mapping table.

1. If the IP addressing scheme in your production site differs from the scheme in the DR site, select the Replica re-IP (for DR sites with different IP addressing scheme) check box.

When selected, this check box enables the Re-IP step where you will have to configure replica re-IP rules.

1. If you want the resource scheduler of Veeam Backup & Replication to prioritize this job higher than other similar jobs and to allocate resources to it in the first place, select the High priority check box. For more information on job priorities, see [Job Priorities](job_priorities.md).

|  |
| --- |
| Tip |
| In the list of jobs in the Veeam Backup & Replication console, jobs with the High priority option enabled are marked with double green arrows (![Step 2. Specify Job Name and Description](images/high_priority_job.webp)). |

![Step 2. Specify Job Name and Description](images/vm_replica_job_name.webp)

Related Topics

[Replica Seeding and Mapping](replica_seeding.md)

Page updated 5/1/2025

Page content applies to build 13.0.1.1071
