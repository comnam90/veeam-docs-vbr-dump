---
title: "Redshift Clusters Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_redshift_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Clusters Restore Using Console


You can recover corrupted Redshift clusters in the backup appliance Web UI only. However, you can launch the Redshift Cluster Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects the Redshift clusters you want to recover, select the necessary cluster and click Amazon Redshift on the ribbon.

Alternatively, you can right-click the selected cluster and click Restore to Amazon Redshift.

|  |
| --- |
| Important |
| You cannot restore multiple Redshift clusters from the Veeam Backup & Replication console. |

Veeam Backup & Replication will open the Redshift Cluster Restore wizard in a web browser. Complete the wizard as described in section [Redshift Restore Using Web UI](aws_restore_point_redshift.md).

[![Restore to Amazon Redshift](images/aws_redshift_cluster_restore_console.webp)](images/aws_redshift_cluster_restore_console.webp "Restore to Amazon Redshift")

Page updated 2026-07-20

