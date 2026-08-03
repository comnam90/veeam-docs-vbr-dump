---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_limitations_rhv.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for oVirt KVM, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for oVirt KVM, consider the following:

* In the case where a Veeam Backup & Replication certificate is changed it will be necessary to restart the Veeam oVirt KVM service in order to facilitate proper internal component communications.

* Veeam Plug-in for oVirt KVM does not support VDSM (Virtual Desktop and Server Manager) versions earlier than 4.50.3.5. Using an unsupported VDSM version may cause worker deployment to fail.

* Veeam Plug-in for oVirt KVM does not support the IPv6 protocol.

* Veeam Plug-in for oVirt KVM does not support synchronization of date and time settings with the backup server — the AM/PM format is used by default and cannot be changed.

* The oVirt KVM Manager must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for oVirt KVM does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) repositories. However, you can use them for [storing copies of backups](ovirt_backup_copy_job.md) created with Veeam Plug-in for oVirt KVM.

Backup

When protecting oVirt KVM resources, consider the following:

* Veeam Plug-in for oVirt KVM does not support creation of application-consistent backups.
* Veeam Plug-in for oVirt KVM only supports the following virtual disk formats for VM backup: RAW and QCOW2.
* Veeam Plug-in for oVirt KVM enables deduplication and applies 1MB block size setting for all VM backups by default. These settings cannot be changed.
* Veeam Plug-in for oVirt KVM supports VM backup operations with one backup job per VM at a time. If a VM is already being processed by a backup job, another backup job will not start processing this VM until the currently running backup operation completes.
* Veeam Plug-in for oVirt KVM cannot run a VM backup operation for a VM that already has a restore operation running. Wait for the restore process to complete, and then start the backup job.
* Veeam Plug-in for oVirt KVM does not support backup of hosted-engine VMs. However, you can create a backup of the oVirt configuration. For more information, see [Red Hat Virtualization documentation](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html-single/administration_guide/index#chap-Backups_and_Migration) or [Oracle Linux Virtualization Manager documentation](https://docs.oracle.com/en/virtualization/oracle-linux-virtualization-manager/admin/admin-vm-tasks.html#LVMAD-vm-snapshot-create-top).
* Veeam Plug-in for oVirt KVM cannot run a backup operation for a VM that already has a snapshot preview operation running. For more information, see [Red Hat Virtualization documentation](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.4/html/technical_reference/snapshot_previews) or [Oracle Linux Virtualization Manager documentation](https://docs.oracle.com/en/virtualization/oracle-linux-virtualization-manager/admin/admin-admin-tasks.html#vm-snapshot-create-top).
* Veeam Plug-in for oVirt KVM does not support backup of VMs with [shareable disks](https://www.ovirt.org/documentation/administration_guide/index.html#Shareable_Disks) or [direct LUN disks](https://www.ovirt.org/documentation/administration_guide/index.html#sect-Virtual_Disk_Tasks) attached.
* Veeam Plug-in for oVirt KVM does not support addition to the backup scope for VMs that are being backed up by 3rd party software. Wait for the backup process to complete or stop the currently running job manually, and then add the VM to the necessary backup job.
* By default, [backup encryption](data_encryption.md) is disabled for backed-up data. However, you can enable encryption at the repository level. For more information, see [Access Permissions](access_permissions.md).
* [VM guest OS file indexing](indexing.md) is not supported for backups created with Veeam Plug-in for oVirt KVM.
* Since Veeam Backup & Replication does not allow you to assign [information about locations](locations.md) to the oVirt KVM Manager, job statistics do not include information on the oVirt KVM VM data migration between different geographic regions.
* If you want to back up a VM that has been configured with a [Cloud-Init custom script](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.0/html/virtual_machine_management_guide/sect-using_cloud-init_to_automate_the_configuration_of_virtual_machines), first remove the script from the VM since it may contain secure data (such as credentials and authorized keys) that will appear in Veeam Plug-in for oVirt KVM backup logs.

Page updated 2026-07-24

