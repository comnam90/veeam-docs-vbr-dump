---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_before_you_begin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you restore EC2 instances, consider the following limitations:

* To restore an EC2 instance from a backup that is stored in an archive backup repository, you must retrieve the archived data first. You can either retrieve the archived data manually before you begin the restore operation, or launch the data retrieval process right from the Instance Restore wizard. To learn how to retrieve data manually, see [Retrieving EC2 Data From Archive](aws_data_retrieval.md).

* If you restore multiple EC2 instances that have the same EBS volume attached, backup appliances create a separate volume for each instance and enable the Multi-Attach option for all volumes. After the restore operation completes, you can manually delete extra EBS volumes in the AWS Management Console and attach the necessary volume to the instances.

For more information on Amazon EBS Multi-Attach, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes-multi.html).

* [Applies only if you plan to restore EC2 instances to a new location or with different settings] Backup appliances restore EC2 instances with a single network interface and assign a new primary private IP address to each instance.
* [Applies only if you plan to restore EC2 instances to the original location] If [stop protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-stop-protection.html) or [termination protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html#Using_ChangingDisableAPITermination) is enabled on an EC2 instance, backup appliances will not be able to restore the instance and will raise an error notifying that you must disable stop protection or termination protection on the source instance.
* [Applies only if you plan to restore EC2 instances to the original location] Veeam Plug-in for AWS does not support restoring EC2 instances if the source instances with termination protection and stop protection enabled still exist in AWS.

* Veeam Plug-in for AWS does not support restore of IPv6 addresses, tags of Elastic IP addresses or prefixes assigned to Amazon EC2 network interfaces attached to EC2 instances.

* [Applies only if you plan to restore EC2 instances to the original location] Backup appliances restore the instance and all network interfaces that were attached to the source EC2 instance. However, keep in mind the following:

* If the Elastic IP address that was assigned to the source EC2 instance is still assigned to this EC2 instance, the address will be reassigned to the restored instance.
* If the Elastic IP address is in use by any other EC2 instance, your backup appliance will raise a warning. If you decide to proceed with the restore operation, the address will not be associated with the restored instance. Note that backup appliances will not allocate a new Elastic IP address to your AWS account.
* If the Elastic IP address that was assigned to the source EC2 instance has been removed from AWS, backup appliances will attempt to restore this address using the native [AWS capabilities](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#using-eip-recovering).
* If private IP addresses that were assigned to the source EC2 instance are in use by the source or any other EC2 instance, your backup appliance will raise a warning. If you decide to proceed with the restore operation, the restored EC2 instance will be assigned new private IP addresses.
* If the source instance still exists in AWS, backup appliances will raise a warning. If you decide to proceed with the restore operation, the source EC2 instance, including all EBS volumes and all network interfaces attached to it, will be automatically deleted from AWS.

Note that EBS volumes excluded from the backup scope and volumes for which the DeleteOnTermination attribute is set to false will also be deleted from AWS.

Page updated 2026-05-22

