---
title: "Redshift Serverless Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_redshift_serverless_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Restore Using Console


You can recover corrupted Redshift Serverless namespaces in the backup appliance Web UI only. However, you can launch the Redshift Serverless Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects the Redshift Serverless namespaces you want to recover, select the necessary namespace and click Amazon Redshift Serverless on the ribbon.

Alternatively, you can right-click the selected namespace and click Restore to Amazon Redshift Serverless.

|  |
| --- |
| Important |
| Restoring multiple Redshift Serverless namespaces is not supported. |

Veeam Backup & Replication will open the Redshift Serverless Restore wizard in a web browser. Complete the wizard as described in section [Redshift Serverless Restore Using Web UI](aws_restore_point_redshift_serverless.md).

[![Restore to Amazon Redshift Serverless](images/aws_restore_serverless.webp)](images/aws_restore_serverless.webp "Restore to Amazon Redshift Serverless")

Page updated 2026-07-20

