---
title: "EC2 Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_ec2_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# EC2 Restore Using Console


Veeam Backup & Replication offers the following restore operations:

* [Instance restore](aws_restoring_to_amazon.md) — restore an entire EC2 instance.
* [Guest OS file restore](aws_guest_file_recovery.md) — restore individual files and folders of an EC2 instance.
* [Application item restore](aws_application_items_restore.md) — restore applications such as Microsoft Entra ID, Microsoft Exchange, Microsoft SharePoint and Microsoft SQL Server.

You can restore EC2 instance data to the most recent state or to any available restore point.

|  |
| --- |
| Important |
| You can use restore points stored in standard backup repositories to perform all the listed recovery operations, while restore points stored in archive backup repositories can only be used to perform restore of EC2 to the original or to a new location. |

Page updated 2026-05-21

