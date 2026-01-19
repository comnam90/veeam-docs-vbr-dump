---
title: "Step 7. Finalize Upgrade"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_upgrade_finalize.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Step 7. Finalize Upgrade


After you successfully upgraded Veeam Backup Enterprise Manager, consider the following recommendations:

1. If you have Veeam Backup & Replication installed on the same machine, upgrade it immediately after completing upgrade of the Veeam Backup Enterprise Manager server.
2. Proceed with upgrade of remote backup servers.

After you upgrade backup servers, Veeam Backup Enterprise Manager starts a maintenance job to optimize the state of its database. The initial maintenance job session may take significant amount of time (up to an hour, depending on the database size). After the job finishes, the database will be brought to an optimal state, and subsequent maintenance job sessions will take much less time.

1. New features of Veeam Backup Enterprise Manager will be available after all connected backup servers are upgraded, and initial collection of data from these servers in Veeam Backup Enterprise Manager completes successfully.
2. Download and install the latest available update (if any).


