---
title: "Exporting Kasten Backups Manually"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/exporting_from_cluster.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---

# Exporting Kasten Backups Manually


You can manually export backups of Veeam Kasten applications to Veeam backup repositories.

To export application backups, you must perform the following steps:

1. Configure Veeam Backup repository location.

At the location profile settings, specify the Veeam Backup & Replication server and the Veeam backup repository that will keep application backups. For more information, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/configuration.html#veeam-backup-repository-location).

1. Export application restore point.

In the Veeam Kasten dashboard, select the restore point of an application which backup you want to export and select the necessary Veeam backup location profile. Veeam Kasten will export application backups to the Veeam backup repository according to these settings. For more information on the manual export of application backups, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/migration.html#manual-exports).

After you start the manual export, it appears in the Veeam Backup & Replication infrastructure under the Backups > Disk (Exported) node.


