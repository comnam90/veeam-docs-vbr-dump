---
title: "VM Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_replication_how.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Replication


In addition to [image-level backups](pve_backup_job_how.md), you can protect your mission-critical VMs with replicas. A VM replica is an exact VM copy created in the native Proxmox VE format on the target host and maintained in sync with the original VM. Replication provides minimum recovery time objective (RTO), and ensures that you can access services and applications you need with minimum disruption.

To produce VM replicas, Veeam Backup & Replication runs replication jobs. A replication job is a collection of settings that define the way replication operations are performed: what VMs to replicate, where to store replicas, when to start the replication process, and so on. Veeam Backup & Replication does not install agent software inside VMs to perform replication — it uses native Proxmox VE capabilities instead; during every replication session, Veeam Backup & Replication creates a Proxmox VE copy-on-write snapshot of each VM replica produced by a replication job, and this snapshot further acts as a new restore point for the VM replica.

How to Replicate VMs

1. Check [system requirements](pve_system_requirements.md) and [account permissions](pve_permissions.md).
2. [Add backup repositories](pve_configure_repository.md).
3. [Connect the Proxmox VE server](pve_connecting_manager.md).
4. [Configure worker settings](pve_workers_add.md).
5. [Configure email settings and notifications](pve_general_settings.md).
6. [Complete the New Replication Job wizard](pve_replication_job_create.md).

How VM Replication Works

During the first replication session, Veeam Backup & Replication does the following:

1. Launches a worker on the source host (where the original VM resides) and another worker on the target host (where the VM replica will reside).
2. Creates empty disks and attaches them to the worker on the target host. The number of empty disks equals the number of disks attached to the original VM.
3. Uses the worker on the source host to read data from disks that are attached to the original VM, compresses and transfers the data to the worker on the target host.
4. Uses the worker on the target host to read and decompress the VM data, and transfers the data to the empty disks on this worker.
5. Takes a copy-on-write snapshot of the VM replica that will act as the first restore point in the replica chain.
6. Suspends the worker when the replication session completes.

During subsequent replication sessions, Veeam Backup & Replication does the following:

1. Launches a worker on the source host (where the original VM resides) and another worker on the target host (where the VM replica resides).
2. Veeam Backup & Replication reverts the VM replica to the most recent state to discard all changes made while the replica was running.
3. Attaches disks of the VM replica to the worker on the target host.
4. Uses the worker on the source host to read data from disks that are attached to the original VM, compresses and transfers the data to the worker on the target host.

Veeam Backup & Replication uses the changed block tracking (CBT) mechanism to reduce the amount of data read from VM disks: Veeam Backup & Replication reads only those data blocks that have changed since the previous replication session. If CBT cannot be used, Veeam Backup & Replication reads all data from the VM disks. For more information, see Changed Block Tracking.

1. Uses the worker on the target host to read and decompress the VM data, and transfers the data to the disks on this worker.
2. Takes a copy-on-write snapshot of the VM replica that will act as the next restore point in the replica chain.
3. Suspends the worker when the replication session completes.

Page updated 2026-07-21

