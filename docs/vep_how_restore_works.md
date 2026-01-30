---
title: "How Restore Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_how_restore_works.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# How Restore Works


Restoring PostgreSQL instances with Veeam Explorer for PostgreSQL works in the following manner:

1. To start the restore process, Veeam Explorer for PostgreSQL sends a restore command to the Veeam Mount Service. The service runs on the mount server associated with the backup repository.
2. The Veeam Mount Service delegates this request to the Veeam Explorers Recovery Service running on the same server.
3. The Veeam Explorers Recovery Service connects to the target server. The service validates the permissions of the selected user and checks if there is enough free space on the target server. The Veeam Explorers Recovery Service sends a request to the Veeam Mount Service to connect to the backup repository and initiate the mounting operation.
4. The Veeam Mount Service uses FUSE to mount the necessary file system from the backup repository to the /run/media directory on the target PostgreSQL machine.
5. The Veeam Explorers Recovery Service copies the data directory and WAL files from the mounted file system to the native file system of the target machine. The service edits the postgresql.conf file with the selected restore settings, starts the instance and reverts the postgresql.conf file to its previous state.

The restore session is resilient to network disruption, backup server or mount server crashes. If anything disrupts the publishing process (the target or mount server crashes, or the network is down), you can launch the retry manually after the server or network is up.

After the restore operation successfully completes, Veeam Explorer for PostgreSQL unmounts the mounted file system and if necessary, performs the post-restore actions selected at the [Specify Post-Restore Action](vep_restore_single_tas_specify_post_restore_action.md) step.

[![How Restore Works](images/vepg_restore.png)](images/vepg_restore.png "How Restore Works")


