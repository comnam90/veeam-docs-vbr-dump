---
title: "Microsoft Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_ms_environment_planning_mssql.html"
last_updated: "6/10/2026"
product_version: "13.0.2.29"
---

# Microsoft Environment Planning


The integration of Microsoft SQL Server and Veeam Plug-In requires additional environment planning. When you deploy the plug-in, keep in mind the following requirements and limitations.

Data Stream Allocation

Veeam Plug-In for Microsoft SQL Server transfers backup data from the machine with protected Microsoft SQL Server to Veeam backup repository using data streams. By default, Veeam Plug-In uses one data stream per backup operation. You can configure Veeam Plug-In to use additional data streams that will process backup data in parallel. This may be helpful if you want to reduce time spent on your backup operations.

If you want to use additional data streams, configure the Concurrent backup streams setting at the Backup Options step of the Back Up Database wizard. The Concurrent backup streams setting defines the maximum allowed number of data streams being used for each database. For details, see [Specify Backup Options](backup_job_options.md).

Data Stream Distribution

Veeam Plug-In for Microsoft SQL Server distributes data streams between databases that you want to back up in accordance to the resources available on Microsoft SQL Server and backup repository server. As a result, available data streams are distributed considering the following:

* Number of CPU cores on Microsoft SQL Server: Veeam Plug-In can assign no more than 2 data streams per 1 CPU core.
* Amount of RAM on Microsoft SQL Server: Veeam Plug-In can assign no more than 5 data streams per 1 GB RAM.

* Number of available task slots in the backup repository: each parallel data stream uses 1 task slot of the backup repository. To learn how to edit the number of concurrent tasks allowed for the backup repository, see the [Limitation of Concurrent Tasks](limiting_tasks.md#task-limitation-for-backup-repositories) section in Veeam Backup & Replication User Guide.

Example:

You want to back up 2 databases. Using the Concurrent backup streams setting, you set a maximum allowed number of data streams for each database as 5. Thus, you need 10 data streams to back up 2 databases with parallel data streams.

Your Microsoft SQL Server has 4 CPU cores and 4 GB RAM. Your backup repository has 10 available task slots. In this example, the number of data streams is limited by the CPU of your Microsoft SQL Server: 8 data streams in total.

As a result, Veeam Plug-In will split there data streams between 2 databases and process these databases in parallel: Veeam Plug-In will process the first database using 5 parallel streams and the second database using 3 parallel streams. Keep in mind, if number of available data streams is enough for 1 database only, Veeam Plug-In will process databases one by one.


