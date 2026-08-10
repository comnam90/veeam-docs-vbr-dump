---
title: "Redshift Serverless Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Serverless Restore


|  |
| --- |
| Important |
| You can restore a Redshift Serverless namespace only to the same AWS account to which the source namespace belongs and the same AWS Region where the source namespace resides. |

To restore a Redshift Serverless namespace from a cloud-native backup, a backup appliance performs the following steps using native [AWS capabilities](https://docs.aws.amazon.com/redshift/latest/mgmt/serverless-snapshot-restore.html):

1. [Applies only if you perform restore to a new namespace] Creates a workgroup with the settings of a source workgoup or with custom settings in the region where the source namespace resides.
2. [Applies only if you perform restore to a new namespace] Creates a namespace with the settings of a source namespace or with custom settings in the region where the source namespace resides.
3. Restores backed-up database objects and users to the restored Redshift Serverless namespace.

To learn how to restore a Redshift Serverless namespace from a Redshift Serverless backup, see [Redshift Serverless Restore](aws_redshift_serverless_restore.md).

Page updated 2026-05-15

