---
title: "Step 5. Create VPN Connection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_create_vpn_connection.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Create VPN Connection


To enable access to your on-premises network, create a VPN connection between the created virtual private gateway and the customer gateway:

1. In the Amazon VPC console, navigate to Virtual private network > Site-to-Site VPN Connections and click Create VPN Connection.
2. Complete the Create VPN connection wizard:

1. At the Details step of the wizard, do the following:

1. [Optional] In the Name tag field, specify a name for the VPN connection.
2. In the Autonomous System Number (ASN) section, select the Virtual private gateway option and specify the ID of the virtual private gateway that you have created at [step 2](aws_create_target_gateway.md).
3. In the Customer gateway section, select the Existing option and specify the ID of the customer gateway.
4. [Applies only if the customer device does not support Border Gateway Protocol] In the Routing options section, select the Static option and specify the IP prefixes of the appliance VPC.

1. Click Create VPN connection.

|  |
| --- |
| Tip |
| When you create a VPN connection, AWS generates a sample configuration file that can be further used to configure a customer gateway device. To download the file, do the following:   1. In the Amazon VPC console, navigate to Virtual Private Network > Site-to-Site VPN Connections. 2. From the VPN connections drop-down list, select the created connection and click Download configuration.  1. In the Download configuration window, select the vendor, class and operating system of the customer gateway device, and the IKE version that is used for the VPN connection. Then, click Download.   To learn how to configure a customer gateway device, see [AWS Documentation](https://docs.aws.amazon.com/vpn/latest/s2svpn/your-cgw.html). |

Page updated 2026-05-19

