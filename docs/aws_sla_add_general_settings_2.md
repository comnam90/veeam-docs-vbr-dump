---
title: "How Health Check Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_sla_add_general_settings_2.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Health Check Works


When the backup appliance saves a new backup restore point to a backup repository, it calculates CRC values for metadata in the backup chain and saves these values to the chain metadata, together with the instance data. When performing a health check, the backup appliance verifies the availability of data blocks and uses the saved values to ensure that the restore points being verified are consistent.

If you have enabled health checks for the backup policy, the backup appliance performs the following operations at the day scheduled for a health check to run:

1. As soon as the backup appliance finalizes the backup window in all protected AWS Regions, the backup appliance starts the health check on the day specified at [step 5](aws_sla_add_general_settings.md) of the wizard. For each restore point in the standard backup chain, the backup appliance calculates CRC values for backup metadata and compares them with the CRC values that were previously saved to the restore point. The backup appliance also checks whether data blocks that are required to rebuild the restore point are available.
2. If the backup appliance does not detect data inconsistency, the health check session completes successfully. Otherwise, the session completes with an error.

Depending on the detected data inconsistency, the backup appliance performs the following operations:

* If the health check detects corrupted metadata in a full or an incremental restore point, the backup appliance marks the backup chain as corrupted in the appliance configuration database. During the next backup policy session, the backup appliance copies the full instance image, creates a full restore point in the backup repository and starts a new backup chain in the backup repository.

|  |
| --- |
| Note |
| Backup appliances do not support metadata check for encrypted backup chains. |

* If the health check detects corrupted disk blocks in a full or an incremental restore point, the backup appliance marks the restore point that includes the corrupted data blocks and all subsequent affected incremental restore points as incomplete in the appliance configuration database. During the next backup policy session, the backup appliance reads whole data blocks and copies those data blocks that have changed since the previous backup session with corrupted data blocks, and saves these data blocks to the latest restore point that has been created during the current session.

All restore points marked as incomplete will be deleted according to the specified retention policy settings.

Page updated 2026-05-21

