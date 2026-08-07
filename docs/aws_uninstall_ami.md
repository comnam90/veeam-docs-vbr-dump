---
title: "Deleting AWS Resources"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_uninstall_ami.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deleting AWS Resources


When you deploy a backup appliance from the Amazon Machine Image (AMI), it creates a number of resources in AWS, and these resources are not automatically removed from your infrastructure when you delete the EC2 instance where the backup appliance is deployed. To uninstall the backup appliance entirely, you must locate and delete the following resources from your infrastructure:

* AWS::IAM::InstanceProfile
* AWS::DLM::LifecyclePolicy
* AWS::CloudWatch::Alarm
* AWS::EC2::SecurityGroup
* AWS::IAM::Role
* AWS::EC2::Instance

To delete a resource, do the following:

1. Log in to the AWS Management Console using credentials of an AWS account where the backup appliance is deployed.
2. Use the region selector in the upper-right corner of the page to select the AWS Region in which the backup appliance resides.
3. Navigate to AWS service to which the AWS resource belong.
4. Select the AWS resource that you want to remove, and click Delete.

Page updated 2026-05-20

