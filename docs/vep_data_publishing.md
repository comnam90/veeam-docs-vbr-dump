---
title: "Data Publishing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_data_publishing.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Data Publishing

In this article

Publishing a PostgreSQL instance allows you to temporarily attach the instance to the target PostgreSQL server without launching restore. Publishing typically occurs faster than using standard restore features and could be convenient when, for example, your time to perform disaster-recovery operations is limited.

Veeam Explorer for PostgreSQL mounts disks from the backup repository to the target machine (under the /run/media directory), retrieves required instance files and attaches the associated instance directly to PostgreSQL so that you can perform required operations using PostgreSQL tools such as pgAdmin.

After you have launched a publishing operation to a PostgreSQL machine, you can quickly republish the latest or point-in-time state of the instance to the same machine.

Once you are done working with the published instance, you can export the modified databases managed by the published instance. For more information, see [Exporting From Published Instances](vep_published_export.md).

Before publishing data, read the [Considerations and Limitations](vep_considerations.md) section.

In This Section

* [How Publishing Works](vep_how_publishing_works.md)
* [Publishing to Specified Server](vep_ptsr.md)
* [Publishing Latest or Point-in-Time State](vep_pit.md)
* [Managing Publishing Session](vep_publish_managing_session.md)

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
