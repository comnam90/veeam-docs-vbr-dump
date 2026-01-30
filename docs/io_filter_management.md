---
title: "Managing I/O Filter"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/io_filter_management.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Managing I/O Filter


The I/O filter reads and processes I/O operations on VMware vSphere hosts and clusters. It sends and receives data to or from CDP proxies. The filter communicates with the Veeam CDP Coordinator Service on the backup server and notifies the service that the backup infrastructure must be reconfigured if any proxy becomes unavailable. This I/O filter is built on the basis of vSphere API for I/O filtering (VAIO).

The I/O filter is required if you want to protect workloads with [continuous data protection (CDP) for VMware vSphere](cdp_replication.md) or [universal CDP](universal_cdp.md).

In This Section

* [Installing I/O Filter](cdp_io_filter_install.md)
* [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md)
* [Taking I/O Filter Ownership](cdp_io_filter_ownership.md)


