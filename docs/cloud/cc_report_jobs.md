---
title: "Viewing Tenant Job Statistics"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_report_jobs.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---


In this article

When a tenant runs a backup, backup copy, replication job and CDP policy sessions targeted at a cloud repository or cloud host, Veeam Backup & Replication saves the jobs statistics and operation data to the configuration database on the SP backup server. In contrast to regular job statistics, for tenant jobs, Veeam Backup & Replication saves only such data that helps the SP monitor performance of the Veeam Cloud Connect infrastructure and determine possible performance bottlenecks. Sensitive information about tenant backup infrastructure, such as names of processed VMs, VM disks or backup infrastructure components, is not passed to the SP side.

The SP can view real-time statistics for currently performed tenant jobs and view results of job sessions performed within the last 24 hours.

Veeam Agent Backup Job Statistics

In the SP backup console, the SP can view statistics for Veeam Backup & Replication jobs only: VM backup jobs, Veeam Agent backup jobs managed by the backup server, backup copy jobs and replication jobs.

For Veeam Agent backup jobs that run on Veeam Agent computers (configured in Veeam Agent operating in the standalone mode or defined in a backup policy), Veeam Backup & Replication does not display detailed statistics for security purposes. For such jobs, only basic information about a backup job session is available in the SP backup console. This information includes the job name, job session status, session start and end time, name of the tenant or subtenant account under which the job was started and the amount of sent and received data. Detailed statistics on the job session is available in the Veeam Agent control panel on the Veeam Agent computer.

In This Section

* [Viewing Real-Time Statistics](realtime_statistics.md)
* [Viewing Job Session Results](session_results.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
