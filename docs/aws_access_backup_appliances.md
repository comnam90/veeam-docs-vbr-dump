---
title: "Configuring Access to Backup Appliances in AWS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_access_backup_appliances.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Access to Backup Appliances in AWS


|  |
| --- |
| Note |
| This section provides instructions on steps performed in a third-party application as part of one possible solution. Keep in mind that the instructions may become outdated. For up-to-date instructions, see [AWS Documentation](https://docs.aws.amazon.com/vpn/latest/s2svpn/SetUpVPNConnections.html). |

To allow a Veeam Backup & Replication server to communicate with a backup appliance operating in a [private environment](aws_appliance_in_private.md), you can establish an AWS Site-to-Site VPN (Site-to-Site VPN) connection between the VPC of the appliance and your on-premises network:

1. [Create a customer gateway](aws_create_customer_device.md).
2. [Create a virtual private target gateway and attach the gateway to the VPC](aws_create_target_gateway.md).
3. [Enable route propagation](aws_configure_routing_vpn.md).
4. [Allow inbound traffic to the backup appliance](aws_update_security_group.md).
5. [Create a VPN connection](aws_create_vpn_connection.md).

Page updated 2026-05-19

