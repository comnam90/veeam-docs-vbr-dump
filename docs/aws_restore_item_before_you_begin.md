---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_item_before_you_begin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you start file-level recovery, consider the following limitations and prerequisites:

* Restore of files and folders is supported for FAT, FAT32, NTFS, ext2, ext3, ext4, XFS, Btrfs file systems only. For EC2 instances running Microsoft Windows OSes, Veeam Plug-in for AWS supports file-level recovery for basic volumes only.

* Veeam Plug-in for AWS does not support restore of files or folders stored on EBS volumes with Windows-native [Data Deduplication](https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/overview) enabled. To work around the issue, you can restore entire volumes, and then attach these volumes to an EC2 Windows instance with the deduplication feature enabled. To learn how to restore entire EBS volumes, see [Performing Volume Restore](aws_restore_volume_perform.md).
* To recover files and folders of an EC2 instance from an image-level backup that is stored in an archive backup repository, you must retrieve the archived data manually before you begin the file-level recovery operation. For more information on data retrieval, see [Retrieving EC2 Data From Archive](aws_data_retrieval.md).

* The 443 port must be open on worker instances to allow inbound network access from the machine from which you plan to open the file-level recovery browser. To enable access for a worker instance, update the security group specified in [worker instance settings](aws_worker_settings.md) to add an inbound rule. To learn how to add rules to security groups, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html#adding-security-group-rules).

If you want worker instances to operate in a private network, enable the [private network deployment](aws_enable_private_network_deployment.md) functionality and configure specific VPC endpoints for all subnets to which the worker instances will be connected. Alternatively, configure VPC endpoints for all subnets as described in section [Appendix C. Configuring Endpoints in AWS](aws_configure_endpoints.md).

* [Applies only if you plan to open the file-level recovery browser in AWS China Regions] Inbound access on port 443 is available only for AWS accounts with an ICP (Internet Content Provider) license. If your AWS accounts do not have an ICP license, configure a custom port as described in section [Configuring Custom Port for File-Level Recovery Browser in AWS China Regions](#custom_port).

|  |
| --- |
| Tip |
| It is recommended that you run a file-level recovery test before you start a file-level recovery operation in a specific AWS Region. For more information, see [Testing Configurations for FLR](aws_worker_settings_test.md). |

Restoring to Original Location

If you plan to perform file-level recovery to the original location, consider the following additional limitations and prerequisites:

* To perform restore to the original location, backup appliances deploy worker instances in the [backup account](aws_worker_options.md#backup) and in the AWS Region where a backup repository with backed-up data resides. That is why you must specify network settings for worker instances beforehand as described in section [Adding Configurations for Backup Account](aws_worker_add_config_backup.md).
* [For EC2 instances running Linux OS] Restore of files and folders is supported only for systemd-based distributions.
* [For EC2 instances running Windows OS] Restore of files and folders is supported only if Windows Management Framework (WMF) version 5.1 is installed on the processed instances.

* [For Linux-based EC2 instances] Python v2 or v3 with module 6 must be installed on the source instance.
* The source instance must be configured to communicate with AWS System Manager. To learn how to configure instance permissions for Systems Manager, see [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-instance-permissions.html).
* SSM Agent must be installed on the source instance. To learn how to install SSM Agent, see [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent.html).

* The IAM role attached to the source EC2 instance must meet the following requirements:

1. The IAM role must be included in the instance profile. For more information on instance profiles, see [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html).
2. The Amazon EC2 service must be granted permissions to assume the IAM role.

To allow the Amazon EC2 service to assume the IAM role, configure trust relationships for the role and add the following statement to the trust policy.

|  |
| --- |
| {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": "sts:AssumeRole",       "Principal": {         "Service": "ec2.amazonaws.com"       }     }   ]  } |

1. During the file-level recovery session, backup appliances will create a temporary IAM role in the backup account to perform data transmission using [Amazon Kinesis Data Streams](https://docs.aws.amazon.com/streams/latest/dev/introduction.html). That is why the IAM role attached to the source EC2 instance must have the permissions to assume the temporary role:

|  |
| --- |
| {     "Version": "2012-10-17",     "Statement": [         {             "Sid": "VisualEditor1",             "Effect": "Allow",             "Action": "sts:AssumeRole",             "Resource": "arn:aws:iam::<backup-account-id>:role/veeam\_rto\_<original-instance-id>"         }     ]  } |

Where the <service-account-id> is an AWS ID of the trusted [backup account](aws_worker_options.md#backup), and <original-instance-id> is an AWS ID of the source EC2 instance.

* If the source EC2 instance operates in a private network, you must create the following VPC endpoints for the subnet to which the instance is connected:

* com.amazonaws.<region>.ec2messages
* com.amazonaws.<region>.ssm
* com.amazonaws.<region>.sqs
* com.amazonaws.<region>.kinesis-streams
* com.amazonaws.<region>.sts

To learn how to create interface VPC endpoints, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html).

|  |
| --- |
| Tip |
| It is recommended that you run a file-level recovery test before you start a file-level recovery operation in a specific AWS Region. For more information, see [Testing Configurations for FLR](aws_worker_settings_test.md). |

Configuring Custom Port for File-Level Recovery Browser in AWS China Regions

By default, worker instances use port 443 to open the file-level recovery browser. In AWS Global and AWS GovCloud (US) Regions, this port is open for any AWS account. In AWS China Regions, inbound access on port 443 is available only for AWS accounts with an ICP (Internet Content Provider) license. If the source data that you plan to restore resides in AWS China Regions and your AWS accounts do not have an ICP license, you can configure a custom port that will be used to open the file-level recovery browser.

To configure a custom port, do the following:

1. To connect to the EC2 instance where the backup appliance is deployed, run the following command in a terminal window:

|  |
| --- |
| ssh -i <path/to/EC2\_instance.pem> ubuntu@<Public DNS hostname or IPv4 address of the EC2 instance> |

1. To create a directory for the Veeam FLR service configuration, run the following command:

|  |
| --- |
| sudo mkdir -p /etc/systemd/system/veeamflr.service.d |

1. To allow worker instances to use a custom port, do the following:

1. To create a configuration file, run the following command:

|  |
| --- |
| sudo nano /etc/systemd/system/veeamflr.service.d/10-worker-port.conf |

1. In the configuration file, add the following lines, where <port> is the custom port number:

|  |
| --- |
| [Service]  Environment=WORKER\_LISTENING\_PORT=<port> |

1. Save the changes and close the configuration file.

1. To reload the systemd configuration, run the following command:

|  |
| --- |
| sudo systemctl daemon-reload |

1. To restart the Veeam FLR service and apply the changes, run the following command:

|  |
| --- |
| sudo systemctl restart veeamflr.service |

1. To verify that the custom port setting is applied, run the following command:

|  |
| --- |
| systemctl show veeamflr.service -p Environment |

|  |
| --- |
| Important |
| After you specify the port, you must also update the security group specified in [worker instance settings](aws_worker_settings.md) to allow inbound traffic on the new port. To learn how to add rules to security groups, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html#adding-security-group-rules). |

Page updated 2026-07-22

