---
title: "Editing Jobs"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/editing_job_settings.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Editing Jobs


Users with the Portal Administrator role can modify settings of VMware and Hyper-V backup and replication jobs that have been previously configured on backup servers connected to Veeam Backup Enterprise Manager. In Enterprise Manager, you can change only a subset of the job settings. To edit other job settings, use the Veeam Backup & Replication console.

|  |
| --- |
| Important |
| * You can edit jobs if you have an Enterprise or Enterprise Plus license installed. * In Enterprise Manager, you cannot edit jobs that are managed by backup servers of earlier versions as well as Veeam Agent backup jobs, file backup jobs, object storage backup jobs, and backup copy jobs. To edit settings of such jobs, use the Veeam Backup & Replication console. |

In Veeam Backup Enterprise Manager, you can change the following job settings:

* Change a job name, description and retention settings for the restore points.
* Manage a list of machines that the job should process (add and remove machines or containers, exclude individual machines from containers, change the order in which the job will process machines).
* Configure guest processing settings.
* Change a job schedule.

The changes take effect with the next job run.

|  |
| --- |
| Note |
| If the Location properties of the source object and target object do not match, you will receive a warning message after you finish editing. For example, you may have a backup job targeted at repository located in Sydney, and source machines located in London. |

To edit a job, use the Edit Backup Job (or Edit Replication Job) wizard.

1. [Launch the wizard for job editing](jobs_launch_wizard.md).
2. [Edit job name and retention settings](jobs_edit_name.md).
3. [Edit the list of VMs](jobs_edit_list_of_vms.md).
4. [Change the VM processing order](jobs_change_vm_processing_order.md).
5. [Configure guest processing settings](jobs_edit_guest_settings.md).
6. [Edit job scheduling settings](jobs_edit_schedule.md).


