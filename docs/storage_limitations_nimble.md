---
title: "HPE Alletra 5000, 6000, Nimble"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_nimble.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# HPE Alletra 5000, 6000, Nimble

In this article

If you plan to perform operations with HPE Alletra 5000, 6000, Nimble storage systems, consider the following:

* Some versions of Nimble OS may not be supported when the Linux-based backup server operates in FIPS-compliant mode.
* [For backup from storage snapshots] To backup from HPE Alletra 5000, 6000, Nimble Group arrays, we recommend configuring Nimble Connection Manager on Microsoft Windows-based backup proxies. Otherwise, LUNs of temporary snapshots may not be mounted to the backup proxy during backup.

* [For backup from secondary storage arrays] You must configure Volume Collection replication from the primary storage array to the secondary storage array. For more information, see the HPE Alletra 5000, 6000, Nimble documentation.

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
