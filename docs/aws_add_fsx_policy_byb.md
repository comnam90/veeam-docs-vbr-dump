---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_fsx_policy_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you protect FSx file systems, consider the following:

* Veeam Plug-in for AWS supports backup of only those FSx file system properties that are described in section [Protecting FSx File Systems](aws_overview_fsx.md#parameters).

* Veeam Plug-in for AWS supports creating cloud-native backups for FSx file systems only to the same AWS accounts to which the source file systems belong.
* For backup appliances to be able to create cloud-native backups for FSx file systems, you must enable the Opt-in service for the FSx resource type in the AWS Backup settings. Otherwise, the backup appliance will automatically enable the service for each AWS Region specified in the backup policy settings in your AWS account while performing backup operations.

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for NetApp ONTAP file systems. However, you can back up Amazon FSx for NetApp ONTAP file systems using the Veeam Backup & Replication console. For more information, see [Unstructured Data Backup](unstructured_data_backup.md).
* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Windows File Server file systems that use AWS Secrets Manager to store service account credentials when joined to a self-managed Microsoft Active Directory (AD).

* Veeam Plug-in for AWS does not support storing cloud-native backups in [logically air-gapped vaults](https://docs.aws.amazon.com/aws-backup/latest/devguide/logicallyairgappedvault.html) and in backup vaults with the [AWS Backup Vault Lock](https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html) feature enabled.

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Lustre file systems with the [Scratch deployment type](https://docs.aws.amazon.com/fsx/latest/LustreGuide/using-fsx-lustre.html?icmpid=docs_fsx_console#scratch-file-system).

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for Lustre with the [data repository association](https://docs.aws.amazon.com/fsx/latest/LustreGuide/fsx-data-repositories.html).

* Veeam Plug-in for AWS does not support creating cloud-native backups for Amazon FSx for OpenZFS with the [Intelligent-Tiering storage class](https://docs.aws.amazon.com/fsx/latest/OpenZFSGuide/performance-intelligent-tiering.html).

* Backup appliances use the [AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html) service to create FSx backups and backup copies. The AWS Backup service does not support creating backup copies of FSx backups stored in [Opt-in Regions](https://docs.aws.amazon.com/controltower/latest/userguide/opt-in-region-considerations.html).

* Backup appliances run retention sessions at 4:00 AM by default, according to the time zone set on each appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

Page updated 2026-05-21

