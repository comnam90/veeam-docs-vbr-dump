---
title: "Managing Cloud Director I/O Filter"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/io_filter_cd_manage.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Managing Cloud Director I/O Filter


The I/O filter that reads and processes I/O operations between the protected vApps and their underlying datastore, and sends and receives data from CDP proxies. Also, the filter communicates with the Veeam CDP Coordinator Service on the backup server and notifies the service that the backup infrastructure must be reconfigured if any proxy becomes unavailable. This I/O filter is built on the basis of vSphere API for I/O filtering (VAIO).

The filter is required if you want to protect vApp with [continuous data protection (CDP)](vcloud_director_cdp.md).


