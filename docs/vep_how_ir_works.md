---
title: "How Instant Recovery Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_how_ir_works.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# How Instant Recovery Works


Instant recovery of PostgreSQL instances with Veeam Explorer for PostgreSQL works in the following manner:

1. To start the instant recovery process, Veeam Explorer for PostgreSQL sends an instant recovery command to the Veeam Mount Service. The service runs on the mount server associated with the backup repository.
2. The Veeam Mount Service delegates this request to the Veeam Explorers Recovery Service running on the same server.
3. The Veeam Explorers Recovery Service connects to the target server. The service validates the permissions of the selected user and checks if there is enough free space on the target server.

Some aspects of the validation process vary depending on the operating system of the PostgreSQL machine.

* For Windows machines, Veeam Explorer for PostgreSQL uses the Veeam PostgreSQL Restore Service on the target server. This persistent component checks the valid rights assignments required for data recovery, gets information about the PostgreSQL instances, and later performs the required file operations.
* For Linux machines, the Veeam Explorers Recovery Service performs the necessary validations, for example, validating the SSH fingerprints of the target server, without using a persistent component.

The Veeam Explorers Recovery Service sends a request to the Veeam Mount Service to connect to the backup repository and initiate the mounting operation.

1. The Veeam Mount Service mounts the necessary file system from the backup repository to the C:\VeeamFLR directory for Windows machines or the /run/media directory for Linux machines. For more information, see [How Mounting Works](vep_mount.md). The Veeam Explorers Recovery Service starts the instance from the mounted file system.
2. The Veeam Explorers Recovery Service replicates the published instance on the target server using the pg\_basebackup utility. All changes in instance files that occur after publishing are saved in the instant recovery write cache, which is stored in the /var/lib/veeam/IRCache folder (for Linux machines) or the C:\ProgramData\Veeam\Backup\IRCache folder (for Windows machines) on the mount server. The standby instance is continuously synchronized with the changes on the published instance.

After the instances are fully synchronized, you can switch over to the up-to-date standby instance on the production server. For more information on the available switchover options, see [Switchover](vep_ir_switchover.md).

During switchover, the Veeam Explorers Recovery Service does the following:

1. Switches the published instance to the read-only mode.
2. Synchronizes the remaining differences between the published instance and the standby instance on the target server.
3. Turns off the published and the standby instance.
4. Starts the standby instance as a standalone instance.

The instant recovery session is resilient to network disruptions, backup server or mount server crashes. If anything disrupts the instant recovery process, the process stays in the waiting mode and performs 10 automatic retries every 5 minutes. If the retries fail, you can launch retry after the server or network is up.

[![How Instant Recovery Works](images/vepg_ir.webp)](images/vepg_ir.webp "How Instant Recovery Works")

Page updated 2026-07-24

