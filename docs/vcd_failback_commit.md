---
title: "Failback Commit"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_failback_commit.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Failback Commit

In this article

Failback commit is one of the ways to finalize failback. When you commit failback, you confirm that the vApp to which you failed back (the production vApp) works as expected. After the commit operation, Veeam Backup & Replication resumes replication activities for the production vApp.

|  |
| --- |
| Note |
| If during failback, you have selected to switch to the production VM manually, you must first perform the switchover. |

The failback commit operation is performed in the following way:

1. Depending on whether you have failed back to the source vApp or recovered vApp:

* If you have failed back to a vApp recovered from a backup or replica, Veeam Backup & Replication reconfigures all existing jobs where the source vApp is present and adds the source vApp to the list of exclusions. The recovered vApp takes the role of the source vApp and is included into all jobs instead of the excluded vApp. When the VMware Cloud Director replication process starts, Veeam Backup & Replication processes the recovered vApp instead of the former source vApp.
* If you have failed back to the source vApp, the replication job or policy is not reconfigured. When the replication process starts, Veeam Backup & Replication still processes the source vApp.

1. Veeam Backup & Replication changes the state of the replica from Failback to Ready.

During failback commit, the failback delta disk that saves the pre-failback state of a replica is not deleted. Veeam Backup & Replication uses this delta disk as an additional restore point for replica. With the pre-failback delta disk, Veeam Backup & Replication needs to transfer fewer changes and therefore puts less load on the network when replication activities are resumed.

In This Section

* [Committing Failback](vcd_failback_committing.md)
* [Performing Failback Commit Retry](vcd_failback_commit_retry.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
