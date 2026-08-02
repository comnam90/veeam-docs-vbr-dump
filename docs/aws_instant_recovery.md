---
title: "Instant Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_instant_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Instant Recovery


Veeam Backup & Replication allows you to use the Instant Recovery feature to restore EC2 instances from image-level backups to VMware vSphere and Microsoft Hyper-V environments, and to Nutanix AHV clusters. For more information, see section [Instant Recovery to VMware vSphere](instant_recovery.md) in this guide and [Veeam Backup for Nutanix AHV User Guide](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery_ahv.html?ver=8), section Instant Recovery.

|  |
| --- |
| Important |
| Instant Recovery can be performed only using either of the following backups:   * Backup files stored in standard backup repositories for which you have specified access keys of an IAM user whose permissions are used to access the repositories. To learn how to specify credentials for the repositories, see sections [Creating New Repositories](aws_add_s3_account.md) and [Connecting to Existing Appliances](aws_connect_appliance_repo.md). * Backup files stored in storage vaults for which you have registered the backup server in Veeam Data Cloud and assigned the storage vault to this backup server. To learn how to register a backup server in Veeam Data Cloud Vault and assign storage vaults, see sections [Adding Storage Vaults Using Console](aws_add_vault_account.md) and [Connecting to Existing Appliances](aws_connect_appliance_repo.md). |

Before you start the restore operation, make sure to add to the backup infrastructure a vCenter Server, a Microsoft Hyper-V server or a Nutanix AHV cluster that will manage restored EC2 instances, as described in section [Adding VMware vSphere Servers](add_vmware_server.md), [Adding Microsoft Hyper-V Servers](add_hyperv_server.md) or [Adding Nutanix AHV Cluster](https://helpcenter.veeam.com/docs/vbahv/userguide/add_ahv_cluster.html?ver=50).

To perform Instant Recovery, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > External Repository.
3. Expand the backup policy that protects an EC2 instance that you want to recover, select the necessary EC2 instance and click Instant Recovery on the ribbon.
4. Select VMware vSphere, Microsoft Hyper-V or Nutanix AHV.

1. Depending on the selected Instant Recovery option, complete the Instant Recovery wizard as described in section [Performing Instant Recovery of Workloads to VMware vSphere VMs](instant_recovery_vms_vm.md), [Performing Instant Recovery of Workloads to Hyper-V VMs](ir_workloads_hv.md) or [Performing Instant Recovery of Workloads to Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/ir_workloads_ahv.html?ver=8).

[![Instant Recovery to VMware vSphere, vSphere or to Nutanix AHV](images/aws_instant_recovery.webp)](images/aws_instant_recovery.webp "Instant Recovery to VMware vSphere, vSphere or to Nutanix AHV")

Page updated 2026-06-25

