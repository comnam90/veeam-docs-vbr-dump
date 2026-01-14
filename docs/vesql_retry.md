---
title: "Retrying Instant Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_retry.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# Retrying Instant Recovery

In this article

If anything disrupts the restore process (the target or mount server crashes or the network is down), the restore process stays in the waiting mode and performs 10 automatic retries every 5 minutes. If the retries fail, you can launch the retry manually after the server or network is up.

To start the retry process manually, do the following:

1. In the navigation pane, under the Instant Recovery node, select the database.
2. On the Instant Recovery tab, click Retry.

Alternatively, you can right-click the database and select Retry.

[![Retrying Recovery](images/instant_retry.webp)](images/instant_retry.webp "Retrying Recovery")

Page updated 8/25/2025

Page content applies to build 13.0.1.1071
