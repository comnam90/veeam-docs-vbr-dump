---
title: "Step 2. Create Virtual Private Target Gateway"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_target_gateway.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 2. Create Virtual Private Target Gateway


To establish a VPN connection between the VPC of the backup appliance and your on-premises network, create a virtual private target gateway on the AWS side and attach the gateway to the VPC:

1. In the Amazon VPC console, navigate to
   Virtual Private Network
    >
   Virtual Private Gateways
    and click
   Create Virtual Private Gateway
   .
2. Complete the
   Create virtual private gateway
    wizard:

1. At the
   Details
    step, do the following:

1. [Optional] In the
   Name tag
    field, specify a name for the virtual private target gateway.
2. In the
   Autonomous System Number (ASN)
    section, choose whether you want to keep the default ASN or specify a custom one. This ASN must not match the BGP ASN that you have specified for the customer gateway at
   [step 1](aws_create_customer_device.md)
   .

For custom ASNs, the following limitations apply. For a 16-bit ASN, its value must be between 64512 and 65534; for a 32-bit ASN, its value must be between 4200000000 and 4294967294.

Note that after you create the VPN connection, you will not be able to change the ASN for it.

1. Click
   Create virtual private gateway
   .

1. To attach the created virtual private gateway to the VPC, select the gateway in the
   Virtual private gateways
    list and click
   Actions
    >
   Attach to VPC
   .
2. Complete the
   Attach to VPC
    wizard:

1. At the
   Details
    step, select the VPC from the list of available VPCs.
2. Click
   Attach to VPC
   .

Page updated 2025-10-10

