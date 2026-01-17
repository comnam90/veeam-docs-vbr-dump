---
title: "Viewing Replicas and Failover Plans"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_view_replicas.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Viewing Replicas and Failover Plans


After replication job targeted at the cloud host or a cloud failover operation completes, it takes some time for Veeam Backup & Replication to retrieve changes from the database and display those changes in the Veeam Backup & Replication console on the tenant side. For example, when you perform a failover operation, VM replicas and cloud failover plans may be not displayed or displayed with a wrong status.

To refresh the view in the Veeam Backup & Replication console:

1. Open the Home view.
2. Expand the Replicas node and press [F5] to refresh the view.

[![View Replicas and Failover Plans](images/view_replicas.webp)](images/view_replicas.webp "View Replicas and Failover Plans")


