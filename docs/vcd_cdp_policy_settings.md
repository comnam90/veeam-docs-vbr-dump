---
title: "Step 9. Specify Data Transfer and Replica Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_policy_settings.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Step 9. Specify Data Transfer and Replica Settings

In this article

At the Policy Settings step of the wizard, select CDP proxies that must be used for the CDP policy, specify which suffix to add to replica names and CDP proxies availability:

1. Specify which CDP proxies you want to use:

* If you want Veeam Backup & Replication to select proxies automatically, leave Automatic selection in the Source proxy and Target proxy fields.

Veeam Backup & Replication will assign CDP proxies for processing one by one. Before processing a new workload from the list, Veeam Backup & Replication will check available CDP proxies.

* If you want to select CDP proxies manually, do the following:

1. Click Choose next to the Source proxy field if you want to select CDP proxies in the production site, or next to the Target proxy field if you want to select CDP proxies in the disaster recovery site.
2. In the Backup Proxy window, click Use the selected backup proxy servers only. Select proxies that you want to use and click OK.

|  |
| --- |
| Note |
| We recommend that you deploy at least two CDP proxies: one CDP proxy in the production site and one CDP proxy in the disaster recovery site. |

1. To test whether CDP proxies available in the backup infrastructure can handle replication, click Verify whether currently available resource can handle can handle CDP activity.

Veeam Backup & Replication will analyze available CPU on all source and all target CDP proxies, the maximum disk write speed during the last hour, and will calculate approximate requirements for CDP proxies. In the CDP Infrastructure Assessment window, you will see the calculated values:

* The CPU rows show CPU cores available on all proxies (source or target).
* The Proxy RAM rows show RAM required for CDP and, in parenthesis, RAM available on all proxies (source or target). If values in the parentheses and near the paranthesis are the same, you need to upgrade proxies for which values coincide to provide more resources. For example, you can double up the amount of RAM.
* The Proxy Bandwidth rows show the maximum disk write speed during the last hour and, in parenthesis, available bandwidth based on available cores of source or target proxies.

1. In the Replica name suffix field, specify a suffix that will be added to names of replicas.

![Step 9. Specify Data Transfer and Replica Settings](images/vcd_cdp_policy_settings.webp)

Related Topics

[How Cloud Director CDP Works](vcloud_director_cdp_hiw.md)

Page updated 9/1/2025

Page content applies to build 13.0.1.1071
