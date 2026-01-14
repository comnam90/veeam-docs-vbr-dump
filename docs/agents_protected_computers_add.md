---
title: "Adding Computer to Backup Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_protected_computers_add.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Adding Computer to Backup Job

In this article

You can quickly add a specific protected computer to a Veeam Agent backup job that you have configured in Veeam Backup & Replication. To do this, do the following:

1. Open the Inventory view.
2. In the inventory pane, in the Physical and Cloud Infrastructure node, select a protection group whose computers you want to add to a Veeam Agent backup job and do one of the following:

* In the working area, select the computer that you want to add to the job and click Add to Backup > name of the job on the ribbon.
* In the working area, right-click the computer that you want to add to the job and select Add to backup job > name of the job.

|  |
| --- |
| NOTE |
| Consider the following:   * You can add a computer to a Veeam Agent backup job configured for computers of the same platform. For example, you can add a Linux computer only to a Veeam Agent backup job for Linux computers. * You can also add a specific protected computer to a new backup job. To learn more, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md). |

[![Add Computers to Backup Job](images/protected_computer_add.webp)](images/protected_computer_add.webp "Add Computers to Backup Job")

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
