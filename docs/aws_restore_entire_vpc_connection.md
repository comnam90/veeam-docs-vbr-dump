---
title: "Step 6. Review Peering Connection Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_vpc_connection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Review Peering Connection Settings


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Peering Connection step of the wizard, review preconfigured VPC peering connection settings. You cannot modify the settings for the restored VPC configuration — by default, the backup appliance will restore VPC peering connections as follows:

* If you restore both VPCs between which you have created a peering connection, the backup appliance will create a peering connection between the restored VPCs in the target AWS Region.
* If you restore a VPC that has a peering connection to a VPC in the same AWS Region, the backup appliance will create an inter-region peering connection between the restored VPC in the target AWS Region and the VPC with which the source VPC is peered in the source AWS Region.
* If you restore a VPC that has a peering connection to a VPC in another AWS Region, the backup appliance will create an inter-region peering connection between the restored VPC in the target AWS Region and the VPC with which the source VPC is peered in the other AWS Region.

|  |
| --- |
| Note |
| VPC peering connections will have the Pending Acceptance status after restoring. To accept the restored VPC peering connections, use the AWS Management Console. For more information, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/peering/create-vpc-peering-connection.html). |

[![Restoring VPC Configuration](images/aws_vpc_restore_entire_connection2.webp)](images/aws_vpc_restore_entire_connection2.webp "Restoring VPC Configuration")

Page updated 2026-05-22

