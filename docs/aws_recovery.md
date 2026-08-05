---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_recovery.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


In various disaster recovery scenarios, you can perform the following restore operations using backed-up data:

* [Restore of EC2 instances](aws_ec2_restore.md) — restore EC2 instances, volumes and files from from cloud-native snapshots, snapshot replicas or image-level backups to the original location or to a new location.
* [Restore of RDS resources](aws_rds_restore.md) — restore DB instances and Aurora DB clusters (from cloud-native snapshots, snapshot replicas) and DB instance databases (from image-level backups) to the original location or to a new location.
* [Restore of DynamoDB tables](aws_dynamo_restore.md) — restore DynamoDB tables from backups to the original location or to a new location.
* [Restore of Redshift clusters](aws_redshift_restore.md) — restore Redshift clusters from backups to their original location.
* [Restore of Redshift Serverless namespaces](aws_redshift_serverless_restore.md) — restore Redshift Serverless namespaces from cloud-native backups to the original, any existing or a new namespace.
* [Restore of EFS file systems](aws_efs_restore_ui.md) — restore file systems from backups to the original location or to a new location.
* [Restore of FSx file systems](aws_fsx_restore.md) — restore file systems from backups to the original location or to a new location.
* [Restore of VPC configurations](aws_vpc_restore_ui.md) — restore VPC configurations from VPC configuration backups to the original location or to a new location.

* [Instant Recovery](aws_instant_recovery.md) — immediately restore EC2 instances from image-level backups to VMware vSphere and Hyper-V environments, and to Nutanix AHV clusters.
* [EC2 instance disk export](aws_export_disks.md) — restore volume disks and convert them to disks to the VMDK, VHD or VHDX format.
* [EC2 instance disk publish](aws_publishing_disks.md) — publish point-in-time volume disks, and copy the necessary files and folders to the target server.
* [Restore to Microsoft Azure](aws_restore_to_azure.md) — restore EC2 instances from image-level backups to Microsoft Azure as Azure VMs.
* [Restore to Google Cloud](aws_restore_to_google.md) — restore EC2 instances from image-level backups to Google Cloud as VM instances.
* [Restore to Nutanix AHV](aws_restore_to_nutanix.md) — restore EC2 instances from image-level backups to Nutanix AHV as Nutanix AHV VMs.

Page updated 2026-07-09

