---
title: "Step 5. Create Security Groups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_seciruty_groups_workers.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 5. Create Security Groups


Security groups associated with shared subnets are not automatically propagated to other AWS accounts during resource sharing. That is why if you have created a single resource share in one AWS account for all subnets to which worker instances will be connected, you must create security groups in each production account — these groups will be associated with worker instances connected to the shared subnets.

To create a security group, do the following:

1. Log in to the
   AWS Management Console
    using credentials of an AWS account in which you want to create the security group.
2. Navigate to
    Services
    >
   Networking
    &
   Content Delivery
    and click
   VPC
   .
3. In the
   VPC
    console, navigate to
   Security
    >
   Security Groups
    and click
   Create security group
   .
4. Complete the
   Create security group
    wizard:

1. At the
   Basic details
    step, do the following:

1. In the
   Security group name
    and
   Description
    field, specify a name and description for the security group.
2. In the
   VPC
    field, specify the ID of the VPC in which you want to create the security group.

To obtain the ID, you can look it up on the
Your VPCs
 page in the VPC console.

1. At the
   Inbound rules
    step, do not specify any inbound rules.
2. At the
   Outbound rules
    step, specify rules to allow outbound HTTPS trafficto all VPC endpoints used by worker instances that will be connected to the shared subnets through port
   443
   .
3. At the
   Tags
    step, specify AWS tags that will be assigned to the security group.
4. Click
   Create security group
   .

|  |
| --- |
| Important |
| After you create a security group, you must either add a new worker configuration or edit the network settings of an existing one to specify the created security group for each production account in which worker instances will be deployed. To learn how to do that, see  [Adding Configurations for Production Accounts](aws_worker_add_config_prod.md#region) . |

Page updated 2025-04-25

