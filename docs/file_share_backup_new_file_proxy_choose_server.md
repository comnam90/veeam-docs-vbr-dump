---
title: "Step 2. Choose Server"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/file_share_backup_new_file_proxy_choose_server.html"
last_updated: "8/9/2025"
product_version: "13.0.1.1071"
---

# Step 2. Choose Server

In this article

At the Server step of the wizard, specify server settings for the backup proxy.

1. From the Choose server list, select a server that you want to use as a backup proxy.

The list of servers contains only those managed servers that are added to the backup infrastructure. If the server is not added to the backup infrastructure yet, you can click Add New to open the New Windows Server or New Linux Server wizard. For more information, see the [Adding Microsoft Windows Servers](add_windows_server.md) and [Adding Linux Servers](add_linux_server.md) sections.

1. In the Description field, provide a description for future reference. The default description contains information about the user who added the backup proxy, date and time when the backup proxy was added.
2. In the Max concurrent tasks field, specify the number of tasks that the backup proxy can process in parallel.

If the number of parallel tasks reaches this value, the backup proxy will not start a new task until one of current tasks completes. Veeam Backup & Replication creates one task per every source file share. The recommended number of concurrent tasks is calculated automatically based on the amount of available resources. Backup proxies with multi-core CPUs can handle more concurrent tasks.

For example, for a 4-core CPU, it is recommended that you specify a maximum of 8 concurrent tasks, for an 8-core CPU — 16 concurrent tasks. When defining the number of concurrent tasks, keep in mind network traffic throughput in the infrastructure.

![Step 2. Choose Server](images/add_file_proxy_choose_server.webp "Choose Microsoft Windows Server")

Page updated 8/9/2025

Page content applies to build 13.0.1.1071
