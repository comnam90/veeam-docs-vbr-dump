---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for Universal Hypervisor API, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Universal Hypervisor API, consider the following:

* In the case where a Veeam Backup & Replication certificate is changed it will be necessary to restart the Veeam services in order to facilitate proper internal component communications.

* Veeam Plug-in for Universal Hypervisor API does not support the IPv6 protocol.

* Veeam Plug-in for Universal Hypervisor API does not support synchronization of date and time settings with the backup server — the AM/PM format is used by default and cannot be changed.

* The Universal Hypervisor Manager must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for Universal Hypervisor API does not support storing backups in [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13) repositories. However, you can use them for [storing copies of backups](uh_backups_copy.md) created with Veeam Plug-in for Universal Hypervisor API.

Workers

When configuring workers, consider the following:

* [Applies only to Platform9] Veeam Plug-in for Universal Hypervisor API does not support deploying a worker with a static IP address due to technical limitations of the hypervisor.
* [Applies only to Platform9] Veeam Plug-in for Universal Hypervisor API does not support deploying host affinity configuration for workers due to technical limitations of the hypervisor.

Backup

When protecting universal hypervisor resources, consider the following:

* Veeam Plug-in for Universal Hypervisor API does not support creation of application-consistent backups.
* Veeam Plug-in for Universal Hypervisor API enables deduplication and applies 1MB block size setting for all VM backups by default. These settings cannot be changed.
* Veeam Plug-in for Universal Hypervisor API supports VM backup operations with one backup job per VM at a time. If a VM is already being processed by a backup job, another backup job will not start processing this VM until the currently running backup operation completes.
* Veeam Plug-in for Universal Hypervisor API cannot run a VM backup operation for a VM that already has a restore operation running. Wait for the restore process to complete, and then start the backup job.
* Veeam Plug-in for Universal Hypervisor API does not support addition to the backup scope for VMs that are being backed up by 3rd party software. Wait for the backup process to complete or stop the currently running job manually, and then add the VM to the necessary backup job.
* By default, [backup encryption](data_encryption.md) is disabled for backed-up data. However, you can enable encryption at the repository level. For more information, see [Access Permissions](access_permissions.md).
* [VM guest OS file indexing](indexing.md) is not supported for backups created with Veeam Plug-in for Universal Hypervisor API.
* Since Veeam Backup & Replication does not allow you to assign [information about locations](locations.md) to the Universal Hypervisor Manager, job statistics do not include information on the VM data migration between different geographic regions.
* If you want to back up a VM that has been configured with a [Cloud-Init custom script](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.0/html/virtual_machine_management_guide/sect-using_cloud-init_to_automate_the_configuration_of_virtual_machines), first remove the script from the VM since it may contain secure data (such as credentials and authorized keys) that will appear in Veeam Plug-in for Universal Hypervisor API backup logs.
* [Applies only to Platform9] Veeam Plug-in for Universal Hypervisor API does not support the changed block tracking (CBT) mechanism. Full read of VM disks is always performed for backup operations.

Restore

When restoring universal hypervisor resources, consider the following:

* [Applies only to Platform9] Veeam Plug-in for Universal Hypervisor API does not support the Restore to original mode due to technical limitations of the hypervisor. However, a VM can be restored to the same location as a new VM.
* [Applies only to Platform9] Veeam Plug-in for Universal Hypervisor API always powers on a restored VM due to technical limitations of the hypervisor.

Page updated 2026-07-24

