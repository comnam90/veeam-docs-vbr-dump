---
title: "Step 3. Configure Traffic Rules"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_new_file_proxy_traffic_rules.html"
last_updated: "11/15/2024"
product_version: "13.0.1.1071"
---

# Step 3. Configure Traffic Rules


At the Traffic Rules step of the wizard, configure network traffic rules. These rules help you throttle and encrypt traffic transferred between backup infrastructure components. For more information, see [Configuring Network Traffic Rules](network_rules.md).

The list of network traffic rules contains only rules applied to the backup proxy: its IP address falls into the IP range configured for the rule.

To view settings configured for the rule:

1. Select the rule in the list.
2. Click View. The View Network Traffic Rule window will display settings configured for the rule.

To modify network traffic settings:

1. Click the Manage network traffic rules link.
2. The Global Network Traffic Rules window will display the full list of all existing global network traffic rules.
3. Select the rule that you want to modify and click Edit. For more information on how to configure network traffic rules, see [Configuring Network Traffic Rules](network_rules.md).

![Step 3. Configure Traffic Rules](images/add_file_proxy_traffic_rules.webp "Configure Traffic Rules")


