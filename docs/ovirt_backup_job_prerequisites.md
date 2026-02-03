---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_backup_job_prerequisites.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a backup job, consider the following limitations:

* You can back up each VM with one backup job at a time. If a VM is already being processed by a backup job, another backup job will not start processing this VM until the currently running backup operation completes.

* You cannot back up a VM being restored. Wait for the restore process to complete, and then start the backup job.

* You cannot back up hosted-engine VMs. However, you can create a backup of the oVirt configuration. For more information, see [Red Hat Virtualization documentation](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html-single/administration_guide/index#chap-Backups_and_Migration) or [Oracle Linux Virtualization Manager documentation](https://docs.oracle.com/en/virtualization/oracle-linux-virtualization-manager/admin/getstarted-backup-restore.html).
* You cannot back up a VM while previewing its snapshot. For more information, see [Red Hat Virtualization documentation](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html/technical_reference/snapshot_previews) or [Oracle Linux Virtualization Manager documentation](https://docs.oracle.com/en/virtualization/oracle-linux-virtualization-manager/admin/admin-vm-tasks.html#vm-snapshot-create-top).

* You cannot back up a VM that has [shareable disks](https://www.ovirt.org/documentation/administration_guide/index.html#Shareable_Disks) or [direct LUN disks](https://www.ovirt.org/documentation/administration_guide/index.html#sect-Virtual_Disk_Tasks) attached.

* You cannot include into a backup job a VM that is being backed up by 3rd party software. Wait for the backup process to complete or stop the currently running job manually, and then add the VM to the necessary backup job.

* By default, Veeam Plug-in for oVirt KVM applies the following [deduplication and compression settings](https://helpcenter.veeam.com/docs/backup/vsphere/compression_deduplication.html?ver=120) to backed-up data:

+ Deduplication: Enabled
+ Data compression level: Optimal
+ Storage optimization: Local target (1024 KB block size)

Due to technical limitations, you cannot change these settings while configuring backup jobs.

* By default, [backup encryption](https://helpcenter.veeam.com/docs/backup/vsphere/data_encryption.html?ver=120) is disabled for backed-up data. However, you can enable encryption at the repository level. For more information, see [Access Permissions](https://helpcenter.veeam.com/docs/backup/vsphere/access_permissions.html?ver=120).
* [VM guest OS file indexing](https://helpcenter.veeam.com/docs/backup/vsphere/indexing.html?ver=120) is not supported for backups created with Veeam Plug-in for oVirt KVM.

* Since Veeam Backup & Replication does not allow you to assign [information about locations](https://helpcenter.veeam.com/docs/backup/vsphere/locations.html?ver=120) to the oVirt KVM Manager and worker, job statistics do not include information on the oVirt VM data migration between different geographic regions.

* If you want to back up a VM that has been configured with a [oVirt KVM Virtualization Cloud-Init custom script](https://access.redhat.com/documentation/ru-ru/red_hat_virtualization/4.0/html/virtual_machine_management_guide/sect-using_cloud-init_to_automate_the_configuration_of_virtual_machines#doc-wrapper), first remove the script from the VM since it may contain secure data (such as credentials and authorized keys) that will appear in Veeam Plug-in for oVirt KVM backup logs.


