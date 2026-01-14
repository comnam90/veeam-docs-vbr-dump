---
title: "Replication Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/replication.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Replication Jobs

In this article

The Veeam PowerShell Snap-In contains full set of capabilities for running replication tasks.

In This Section

| VMware | Hyper-V | Operation |
| --- | --- | --- |
| [Add-VBRViReplicaJob](add-vbrvireplicajob.md) | [Add-VBRHvReplicaJob](add-vbrhvreplicajob.md) | Creates replication jobs. |
| [Set-VBRViReplicaJob](set-vbrvireplicajob.md) | [Set-VBRHvReplicaJob](set-vbrhvreplicajob.md) | Modifies replication jobs. |
| — | [Reset-HvVmChangeTracking](reset-hvvmchangetracking.md) | Clears change tracking data. |

|  |
| --- |
| Important! |
| The jobs are created in stopped status. |

To run the jobs or to configure job additional settings, use the cmdlets in the following sections:

* [Working with Jobs](working_with_jobs.md)
* [VMs in Job](vms_in_job.md)
* [Replica Re-IP Rules](replica_re-ip_rules.md)
* [Job Schedule](job_schedule.md)
* [Job Options](job_options.md)
* [Application-Aware Processing](application_aware_processing.md)
* [Guest File System Indexing](guest_fs_indexing.md)
* [Advanced Job Options](advanced_job_options.md)

|  |
| --- |
| Tip |
| After you have created a job and configured additional settings, you can clone it. To the clone job, you can apply minor editing, such as changing the name and adding another source VMs. Run the [Copy-VBRJob](copy-vbrjob.md) cmdlet to clone a job. |

See Also

* [Replicas](replicas.md)
* [Failover and Failback](replica_cmdlets.md)
* [Failover Plans](fplan_cmdlets.md)
* [Restore Points](point_cmdlets.md)
* [Sessions](session_cmdlets.md)

Page updated 6/27/2024

Page content applies to build 13.0.1.1071
