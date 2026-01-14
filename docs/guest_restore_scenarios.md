---
title: "Mount Server Automatic Selection"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/guest_restore_scenarios.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Mount Server Automatic Selection

In this article

Veeam Backup & Replication automatically selects a mount server. The selected server depends on the source for recovery and the guest OS of the workload from which you recover files. The following table shows the order in which mount servers are selected. If a component is not present in the infrastructure or is unavailable, the next available server from the list is selected.

| Source | Workload Operating System | Mount Server |
| --- | --- | --- |
| VMware vSphere backup, | Linux | 1. Linux-based mount server associated with the repository.   In case of a storage snapshot, the Linux-based mount server associated with the storage.   1. Default Linux-based mount server. |
| Microsoft Windows | 1. Microsoft Windows-based mount server associated with the repository.   In case of a storage snapshot, Microsoft Windows-based mount server associated with the storage.   1. Default Microsoft Windows-based mount server. 2. Linux-based mount server with the installed ntfs-3g package and associated with the repository.   In case of a storage snapshot, the Linux-based mount server associated with the storage.   1. Default Linux-based mount server with the installed ntfs-3g package. 2. Helper appliance. 3. Prompt to select the mount server manually. |
| Imported backup | Linux | Default Linux-based mount server. |
| Microsoft Windows | 1. Default Microsoft Windows-based mount server. 2. Default Linux-based mount server with the installed ntfs-3g package. 3. Helper appliance. 4. Prompt to select the mount server manually. |
| Cloud Connect backup, Cloud Connect replica, Cloud Connect CDP replica | Linux | Not supported. |
| Microsoft Windows | 1. Default Microsoft Windows-based mount server. 2. Prompt to select the mount server manually. |
| Veeam Agent Backup | Linux, Mac | 1. [For Linux] Original Linux workload (workload whose data is recovered). 2. Linux-based mount server associated with the repository. 3. Default Linux-based mount server. |
| Microsoft Windows | 1. Microsoft Windows-based mount server associated with the repository. 2. Default Microsoft Windows-based mount server. 3. Linux-based mount server with the installed ntfs-3g package and associated with the repository. 4. Default Linux-based mount server with the installed ntfs-3g package. 5. Helper appliance. 6. Prompt to select the mount server manually. |

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
