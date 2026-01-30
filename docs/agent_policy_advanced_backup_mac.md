---
title: "Backup Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_advanced_backup_mac.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Backup Settings


To specify settings for a backup chain created with the backup policy:

1. In the Advanced Settings window, select the Backup tab.
2. If you want to periodically create synthetic full backups, select Create synthetic full backups periodically and click Configure to define the schedule.

|  |
| --- |
| NOTE |
| Synthetic full backup is not available for backup jobs targeted at an object storage repository. |

1. If you want to periodically create active full backups, select Create active full backups periodically and click Configure to define the schedule.

|  |
| --- |
| NOTE |
| Consider the following:   * Before scheduling periodic full backups, you must make sure that you have enough free space on the target location. * If you schedule the active full backup and synthetic full backup on the same day, Veeam Backup & Replication will perform only active full backup. Synthetic full backup will be skipped. |

![Backup Settings](images/agent_policy_settings_backup_mac.webp)


