---
title: "Step 8. Configure Re-IP Rules"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_policy_reip.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 8. Configure Re-IP Rules


The Re-IP step is available if you have selected the Replica re-IP check box at the [Name](uni_cdp_policy_name.md) step of the wizard.

At the Re-IP step of the wizard, configure re-IP rules. These rules map IPs in the production site to IPs in the disaster recovery (DR) site. When you perform failover, Veeam Backup & Replication will check the configured re-IP rules and will change replica IPs if the rules apply. Replicas will get new IP addresses according to the network masks specified in the rules, so that you will be able to reach replicas in the DR site.

To configure a re-IP rule:

1. Click Add.
2. In the Source VM section, specify an IP numbering scheme used in the production site.

To facilitate the configuration, Veeam Backup & Replication detects an IP address and subnet mask for the backup server and pre-populates values in the Source VM section.

1. In the Target VM section, specify an IP address, subnet mask and default gateway that will be used for replicas in the DR site. If required, specify the DNS server addresses. You can also specify WINS server addresses.
2. In the Description field, provide a description.
3. Click OK.

|  |
| --- |
| Note |
| Consider the following:   * Only IPv4 rules are supported.  * You can specify static IPs or IP ranges. Do not use 0 to specify IP address ranges. In Veeam Backup & Replication, value 172.16.17.0 means a regular IP address 172.16.17.0, not an IP address range. To specify a range, use the asterisk character (\*).   The asterisk matches one entire octet, and re-IP rules match source IPs by octet only — the subnet mask is not used to select which IPs a rule applies to. For example, the source address 10.0.0.\* matches 10.0.0.0 through 10.0.0.255, but not 10.0.1.1, even if both addresses belong to the same subnet.   * Replica re-IP works only for Microsoft Windows VMs. * Replica re-IP works only if you perform replica failover using Veeam Backup & Replication. If you power on a replica in some other way, for example, manually using a native client, re-IP rules will not be applied to it. * The backup server OS must support mounting of the system disks of VMs that will be replicated. |

![Step 8. Configure Re-IP Rules](images/uni_cdp_policy_reip.webp "Configure re-IP rules")

Page updated 2026-05-20

