---
title: "Configuring Network Traffic Rules"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/network_rules.html"
last_updated: "2/25/2025"
product_version: "13.0.1.1071"
---

# Configuring Network Traffic Rules


Network traffic rules control traffic transferred between backup infrastructure components. These rules allow you to do the following:

* Throttle network traffic
* Encrypt transferred data

The rules apply only to traffic sent between the backup infrastructure components, so you do not have to change your network infrastructure.

How Network Rules Work

Each network rule contains IP address ranges for source and target components. When a job starts, Veeam Backup & Replication checks the rules against the components involved in the job. If the IP addresses of the components fall into the IP address ranges of a rule, the rule applies.

For example, 192.168.0.1–192.168.0.255 is the source range, and 172.16.0.1–172.16.0.255 is the target range. 192.168.0.12 is the IP address of one component, and 172.16.0.31 is the IP address of another component. Both IP addresses fall into the ranges, so the rule will apply.

Note that the rules are reversible. The rule from the example will also apply to the specified components if you swap the ranges: make 192.168.0.1–192.168.0.255 the target range and 172.16.0.1–172.16.0.255 the source range.

|  |
| --- |
| Note |
| If the configured network rule covers at least one of the connection interfaces to a Veeam agent, Veeam Backup & Replication applies network traffic throttling even if the traffic is transferred to/from this Veeam agent through another interface. |

|  |
| --- |
| Tip |
| You can define a rule for specific components. For this, specify a single IP address in the source range and in the target range. |

Creating Network Rules

You must create network rules at the backup server level. For details, see [Enabling Traffic Throttling](setting_network_traffic_throttling.md) and [Enabling Traffic Encryption](enable_network_encryption.md). Veeam Backup & Replication also has a predefined rule for traffic transferred between public networks. For more information, see [Adjusting Internet Rule](internet_rule.md).

After you create or edit network rules, they are applied almost immediately.

|  |
| --- |
| Tip |
| If you created a rule for a vSphere backup proxy or Hyper-V off-host backup proxy, you can check whether it applies. For this, open the [Traffic Rules](vmware_proxy_traffic.md) (vSphere) [Traffic Rules](hv_proxy_traffic.md) (Hyper-V) step of the backup proxy wizard. The rule must be in the list of rules. |


