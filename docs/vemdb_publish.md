---
title: "Data Publishing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_publish.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Data Publishing

In this article

Publishing a MongoDB instance allows you to temporarily attach the instance to the target MongoDB server without launching restore. Publishing typically occurs faster than using standard restore features and could be convenient when, for example, your time to perform disaster-recovery operations is limited.

Veeam Explorer for MongoDB mounts disks from the backup repository to the target machine (under the /run/media directory), retrieves required instance files and attaches the associated instance directly to MongoDB so that you can perform required operations using MongoDB tools such as MongoDB Compass.

Veeam Explorer for MongoDB allows you to restore collections managed by the published instance. You can use this feature to restore modified collections or to restore collections as of the point-in-time state of the published instance. For more information, see [Restoring From Published Instances](vemdb_rs_published_restore.md).

Before restoring data, read the [Considerations and Limitations](vemdb_considerations.md) section.

In This Section

* [How Publishing Works](vemdb_how_publish_works.md)

* [Publishing Instance](vemdb_rs_publish_instance.md)
* [Managing Publishing Session](vemdb_rs_publish_managing_session.md)

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
