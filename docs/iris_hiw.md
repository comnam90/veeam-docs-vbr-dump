---
title: "Solution Architecture"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Solution Architecture


Epic EHR System Protection protection in Veeam Backup & Replication is a storage-integration workflow that protects InterSystems IRIS instances without going through a hypervisor. Rather than capturing the disk at the VM level, Veeam Backup & Replication uses the Universal Storage API to create application-consistent snapshots of the storage volumes that hold the InterSystems IRIS databases, and processes them with the unstructured data backup engine.

Solution Components

Epic EHR System Protection uses the following infrastructure components:

* Veeam Backup & Replication server orchestrates the entire workflow of discovery, backup policy sessions and restore operations. It communicates with ODB servers through the Veeam Transport service and with storage systems exclusively through the Universal Storage API.
* ODB server is the source Linux server that hosts InterSystems IRIS instances and whose volumes are backed up. During the first protection group rescan, Veeam Backup & Replication automatically deploys the following Veeam components on each ODB server:

* Veeam Transport service manages the secure connection between the Veeam Backup & Replication server and the ODB server. It authenticates using a TLS certificate installed during deployment and is the communication channel through which all subsequent operations run.
* InterSystems IRIS plug-in is an internal Veeam component that extends the Transport service with InterSystems IRIS-specific capabilities that list instances and collect topology (using iris qlist and iris.cpf), resolve the block-device hierarchy of instance volumes (including LVM devices and RDM disks), and perform freeze and thaw operations on the InterSystems IRIS instance during backup. The plug-in is not visible to end users.

* Storage system is a Universal Storage API-compatible storage array that presents the volumes used by InterSystems IRIS instances. Veeam Backup & Replication instructs it to create storage snapshots and thin clones through the Universal Storage API. It must be registered in Veeam Backup & Replication with the Block storage for application protection role.
* Linux-based backup proxy receives the thin clones of storage snapshots exported over SAN (iSCSI or Fibre Channel) and runs the source data mover of the unstructured data backup engine. It reads data from the mounted clone and transfers it to the backup repository.
* Backup repository stores the backup files produced by the target data mover. All primary backup repositories available in Veeam Backup & Replication are supported. In snapshot-only mode, no backup repository is required; storage snapshots are retained on the storage system instead.

Backup Workflow

When you run an InterSystems IRIS backup policy, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication reads the list of InterSystems IRIS instances and their storage volumes collected during the protection group rescan and stored in the configuration database.
2. Veeam Backup & Replication connects to the Veeam Transport service on the ODB server and instructs the InterSystems IRIS plug-in to freeze the InterSystems IRIS instance to a consistent state. The plug-in calls the ExternalFreeze method on behalf of the instance owner specified in the policy processing settings.
3. Veeam Backup & Replication uses the Universal Storage API to create a storage snapshot of the volumes that hold the InterSystems IRIS instance data.
4. Veeam Backup & Replication instructs the InterSystems IRIS plug-in to thaw the InterSystems IRIS instance. The ExternalThaw method is called and the instance resumes normal operation. The freeze window is limited to the time it takes to create the storage snapshot.

For more information about running InterSystems IRIS database processes, see the [InterSystems IRIS Documentation](https://docs.intersystems.com/iris20261/csp/docbook/Doc.View.cls?FIND=CLASSES+Backup.General).

What happens next depends on the mode configured in the policy:

* Snapshot-only mode — the storage snapshot is retained on the storage system according to the snapshot retention settings configured in the policy. No data is transferred to a backup repository and the policy session ends.
* Backup mode — Veeam Backup & Replication uses the Universal Storage API to create a thin clone of the snapshot and exports it to the Linux-based backup proxy over SAN. The source data mover on the proxy mounts the clone, reads the InterSystems IRIS instance data from it using the unstructured data backup engine, and transfers the data to the target data mover on the backup repository, where it is stored as a backup file.

For more information about backup policy settings and the detailed backup workflow, see [Working with Application Backup Policy](iris_policy.md).

Page updated 2026-07-24

