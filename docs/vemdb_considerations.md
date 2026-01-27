---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_considerations.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and known limitations of Veeam Explorer for MongoDB.

General

Consider the following:

* When Veeam Explorer for MongoDB is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.
* Before you recover MongoDB data to another server, make sure MongoDB is installed on the target server. For more information on supported MongoDB versions, see [System Requirements](vemdb_systemreqs.md).
* Before you recover MongoDB data, make sure that the target system has the same major MongoDB version as the one installed on the backed-up system.
* Data recovery to MongoDB sharded clusters is not supported.
* You cannot recover MongoDB data encrypted with native MongoDB encryption.
* Before you use TLS or X.509 authentication with the System Certificate Authority option, make sure that the Certificate Authority file of the target replica set is added to the Trusted Root Certification Authorities certificate store of the mount server associated with the backup repository.
* Data recovery to machines running MongoDB Community Edition is not supported.
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

Restore

Consider the following when planning to restore MongoDB data:

* Veeam Explorer for MongoDB does not support restore using PowerShell Direct, VIX API or vSphere Automation API.
* Restoring an entire MongoDB instance does not preserve replica set infrastructure. For more information on how to redeploy the replica set, see the [MongoDB Manual](https://www.mongodb.com/docs/manual/tutorial/convert-standalone-to-replica-set/).
* When restoring collections, you can only restore to the primary node of the target MongoDB replica set.
* Point-in-time restore is only available when restoring multiple collections from the replica set node or when restoring an entire instance. Point-in-time restore is not available when restoring single databases, or when restoring multiple collections from a database. This is because MongoDB collects the oplog on the level of the entire replica set.
* You cannot restore MongoDB data from multiple backups in parallel to the same target machine.

Publish

Consider the following when planning to publish MongoDB data:

* Make sure that the volume with the write cache has enough free disk space to store the changes of the published database. The write cache is stored in the /var/lib/veeam/IRCache folder on the mount server.
* To be able to restore collections from a published instance, make sure the instance is published to the primary node of the target replica set.


