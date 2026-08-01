---
title: "Redshift Clusters Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Clusters Restore


|  |
| --- |
| Important |
| You can restore a Redshift cluster only to the same AWS account to which the source cluster belongs and the same AWS Region where the source cluster resides. |

To restore a Redshift cluster from a backup, a backup appliance performs the following steps using native [AWS capabilities](https://docs.aws.amazon.com/aws-backup/latest/devguide/redshift-restores.html):

1. Creates a cluster in the specified location.
2. Modifies the configuration setting values of the created Redshift cluster.
3. Restores backed-up databases to the restored Redshift clusters.

To learn how to restore a Redshift cluster from a Redshift backup, see [Redshift Clusters Restore](aws_redshift_restore.md).

Page updated 2026-05-15

