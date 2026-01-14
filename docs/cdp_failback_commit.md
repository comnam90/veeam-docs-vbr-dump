---
title: "Failback Commit"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_failback_commit.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Failback Commit

In this article

Failback commit is one of the ways to finalize failback. When you commit failback, you confirm that the VM to which you failed back (the production VM) and also changes sent to it during failback work as expected. After the commit operation, Veeam Backup & Replication resumes replication activities for the production VM.

|  |
| --- |
| Note |
| If you have selected to [switch to the production VM manually](cdp_failback_schedule.md), you must first perform the [switchover](cdp_failback_switch_manually.md). |

The failback commit operation is performed in the following way:

1. Veeam Backup & Replication changes the state of the replica from Failback to Ready.
2. Further operations depend on whether you have failed back to the source VM or recovered VM:

* If you have failed back to a VM recovered from a backup or replica, Veeam Backup & Replication reconfigures all existing jobs where the source VM is present and adds the source VM to the list of exclusions. The recovered VM takes the role of the source VM and is included into all jobs instead of the excluded VM. When the CDP policy starts, Veeam Backup & Replication processes the recovered VM instead of the former source VM.
* If you have failed back to the source VM, the CDP policy is not reconfigured. When the CDP policy starts, Veeam Backup & Replication still processes the source VM.

Page updated 6/14/2024

Page content applies to build 13.0.1.1071
