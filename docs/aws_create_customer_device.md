---
title: "Step 1. Create Customer Gateway"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_customer_device.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 1. Create Customer Gateway


A customer gateway device is a physical device or software application in your on-premises network. A customer gateway is a resource in AWS representing the customer gateway device in the on-premises network. For more information, see
[AWS Documentation](https://docs.aws.amazon.com/vpn/latest/s2svpn/how_it_works.html#CustomerGatewayDevice)
.

To provide information on a customer gateway device to AWS, create a customer gateway:

1. Log in to the AWS Management Console using credentials of an AWS account in which you want to create the Site-to-Site VPN connection.
2. Navigate to
   All Services
    >
   Networking
    &
   Content Delivery
    and click
   VPC
   .
3. In the Amazon VPC console, navigate to
   Virtual Private Network
    >
   Customer Gateways
    and click
   Create Customer Gateway
   .
4. Complete the
   Create customer gateway
    wizard:

1. At the
   Details
    step of the wizard, do the following:

1. [Optional] In the
   Name tag
    field, specify a name for the gateway.
2. In the
   BGP ASN
    field, specify a Border Gateway Protocol (BGP) Autonomous System Number (ASN) for the gateway.
3. In the
   IP address
    field, specify a static, internet-routable IP address for the gateway.
4. From the
   Certificate ARN
    drop-down list, specify the Amazon Resource Name of a private certificate that will be used to connect to the gateway.
5. [Optional] In the
   Device
    field, specify a name for the customer gateway device.

1. Click
   Create customer gateway
   .

Page updated 2026-03-31

