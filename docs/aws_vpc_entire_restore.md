---
title: "Performing Entire Configuration Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_vpc_entire_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Entire Configuration Restore


In case of unexpected configuration changes, you can restore entire Amazon VPC configuration from a VPC configuration backup. Veeam Plug-in for AWS allows you to restore the VPC configuration to the original location or to a new location.

|  |
| --- |
| Important |
| Restore to a new location is not supported for the following VPC configuration items:   * Client VPN endpoints. * Customer gateways and load balancer listeners that use authentication certificates. |

To restore the entire VPC configuration, do the following:

1. [Launch the VPC Restore wizard](aws_restore_entire_vpc_launch.md).
2. [Select a restore point and VPCs to restore](aws_restore_entire_vpc_point.md).
3. [Specify account settings for restore](aws_restore_entire_vpc_account.md).
4. [Choose a restore mode](aws_restore_entire_vpc_mode.md).
5. [Configure mapping for Availability Zones](aws_restore_entire_vpc_zone_mapping.md).
6. [Review settings of VPC peering connections](aws_restore_entire_vpc_connection.md).
7. [Specify a restore reason](aws_restore_entire_vpc_reason.md).
8. [Finish working with the wizard](aws_restore_entire_vpc_finish.md).

Page updated 2026-05-22

