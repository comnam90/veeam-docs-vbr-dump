---
title: "Failback Commit"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failback_commit.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# Failback Commit


Failback commit is one of the ways to finalize failback. When you commit failback, you confirm that the VM to which you failed back (the production VM) and also changes sent to it during failback work as expected. After the commit operation, Veeam Backup & Replication resumes replication activities for the production VM.

|  |
| --- |
| Note |
| If you have selected to [switch to the production VM manually](uni_cdp_failback_schedule.md), you must first perform the [switchover](uni_cdp_failback_switch_manually.md). |

The failback commit operation is performed in the following way:

1. Veeam Backup & Replication changes the state of the replica from Failback to Ready.
2. Veeam Backup & Replication reconfigures all existing jobs where the source workload is present and adds the source workload to the list of exclusions. The production VM (VM recovered from replica) takes the role of the source workload and is included into all jobs instead of the excluded workload. When the CDP policy starts, Veeam Backup & Replication processes the production VM (recovered VM) instead of the former source workload.


