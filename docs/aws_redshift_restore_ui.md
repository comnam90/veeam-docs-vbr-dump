---
title: "Redshift Clusters Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_redshift_restore_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Redshift Clusters Restore Using Web UI


In case of a disaster, you can restore a Redshift cluster from a Redshift backup. Veeam Plug-in for AWS allows you to restore one or more Redshift clusters at a time to the original location, with the source or different settings. To learn how Redshift restore works, see [Redshift Restore](aws_restore_hiw_redshift.md).

|  |
| --- |
| Important |
| * Veeam Plug-in for AWS supports restoring Redshift clusters only to the same AWS accounts to which the source clusters belong and to the same AWS Region where the source cluster resides.  * Veeam Plug-in for AWS supports restoring only those Redshift cluster properties that are described in section [Protecting Redshift Clusters](aws_overview_redshift.md#properties).  * Veeam Plug-in for AWS does not support restoring Amazon Redshift clusters with the Multi-AZ deployment. These clusters will be restored as clusters with the Single-AZ deployment. |

To restore a protected Redshift cluster, do the following:

1. [Launch the Redshift Restore wizard](aws_restore_launch_redshift.md).
2. [Select a restore point](aws_restore_point_redshift.md).
3. [Specify account settings for restore](aws_restore_account_redshift.md).
4. [Choose a restore mode](aws_restore_mode_redshift.md).
5. [Enable encryption for the restored cluster](aws_restore_encryption_redshift.md).
6. [Configure Redshift cluster settings](aws_restore_redshift_settings.md).
7. [Configure network settings](aws_restore_redshift_networks.md).
8. [Specify a restore reason](aws_restore_reason_redshift.md).
9. [Finish working with the wizard](aws_restore_finish_redshift.md).

Page updated 2026-05-22

