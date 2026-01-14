---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_google_byb.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

Check the following considerations and limitations.

General

* Make sure that you have a backup of the workload that you plan to restore to Google Compute Engine.
* The Google Compute Engine recovery project is the project to which the [service account used for recovery](restore_google_account.md) has access. Specify this project as the target project in Google Compute Engine. This is required because Veeam Backup & Replication uses the VM Migration API to recover workloads. For more information on adding a project as a target project, see [Google Cloud documentation](https://cloud.google.com/migrate/virtual-machines/docs/5.0/get-started/target-project#add-project).
* For recovery without a helper appliance, place the gateway server associated with the backup repository where the backup is stored or the backup server into the Google Compute Engine where you plan to recover workloads.
* Verify that the backup server and repositories with workload backup files have access to the internet.

If backup files are located on deduplicating storage appliances or shared folder repositories, ensure that gateway servers communicating with these repositories have internet access.

* If you plan to assign Google labels to the restored workload, check limitations for labels in the [Google Cloud documentation](https://cloud.google.com/compute/docs/labeling-resources#restrictions).

User Account Permissions

Confirm that the IAM service account you [plan to use for restoring workloads to Google Compute Engine](restore_google_account.md) has the necessary permissions. For more information, see [Google Compute Engine IAM User Permissions](gcp_iam_permissions.md).

Source Workload Considerations

* If you restore workloads from backups of virtual or physical machines (non-Google Compute Engine virtual machines), review the supported operating systems and their differences from standard images in [Google Cloud documentation](https://cloud.google.com/compute/docs/images/os-details).

* Veeam Backup & Replication does not support recovery for BSD operating systems.

* Check that the logical sector size of the disks you plan to restore is less than 4096 bytes. Disks with a logical sector size of 4096 bytes will be unreadable in Google Compute Engine.
* [For Microsoft Windows-based backup server] Veeam Backup & Replication does not support restoring disks encrypted by BitLocker, except for backups created by Veeam Agent for Microsoft Windows. For more information, see the [Veeam Agent for Microsoft Windows User Guide](https://helpcenter.veeam.com/docs/agentforwindows/userguide/bitlocker.html?ver=13).
* If you use a cloud-init-based Linux distribution, use SSH keys for authentication. If you use a password, it is blocked after restore for security reasons. To reset the password on the restored VM, use the technologies described in [Google Cloud Documentation](https://cloud.google.com/compute/docs/connect/add-ssh-keys).

Helper Appliance

The helper appliance is an auxiliary Linux-based VM instance. It is used to upload backed-up data to Google Compute Engine. Veeam Backup & Replication automatically deploys the helper appliance in Google Compute Engine only for the duration of the restore process and removes it immediately after that.

* It is recommended to use the helper appliance when you recover from backups of Google Compute Engine virtual machines. In other cases, it is recommended to use restore without the helper appliance.

For information on how to configure the helper appliance, see [Configure Helper Appliance](restore_google_proxy_appliance.md).

* If you want to restore from backups in an on-premises object storage repository and plan to use the helper appliance, the helper appliance machine must have access to the source object storage repository. To provide access to object storage repositories, you can use VPN or Google Dedicated Interconnect. For more information, see the [Google Cloud documentation](https://cloud.google.com/network-connectivity/docs/interconnect/concepts/dedicated-overview).
* To upload one machine disk to Google Compute Engine, the helper appliance requires 1 GB RAM. Make sure that the type of Google Compute Engine instance selected for the helper appliance offers enough memory resources to upload all machine disks. Otherwise, the restore process may fail.

* The VPC route table must contain a route from the IP address of the Veeam Backup & Replication server to an active Google Cloud internet gateway. For more information on internet gateways and how to create route tables, see the [Google Cloud documentation](https://cloud.google.com/vpc/docs/routes).
* Check that OS Login is disabled for the project where you plan to recover VM instances. For more information on how to configure OS Login, see the [Google Cloud documentation](https://cloud.google.com/compute/docs/oslogin/set-up-oslogin). If you want to have OS Login enabled, use restore without the helper appliance.

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
