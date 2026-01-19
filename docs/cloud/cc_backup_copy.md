---
title: "Backup Copy to Cloud Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_backup_copy.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Backup Copy to Cloud Repository


To follow the 3–2–1 backup best practice, you can configure a backup copy job and target it at the cloud repository. Backup copy jobs allow you to create several instances of the same backup file in different locations, onsite or offsite. For example, you can configure a backup job to create a VM backup on the local backup repository, and use the backup copy job to copy the created VM backup from the local backup repository to the cloud repository. Copied backup files have the same format as those created by backup jobs, and you can use any data recovery option for them.

During the backup copying process, Veeam Backup & Replication does not simply copy a backup file from one backup repository to another. Instead, Veeam Backup & Replication retrieves data blocks necessary to create a restore point as of the latest point in time and copies this data to the cloud repository. The backup chain produced on the target backup repository is forever-incremental: the first file in the chain is a full backup while all subsequent restore points are incremental.

The backup copy process is job-driven. When you create a backup copy job, you define what backup file you want to copy, the target repository for storing the copy, retention policy and other settings for the copying process. The backup copy job supports the GFS retention scheme, allowing you to design a long-term archiving plan.

The backup copy process differs depending on the backup copy mode: immediate copy or periodic copy.

* In the immediate copy mode, once a new restore point has been added to the primary backup chain, the backup copy job immediately copies it to the target backup repository. After that, the backup copy job stops until a new restore point appears on the source backup repository. You can specify the backup copy window to allow the job to copy restore points during specific time periods only.
* In the periodic copy mode, the backup copy job runs according to the schedule that you specify in the backup copy job settings. You can set up the job to run daily, monthly or periodically at the specified time, specify automatic job retry settings and specify the backup copy window to allow the job to copy restore points during specific time periods only. When the backup copy job starts, Veeam Backup & Replication checks the source backup repository: if a new restore point has been added to the primary backup chain, Veeam Backup & Replication automatically copies it to the target backup repository.

Supported Backup Types

Veeam Backup & Replication supports backup copy to the cloud repository for the following types of backups:

* Backups of VMware vSphere VMs created by Veeam Backup & Replication

* Backups of VMware Cloud Director VMs created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V VMs created by Veeam Backup & Replication

* Backups of Microsoft Windows machines created by Veeam Agent for Microsoft Windows
* Backups of Linux machines created by Veeam Agent for Linux
* Backups of Mac machines created by Veeam Agent for Mac
* Backups of IBM AIX machines created by Veeam Agent for IBM AIX
* Backups of Oracle Solaris machines (based on the x86 or SPARC architecture) created by Veeam Agent for Oracle Solaris

* Backups of Proxmox VE VMs created by [Veeam Backup for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* Backups of Nutanix AHV virtual machines created by [Veeam Backup for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/welcome.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)

* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)
* Backups of oVirt KVM virtual machines created by [Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)
* Backups created by backup copy jobs configured in Veeam Backup & Replication (For details, see [Support for Backup Copy from Backup Copy](#backup_copy_jobs).)

Support for Backup Copy from Backup Copy

Veeam Backup & Replication allows you to create a backup copy from another backup copy. For this operation, consider the following specifics and limitations:

* Veeam Cloud Connect supports this operation for copies of the following types of backups:

* Backups of VMware vSphere VMs created by Veeam Backup & Replication
* Backups of VMware Cloud Director VMs created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V VMs created by Veeam Backup & Replication

* Veeam Cloud Connect does not support this operation for copies of the following types of backups:

* External repository platforms, such as Amazon EC2, Microsoft Azure or Google Cloud
* Backups created by Veeam Agents

* Backups of Proxmox VE VMs created by [Veeam Backup for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* Backups of Nutanix AHV virtual machines created by [Veeam Backup for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of oVirt KVM virtual machines created by [Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)

Related Tasks

[Creating Backup Copy Jobs](cloud_connect_backup_copy.md)


