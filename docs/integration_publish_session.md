---
title: "Managing Publishing Disks Session"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_publish_session.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# Managing Publishing Disks Session


After you started a publishing session, you can check details about the session or stop it.

Viewing Statistics on Publishing Session

To view publishing session statistics, do one of the following:

* Open the Home view. In the inventory pane, select Instant Recovery. In the working area, select the necessary publishing session and click Properties on the ribbon. Alternatively, right-click the session and Properties.
* Open the Home view. In the inventory pane select Last 24 hours. In the working area, double-click the necessary publishing session. Alternatively, you can select the session and click Statistics on the ribbon or right-click the session and select Statistics.
* Open the History view. In the inventory pane select Restore. In the working area, double-click the necessary publishing session. Alternatively, you can select the session and click Statistics on the ribbon or right-click the session and select Statistics.

The publishing statistics provides the following data:

* At the top of the Restore Session window, Veeam Backup & Replication shows general session statistics. It includes a name of the Veeam Agent computer whose disk you want to publish, a name of the backup server which initiated the publishing session, a user name of the account under which the session was started, session status and duration details.

* The Reason tab shows the reason for the publishing session.
* The Parameters tab shows information about the target server, the Veeam Agent computer whose disks you publish and the restore point selected for publishing.
* The Log tab shows the list of operations performed during the session.

[![Managing Publishing Disks Session](images/disk_publish_statistics_agents.webp)](images/disk_publish_statistics_agents.webp)

Stopping Publishing Session

To stop a publishing session, do one of the following:

* Open the Home view. In the inventory pane select Instant Recovery. In the working area, double-click the necessary publishing session and click Cancel restore task in the Restore Session window. Alternatively, you can select the necessary publishing session and click Stop Publishing on the ribbon or right-click the session and click Stop Publishing.
* Open the Home view. In the inventory pane select Last 24 hours. In the working area, double-click the necessary publishing session and click Cancel restore task in the Restore Session window. Alternatively, you can select the necessary publishing session and click Stop on the ribbon or right-click the session and click Stop.
* Open the History view. In the inventory pane select Restore. In the working area, select the necessary publishing session and double-click it. In the Restore Session window, click Cancel restore task. Alternatively, you can right-click the publishing session and click Stop session.

[![Managing Publishing Disks Session](images/disk_publish_stop_agents.webp)](images/disk_publish_stop_agents.webp)


