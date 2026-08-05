---
title: "Application Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_backup_job.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Application Backup Policies


To back up InterSystems IRIS instances with Veeam Backup & Replication, you must configure an application backup policy. A backup policy defines which instances to protect, the target backup repository or storage snapshot location, and the schedule on which backups run. The policy can operate in two modes: backup mode, in which data is copied to a backup repository, or snapshot-only mode, in which only storage snapshots are retained on the storage system. The policy does not process the journal files of the InterSystems IRIS instance, so point-in-time restore is not available. For details, see [Backup Types](iris_backup_types.md).

For the application backup policy, all management tasks are performed on the Veeam Backup & Replication server side: Veeam Backup & Replication starts the policy according to the defined schedule, allocates backup infrastructure resources and orchestrates the snapshot and data-transfer operations. For more information, see [How Application Backup Policy for InterSystems IRIS Works](iris_backup_job.md#hiw).

To configure an application backup policy, launch the New Application Backup Policy wizard. For more information, see [Creating Application Backup Policy](iris_policy_create.md).

How Application Backup Policy for InterSystems IRIS Instance Works

When you use an application backup policy to protect InterSystems IRIS instances, Veeam Backup & Replication performs backup in the following way:

1. When you create an application backup policy in Veeam Backup & Replication, Veeam Backup & Replication saves the policy settings in its configuration database.
2. When a new backup policy session starts, Veeam Backup & Replication reads the policy settings and the list of InterSystems IRIS instances and their storage volumes discovered during the protection group rescan.
3. Veeam Backup & Replication starts the Veeam Backup Manager process on the backup server. Veeam Backup Manager reads the policy settings from the configuration database and creates a list of tasks to process. Veeam Backup & Replication processes one task per InterSystems IRIS instance.
4. Veeam Backup Manager connects to the Veeam Backup Service. The resource scheduler checks what backup infrastructure resources are available and assigns a Linux-based backup proxy and a backup repository to process the policy tasks.
5. Veeam Backup Manager establishes a connection with the Veeam Transport Service on the Linux-based backup proxy and on the backup repository, and sets rules for data transfer, such as network traffic throttling rules.
6. Veeam Backup & Replication connects to the Veeam Transport Service on the ODB server and instructs the InterSystems IRIS plug-in to freeze the instance to a consistent state. The plug-in calls the ExternalFreeze method on behalf of the instance owner specified in the policy processing settings. Write activity is paused until the storage snapshot is created.
7. Veeam Backup & Replication uses the Universal Storage API to instruct the storage system to create a storage snapshot of the volumes that hold the InterSystems IRIS instance data.
8. Veeam Backup & Replication instructs the InterSystems IRIS plug-in to thaw the instance. The ExternalThaw method is called and the instance resumes normal operation. All subsequent backup processing is performed against the immutable storage snapshot.

What happens next depends on the backup mode configured in the policy:

* In snapshot-only mode, the storage snapshot is retained on the storage system according to the snapshot retention settings. No data is transferred to a backup repository and the policy session ends here.
* In backup mode, Veeam Backup & Replication proceeds with steps 9–12 to copy data from the snapshot to the backup repository.

1. Veeam Backup & Replication uses the Universal Storage API to create a thin clone of the storage snapshot and exports it to the Linux-based backup proxy over SAN (iSCSI or Fibre Channel).
2. The source data mover on the Linux-based backup proxy mounts the snapshot clone and reads the data from the InterSystems IRIS instance volumes. The data is processed by the unstructured data backup engine and transferred to the target data mover on the backup repository.

On the first run, a full backup is produced. On subsequent runs, the unstructured data backup engine uses the change block tracking (CBT) mechanism to read and transfer only the changed blocks inside the .DAT files, reducing the amount of data read and transferred. For details, see [Backup Types](iris_backup_types.md).

1. Veeam Backup & Replication stores the backed-up data in the backup file in the backup repository.

Page updated 2026-07-29

