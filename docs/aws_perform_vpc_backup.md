---
title: "Performing VPC Configuration Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_perform_vpc_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing VPC Configuration Backup


To protect the Amazon VPC configuration and settings, the backup appliance comes with a preconfigured VPC Configuration Backup policy. With this policy, you can protect VPC configurations of AWS Regions in your AWS accounts or AWS Organizations.

The VPC Configuration Backup policy is disabled by default. To start protecting your Amazon VPC configuration, [edit backup policy settings](aws_policies_edit_vpc.md) and [enable the policy](aws_policies_disable_enable_vpc.md).

|  |
| --- |
| Important |
| Veeam Plug-in for AWS does not support backup of the following VPC configuration components: VPC Traffic Mirroring, AWS Network Firewall, Route 53 Resolver DNS Firewall, AWS Verified Access, VPC Flow Logs, carrier gateways, customer IP pools, transit gateway policy tables, or core networks in route tables. |

In This Section

* [Editing VPC Backup Policy](aws_policies_edit_vpc.md)
* [Enabling and Disabling VPC Configuration Backup Policy](aws_policies_disable_enable_vpc.md)
* [Starting and Stopping VPC Configuration Backup Policy](aws_policies_start_stop_vpc.md)

Page updated 2026-05-21

