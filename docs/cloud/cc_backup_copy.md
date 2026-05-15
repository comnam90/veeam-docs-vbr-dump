---
title: "Backup Copy to Cloud Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_backup_copy.html"
last_updated: "5/13/2026"
product_version: "13.0.1.2067"
---

# Backup Copy to Cloud Repository


To follow the 3–2–1 backup best practice, you can configure a backup copy job and target it at the cloud repository. Backup copy jobs allow you to create several instances of the same backup file in different locations, onsite or offsite. For example, you can configure a backup job to create a VM backup on the local backup repository, and use the backup copy job to copy the created VM backup from the local backup repository to the cloud repository. Copied backup files have the same format as those created by backup jobs, and you can use any data recovery option for them.

During the backup copying process, Veeam Backup & Replication does not simply copy a backup file from one backup repository to another. Instead, Veeam Backup & Replication retrieves data blocks necessary to create a restore point as of the latest point in time and copies this data to the cloud repository. The backup chain produced on the target backup repository is forever-incremental: the first file in the chain is a full backup while all subsequent restore points are incremental.

The backup copy process is job-driven. When you create a backup copy job, you define what backup file you want to copy, the target repository for storing the copy, retention policy and other settings for the copying process. The backup copy job supports the GFS retention scheme, allowing you to design a long-term archiving plan.

The backup copy process differs depending on the backup copy mode: immediate copy or periodic copy.

* In the immediate copy mode, once a new restore point has been added to the primary backup chain, the backup copy job immediately copies it to the target backup repository. After that, the backup copy job stops until a new restore point appears on the source backup repository. You can specify the backup copy window to allow the job to copy restore points during specific time periods only.
* In the periodic copy mode, the backup copy job runs according to the schedule that you specify in the backup copy job settings. You can set up the job to run daily, monthly or periodically at the specified time, specify automatic job retry settings and specify the backup copy window to allow the job to copy restore points during specific time periods only. When the backup copy job starts, Veeam Backup & Replication checks the source backup repository: if a new restore point has been added to the primary backup chain, Veeam Backup & Replication automatically copies it to the target backup repository.

For more information, see the [Backup Copy](https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy.html?ver=13) section in the Veeam Backup & Replication User Guide.

Supported Backup Types

Veeam Cloud Connect supports backup copy to the cloud repository for backups of the following workloads created by Veeam Backup & Replication:

* [VMware vSphere VMs](https://helpcenter.veeam.com/docs/vbr/userguide/vmware_vsphere.html?ver=13)
* [VMware Cloud Director VMs](https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director.html?ver=13)
* [Microsoft Hyper-V VMs](https://helpcenter.veeam.com/docs/vbr/userguide/ms_hyperv.html?ver=13)
* [Nutanix AHV VMs](https://helpcenter.veeam.com/docs/vbr/userguide/ahv_overview.html?ver=13)
* [Proxmox VE VMs](https://helpcenter.veeam.com/docs/vbr/userguide/pve_overview.html?ver=13)
* [HPE Morpheus VM Essentials VMs](https://helpcenter.veeam.com/docs/vbr/userguide/hpe_morpheus_vme.html?ver=13) (requires installation of the HPE Morpheus plug-in)
* [oVirt KVM VMs](https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_overview.html?ver=13)
* Backups created by backup copy jobs configured in Veeam Backup & Replication (For details, see [Support for Backup Copy from Backup Copy](#backup_copy_jobs).)

Veeam Cloud Connect supports backup copy to the cloud repository for the following types of backups created by [Veeam Agents](https://helpcenter.veeam.com/docs/vbr/userguide/protect_comp.html?ver=13):

* Microsoft Windows machines
* Linux machines
* Mac machines
* IBM AIX machines
* Oracle Solaris machines (based on the x86 or SPARC architecture)

Veeam Cloud Connect supports backup copy to the cloud repository for backups of the following workloads created by Veeam products for public cloud backup:

* [Amazon EC2 instances](https://helpcenter.veeam.com/docs/vbaws/guide/welcome.html?ver=10)

* [Microsoft Azure VMs](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* [Google Compute Engine VM instances](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)

Support for Backup Copy from Backup Copy

Veeam Backup & Replication allows you to create a backup copy from another backup copy. For this operation, consider the following specifics and limitations:

* Veeam Cloud Connect supports this operation for copies of the following types of backups:

* VMware vSphere VMs
* VMware Cloud Director VMs
* Microsoft Hyper-V VMs

* Veeam Cloud Connect does not support this operation for copies of the following types of backups:

* Nutanix AHV VMs
* Proxmox VE VMs
* HPE Morpheus VM Essentials VMs (requires installation of the HPE Morpheus plug-in)
* oVirt KVM VMs
* Backups created by Veeam Agents
* Backups of cloud workloads, such as Amazon EC2, Microsoft Azure or Google Cloud, created by Veeam products for public cloud backup

Related Tasks

[Creating Backup Copy Jobs](cloud_connect_backup_copy.md)


