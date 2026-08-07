---
title: "Step 2. Create VPC Peering Connection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_vpc_peering_connection.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 2. Create VPC Peering Connection


If you have created interface endpoints and S3 interface endpoints in subnets of two different VPCs, you must create a peering connection between the accepter and requester VPC to enable route traffic between those VPCs using private IP addresses.

To create a VPC peering connection, do the following:

1. In the Amazon VPC console, navigate to
   Virtual Private Cloud
    >
   Peering connections
    and click
   Create peering connection
   .
2. Complete the
   Create peering connection
    wizard:

1. At the
   Peering connection settings
    step, do the following:

1. [Optional] In the
   Name
    field, specify a name for the connection.
2. In the
   Select a local VPC to peer with
    section, choose the requester VPC.
3. In the
   Select another VPC to peer with
    section, choose an AWS account and AWS Region in which you want to create the connection, and specify the ID of the accepter VPC.
4. In the
   Tags
    section, specify AWS tags that will be assigned to the connection.

1. Click
   Create Peering Connection
   .

1. To enable route traffic between the requester and accepter VPC, select the created peering connection in the
   Peering connections
    list and click
   Actions
    >
   Accept request
   .

Page updated 2025-10-10

