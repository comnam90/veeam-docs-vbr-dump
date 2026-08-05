---
title: "Rescan Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_rescan_job.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Rescan Job


For automated discovery of ODB servers and InterSystems IRIS instances, Veeam Backup & Replication uses the rescan job that runs on the backup server. Veeam Backup & Replication automatically creates this job when you create the protection group. The rescan job runs on the schedule defined individually for each protection group. By default, Veeam Backup & Replication performs discovery at 9:00 PM daily. You can adjust the daily schedule or switch to a periodic schedule in the protection group settings.

The rescan job is not displayed in the Veeam Backup & Replication console. However, you can start and stop rescan job sessions manually for a specific protection group. This may be helpful, for example, if a new ODB server was added to your environment and you want to discover it without waiting for the next scheduled run. For details, see [Rescanning Protection Group](iris_protection_group_rescan.md).

You can view statistics for currently running and completed rescan job sessions. For details, see [Viewing Rescan Job Statistics](iris_report_rescan_job_stats.md).

How Rescan Job Works

When the rescan job starts, Veeam Backup & Replication performs the following operations:

1. Reads the list of ODB servers to scan and the credentials for connecting to them from the protection group settings on the configuration database.
2. Connects to each ODB server over SSH or through the Deployment Kit using the account specified in the protection group configuration. After a successful connection, Veeam Backup & Replication checks whether the Veeam Transport service and the InterSystems IRIS plug-in are installed on the server.
3. Deploys Veeam components on each newly discovered ODB server. As part of this process, Veeam Backup & Replication performs the following:

1. Copies and installs the Veeam Transport service binaries over SSH or using the Deployment Kit.
2. Copies and installs the TLS certificate. Veeam Backup & Replication uses this certificate for subsequent connections to the Transport service.
3. Copies and installs the InterSystems IRIS plug-in. The plug-in extends the Transport service with the capability to interact with InterSystems IRIS instances, enabling listing instances, collecting topology, and performing freeze and thaw operations during backup.
4. Runs the topology collection task. The result is returned to the backup server as an XML document and saved to the configuration database.

|  |
| --- |
| Note |
| If a new ODB server is added to an existing protection group, you must edit the protection group and rescan it to deploy the components on the new server. For details, see [Editing Protection Group Settings](iris_protection_group_edit.md) and [Rescanning Protection Group](iris_protection_group_rescan.md). |

1. Discovers the InterSystems IRIS instances and their storage volumes on each ODB server. During this step, Veeam Backup & Replication performs the following:

1. Lists InterSystems IRIS instances on the ODB server and obtains the paths to the instance configuration files.
2. Extracts data volume paths from each configuration file.
3. Reads the IRISFeatureTracker file, if present, to obtain a stable instance GUID. If the file is not present, the combination of instance name and BIOS UUID is used to identify the instance.
4. For each data path, resolves the block device hierarchy down to the raw block device, RDM or physical disk.
5. Matches the resolved devices against the information returned by the storage system rescan operation to confirm that the instance volumes reside on a registered USAPI storage system. If a volume cannot be matched, that instance is not added and the rescan operation fails.
6. Writes the discovered instance information to the configuration database, making the instances available for selection in an application backup policy.

1. Updates the cache repository used to store the CRC tree structure of the source instance file system. The cache enables incremental processing during subsequent backup sessions.

Page updated 2026-07-29

