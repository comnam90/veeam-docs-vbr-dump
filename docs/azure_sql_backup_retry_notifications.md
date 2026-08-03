---
title: "Step 6. Configure General Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_sql_backup_retry_notifications.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 6. Configure General Settings


At the Settings step of the wizard, you can enable automatic retries, schedule health checks and specify notification settings for the backup policy.

Automatic Retry Settings

To instruct the backup appliance to run the backup policy again if it fails on the first try, do the following:

1. In the Schedule section of the step, select the Automatic retry failed policy check box.
2. In the field to the right of the check box, specify the maximum number of attempts to run the backup policy. The time interval between retries is 600 seconds.

When retrying backup policies, the backup appliance processes only those Azure SQL databases that failed to be backed up during the previous attempt.

|  |
| --- |
| Note |
| The automatic retry settings apply only to backup policies that run according to specific schedules — these settings do not apply to policies [started manually](azure_backup_policy_start_stop.md). |

Private Endpoint Settings

If any of the Azure SQL databases that you have selected at [step 3](azure_sql_backup_source_settings.md#resources) of the wizard cannot be accessed through a public network, you must allow the backup appliance to create and use private endpoints to protect these databases — to do that, set the Enable private endpoint creation toggle to On. Otherwise, the appliance will only create backups of SQL databases that can be accessed through a public network, and the backup policy will complete with an error.

|  |
| --- |
| Important |
| If the selected databases and your backup appliance belong to the same Microsoft Entra tenant, the private endpoints will be automatically approved upon creation, and you will not have to take any additional configuration steps. Otherwise, the endpoints will be created with the Pending status, and you will have to either approve them manually as described in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/postgresql/network/how-to-networking-servers-deployed-public-access-approve-private-endpoint?tabs=portal-approve-private-endpoint-connections) or enable automatic endpoint approval for the service account specified in the policy settings as described in section [Adding Service Accounts](azure_service_account_endpoint_approval.md). |

Health Check Settings

The backup appliance can periodically perform a health check for all restore points created by the backup policy. During the health check, the backup appliance performs an availability check for data blocks in the whole regular backup chain, and a cyclic redundancy check (CRC) for metadata to verify its integrity. The health check helps you ensure that the restore points are consistent and that you will be able to restore data using these restore points. For more information on the health check, see [How Health Check Works](azure_sql_how_health_check_works.md).

|  |
| --- |
| Note |
| During a health check, the backup appliance does not verify archived restore points created by the policy. |

To instruct Veeam Backup for Microsoft Azure to perform a health check, do the following:

1. In the Health check section of the step, set the Enable health check toggle to On.
2. Use the Run on drop-down lists to schedule a specific day for the health check to run.

|  |
| --- |
| Note |
| The backup appliance performs the health check during the last policy session that runs on the day when the health check is scheduled. If another backup policy session runs on the same day, the backup appliance will not perform the health check during that session. For example, if the backup policy is scheduled to run multiple times on Saturday, and the health check is also scheduled to run on Saturday, the health check will only be performed during the last policy session on Saturday. |

Notification Settings

To instruct the backup appliance to send email notifications for the backup policy, do the following:

1. In the Notifications section of the step, set the Enabled toggle to On.

If you set the toggle to Off, the backup appliance will not send any notifications for this backup policy — regardless of the configured [global notification settings](azure_configuring_notification_settings.md).

1. In the Email field, specify an email address of a recipient. Use a semicolon to separate multiple recipient addresses.
2. Use the Notify on list to choose whether you want the backup appliance to send email notifications in case the backup policy completes successfully, completes with warnings or completes with errors.

|  |
| --- |
| Note |
| If you specify the same email recipient in both backup policy notification and [global notification settings](azure_configuring_notification_settings.md), the backup appliance will override the configured global notification settings and will send each notification to this recipient only once to avoid notification duplicates. |

[![Adding Backup Policy](images/azure_sql_backup_settings.webp)](images/azure_sql_backup_settings.webp "Adding Backup Policy")

Page updated 2026-07-28

