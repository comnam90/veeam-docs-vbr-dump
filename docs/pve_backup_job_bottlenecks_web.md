---
title: "Analyzing Performance Bottlenecks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_bottlenecks_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Analyzing Performance Bottlenecks


As any backup application handles a great amount of data, it is important to make sure the data flow is efficient and all resources engaged in the backup process are optimally used. For backup jobs, Veeam provides advanced statistics about the data flow efficiency and lets you identify bottlenecks at the following stages of the data transmission process:

1. Reading VM data blocks from the source.
2. Processing VM data on a worker.
3. Transporting data over the network.
4. Writing data to the target.

[![bottleneck](images/vplugins_bottlenecks_scheme.webp)](images/vplugins_bottlenecks_scheme.webp "bottleneck")

While evaluating the data transmission process, Veeam Backup & Replication analyzes performance of all the data flow components:

* Source — the source disk reader component responsible for retrieving data from the source node.
* Proxy — the worker component responsible for processing VM data.
* Network — the network queue writer component responsible for getting processed VM data from the worker and sending it over the network to the Target (directly or through the Gateway Server).
* Target — the gateway server component responsible for processing VM data, or the target disk writer component responsible for storing data in the backup repository.

To see the bottleneck statistics for a job or a specific VM processed by the job, do the following:

1. Navigate to Jobs.
2. In the working area, select the necessary job and click Manage > Details.

Alternatively, you can right-click the job and select Manage > Details.

1. In the Backup Job Details tab, check the bottleneck statistics.

To learn how to analyze the bottleneck statistics, see [Performance Bottlenecks](detecting_bottlenecks.md).

[![Analyzing Performance Bottlenecks](images/pve_bottlenecks_web.webp)](images/pve_bottlenecks_web.webp "Analyzing Performance Bottlenecks")

Page updated 2026-07-20

