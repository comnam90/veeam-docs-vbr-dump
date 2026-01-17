---
title: "Support for Archive Tier"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_archive_tier.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

Archive tier is a functionality to extend a scale-out backup repository with an additional tier of storage. In the Veeam Cloud Connect infrastructure, the SP can use the archive tier for backup of rarely accessed tenant data. Compared to the capacity tier, it is cheaper to store archived data in the archive tier, but more expensive to restore it from the archive tier. For more information on the archive tier functionality, see the [Archive Tier](https://helpcenter.veeam.com/docs/vbr/userguide/archive_tier.html?ver=13) section in the Veeam Backup & Replication User Guide.

Archived data must be prepared for the restore from the archive tier. The tenant cannot restore data from the archive tier without support of the SP. The SP must retrieve the archived data to enable a successful restore from the archive tier. In contrast to the regular backup scenario where SP can retrieve archived data using the Veeam Backup & Replication console, in the Veeam Cloud Connect scenario, this operation is available with a Microsoft PowerShell cmdlet only. For more information, see [Retrieving Tenant Data from Archive Tier](cc_archive_tier_publish.md).

How Restore from Archive Tier Works

In the scenario where the tenant data is stored in the archive tier, the SP and tenant perform restore in the following way:

1. The tenant attempts to perform a restore operation.
2. During the restore process, Veeam Backup & Replication displays the following message: Unable to restore from the Archive Tier because backup was not retrieved. Ask your service provider to publish restore point with ID ‘<restore point ID>’.
3. The tenant collects the message with the restore point ID and sends it to the SP.
4. The SP retrieves the data, publishes the restore point and notifies the tenant that the restore point is ready for a restore.
5. The tenant reattempts to perform the restore operation from the published restore point.

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
