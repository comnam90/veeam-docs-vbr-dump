---
title: "Appendix D. Enabling Swap Partition"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_enable_swap_partition.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix D. Enabling Swap Partition


|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application. Keep in mind that the instructions may become outdated. For up-to-date instructions, see AWS Documentation. |

By enabling a swap partition on the EC2 instance where the backup appliance is installed, you can prevent runtime issues on the backup appliance. The swap partition allows the system to allocate additional resources when the backup appliance runs out of physically allocated memory due to overload caused by multiple concurrent operations.

To enable the swap partition on the backup appliance, you must first create and attach an additional EBS volume to the EC2 instance where the backup appliance is deployed, and then perform a number of configuration actions on the instance.

|  |
| --- |
| Note |
| When you deploy a backup appliance on the EC2 instance of the C5d instance type, a number of [instance store volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-store-volumes.html) is automatically attached to the instance, and the store volumes are partitioned with swap spaces, one of which equals to the amount of RAM allocated to the instance. However, if instance store volumes have already been manually configured before the product installation, the swap space formatting will not be created automatically, and you will have to create it manually as described in [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-store-swap-volumes.html). |

Creating and Attaching EBS Volume in AWS

To create a new EBS volume and attach it to the backup appliance, do the following:

1. Log in to the AWS Management Consoleusing credentials of an AWS account where the backup appliance resides.
2. Navigate to All Services > Compute and click EC2.
3. In the Amazon EC2 console, navigate to Volumes and click Create Volume.
4. Complete the Create volume wizard:

1. At the Volume settings section of the wizard, do the following:

1. From the Volume type drop-down list, select General Purpose SSD (gp3). For more information on EBS volume types, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html).
2. In the Size (GB) field, specify the size of the volume. For swap partition purposes, it is recommended that you create an EBS volume with a minimum size equal to the memory size of the EC2 instance.

For more information on EC2 instance memory sizes, see [AWS Documentation](https://aws.amazon.com/ec2/instance-types/?trk=b59ef3d1-61fa-4eea-9a0b-96fbd6584e69&sc_channel=ps&ef_id=EAIaIQobChMIqOSTr_Hb_gIVIkeRBR1bTQ_TEAAYASABEgKIJ_D_BwE:G:s&s_kwcid=AL!4422!3!645133569741!p!!g!!ec2%20instance!19579892353!148838337521).

1. In the IOPS field, specify the maximum number of input/output operations per second that the volume must provide. For swap partition purposes, 4000 IOPS is recommended.
2. In the Throughput field, specify the throughput that the volume must provide. It is recommended that you specify the maximum throughput available for the selected volume size.
3. From the Availability Zone drop-down list, select the availability zone in which the backup appliance resides.
4. From the Snapshot ID drop-down list, select the Don't create volume from a snapshot option.
5. If you want to encrypt the EBS volume, select the Encrypt the volume check box. You can either select a [default KMS key](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html#EBSEncryption_key_mgmt) from the KMS key drop-down list, which is automatically created by Amazon EBS in the specified AWS Region, or specify the amazon resource number (ARN) of the key in the Specify a custom KMS key window.

|  |
| --- |
| Important |
| If you choose to encrypt the EBS volume, make sure that the EC2 instance type of the backup appliance supports Amazon EBS encryption. For more information, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html). |

For more information on KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html).

1. At the Tags section of the wizard, you can specify AWS tags that will be assigned to the volume.
2. Click Create volume.

1. To attach the created EBS volume to the EC2 instance, select the volume from the Volumes list and click Actions > Attach volume.
2. Complete the Attach volume wizard:

1. From the Instance drop-down list, select the EC2 instance where the backup appliance is deployed.

|  |
| --- |
| Note |
| The backup appliance and the EBS volume that you want to attach must reside in the same availability zone. |

1. In the Device name field, specify a name for the volume that will be used by Amazon EC2. Note that the name must conform the available device name rules, and it will be changed later by the block device driver when mounting the volume. For more information, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/device_naming.html).
2. Click Attach volume.

Configuring Swap Partition on EC2 Instance

After you have attached the created volume to the backup appliance, you must perform a number of configuration actions to enable a swap partition:

1. Connect to the EC2 instance where the backup appliance is installed. To do that, run the following ssh command in a terminal window:

|  |
| --- |
| ssh -i /path/EC2\_instance.pem key ubuntu@<Public DNS hostname or IPv4 address of the EC2 instance> |

1. To get a list of available volumes, run the following command:

|  |
| --- |
| sudo lsblk |

You can identify the newly added volume by the absence by the mount point. Save the volume name for future reference.

1. To create a swap file system on the new volume, run the following command:

|  |
| --- |
| sudo mkswap /dev/<volume\_name> -L "vbaws\_swap" |

1. To add the newly created file system to the /etc/fstab file, do the following:

1. Open the file:

|  |
| --- |
| sudo nano /etc/fstab.conf |

1. Add the following file system label:

|  |
| --- |
| LABEL=vbaws\_swap swap swap defaults,nofail 0 0 |

1. Save the changes.

1. To enable the swap partition, run the following command:

|  |
| --- |
| sudo swapon –all |

1. To confirm that the swap partition is enabled, run the following command:

|  |
| --- |
| sudo swapon |

1. To allow the backup appliance to use swap space preference, do the following:

1. Open the file:

|  |
| --- |
| sudo nano /etc/sysctl.d/99-sysctl.conf |

1. Add the following variable to the file and set its value to 1:

|  |
| --- |
| vm.swappiness = 1 |

1. Save the changes.

1. Reload the /etc/sysctl.d/99-sysctl.conf file to apply the changes without rebooting EC2 instance:

|  |
| --- |
| sudo sysctl -p /etc/sysctl.d/99-sysctl.conf |

Page updated 2026-05-22

