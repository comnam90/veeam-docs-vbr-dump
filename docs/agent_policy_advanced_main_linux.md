---
title: "Maintenance Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_advanced_main_linux.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Maintenance Settings


You can specify maintenance settings for a backup chain created with the Veeam Agent backup policy. Maintenance operations help make sure that the backup chain remains valid and consistent.

To specify maintenance settings for the backup policy:

1. In the Advanced Settings window, select the Maintenance tab.
2. On the Maintenance tab, select Remove deleted items data after and specify the number of days for which you want to keep the backup created with the backup job in the target location.

By default, the deleted items data retention period is 30 days. Do not set the deleted items retention period to 1 day or a similar short interval. In the opposite case, the backup job may work not as expected and remove data that you still require.

![Maintenance Settings](images/agent_policy_settings_maintain_linux.webp)


