---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_amazon_byb.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Check the following considerations and limitations.

General

* The backup server and repositories with workload backup files must have access to the internet.

If backup files are located on deduplicating storage appliances or shared folder repositories, the internet connection is required for gateway servers that communicate with these repositories.

* [For Veeam Backup & Replication server located in Amazon EC2] If you restore workloads from a backup stored in an object storage repository, we recommend using Private IPs to increase the transfer speed. For more information, see [this Veeam KB article](https://www.veeam.com/kb4264).

User Account Permissions

Make sure that a user whose credentials you plan to use to connect to AWS has permissions to restore to Amazon EC2. For more information, see [AWS IAM User Permissions](restore_amazon_permissions.md).

Helper Appliance

The helper appliance is an auxiliary Linux-based EC2 instance. It is used to upload backed-up data to Amazon EC2. Veeam Backup & Replication automatically deploys the helper appliance in Amazon EC2 only for the duration of the restore process and removes it immediately after that.

* It is recommended to use the helper appliance when you recover from backups of EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10). In other cases, it is recommended to use restore without the helper appliance.

For information on how to configure the helper appliance, see [Configure Helper Appliance](restore_amazon_proxy.md).

* If you plan to use the helper appliance, consider the following:

* To upload one machine disk to Amazon EC2, the helper appliance requires 1 GB RAM. Make sure that the type of EC2 instance selected for the helper appliance offers enough memory resources to upload all machine disks. Otherwise, the restore process may fail.
* To recover from a backup in an on-premises object storage repository, the helper appliance machine must have access to the source object storage repository. To provide access to object storage repository, you can use VPN or AWS Direct Connect.
* To restore from a backup in an Amazon S3 object storage, use the helper appliance that has the instance type with the maximum values for the Network Bandwidth (Gbps) and EBS Bandwidth (Mbps). In most cases, you can use c5.18xlarge. For more information on instance types, see [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/).

* A subnet and security group that you select for the helper appliance must meet the following requirements:

* Auto-assignment of public IPv4 addresses must be enabled in the subnet. For more information on how to enable this option, see the [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-ip-addressing.html#subnet-public-ip).
* The subnet route table must contain a default route to an active AWS internet gateway. For more information on internet gateways and how to create route tables, see the [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html).
* The subnet must have no network access control lists (ACLs) or a network ACL that allows inbound and outbound traffic on the ports listed in section [Ports](used_ports.md#restore_to_amazon).
* The security group must allow inbound and outbound traffic on the ports listed in section [Ports](used_ports.md#restore_to_amazon).

Source Workload Considerations

* You must have a backup of the workload that you plan to restore to Amazon EC2.

* If you use a cloud-init-based Linux distribution, we recommend that you use SSH keys on these distributions. If you use a password, it is blocked after restore for security reasons. To reset the password on the restored instance, use the technologies described in [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-ec2reset.html).

* Veeam Backup & Replication does not support recovery for BSD operating systems.

* If you plan to restore a Linux- or Unix-based workload, check that Amazon EC2 supports the kernel version. If the version is not supported, consider changing the kernel version before backing up. For more information on kernel versions, see [AWS Documentation](https://docs.aws.amazon.com/vm-import/latest/userguide/prerequisites.html#vmimport-operating-systems-linux).
* If you plan to restore workloads other than EC2 instances, check the supported OS, EC2 instance and file system types in the [AWS Documentation](https://docs.aws.amazon.com/vm-import/latest/userguide/vmie_prereqs.html).

* Check that the logical sector size of disks that you plan to restore equals 512 bytes. Contents of disks whose sector size is 4096 bytes will be unreadable in Amazon EC2.
* [For restore of EC2 instances without helper appliance] If you restore workloads with more than five disks, check that the Limit maximum concurrent tasks option of the repository where the backups are stored is equal or less than the limit of the AWS ImportVolume service for concurrent tasks. Veeam Backup & Replication uses this service during the restore. For more information on the limit, see [AWS Documentation](https://docs.aws.amazon.com/general/latest/gr/ec2-service.html#limits_ec2).

* [For Microsoft Windows-based backup server] Veeam Backup & Replication does not support restoring disks encrypted by BitLocker, except for restoring from backups created by Veeam Agent for Microsoft Windows. For more information, see the [Veeam Agent for Microsoft Windows User Guide](https://helpcenter.veeam.com/docs/agentforwindows/userguide/bitlocker.html?ver=13).
* You cannot restore EC2 instances with encrypted EBS volumes using a helper appliance. To restore such instances, [disable the use of the helper appliance](restore_amazon_proxy.md). If your backups are stored on an object storage repository, you can disable the appliance in the configuration file on the Linux-based backup server or with registry values on the Microsoft Windows-based backup server. For more information, contact Veeam Customer Support.

AWS-Specific Considerations

* Veeam Backup & Replication uses AWS VM Import/Export during restore. It is recommended to check limitations in the [AWS Documentation](https://docs.aws.amazon.com/vm-import/latest/userguide/vmie_prereqs.html).
* If you plan to assign AWS tags to the restored EC2 instance, check limitations for tags in the [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/Using_Tags.html).


