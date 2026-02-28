---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_publish_before.html"
last_updated: "2/25/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you publish disks, check the following requirements and limitations:

* The necessary ports must be opened on the target server. For more information, see [Ports](used_ports.md).
* The target server must support the file system of the disk that you plan to publish.
* macOS computers are not supported as target servers.
* Unix servers are supported as target servers for publishing disks only from backups of Unix-based computers
* If data deduplication is enabled for some disks in a backup, data deduplication must be enabled on the target server.
* [For Microsoft Windows-based Veeam Agent computers] The target Microsoft Windows server must support the same ReFS version or later than the version used on the Veeam Agent computer from which you plan to publish disks. For more information on which OSes support which ReFS, see the [ReFS versions and compatibility matrix](https://gist.github.com/0xbadfca11/da0598e47dd643d933dc#mountability).
* [For Linux-based, Unix-based and macOS-based Veeam Agent computers] You cannot publish disks from backups stored in the Veeam Cloud Connect repository.
* [For Linux-based and Unix-based Veeam Agent computers] If the disk you want to publish contains a Logical Volume Manager (LVM) volume group, Veeam Agent will publish the original disk and the LVM volume group as 2 separate disks. This may lead to the increase of the required storage space. For example, if you publish all disks from a backup of a machine that has 2 disks and a separate LVM volume group on each disk, Veeam Agent will publish 4 disks. The published disks will consume storage space equal to the size of 2 original disks and 2 LVM volume groups from these disks.

For the full list of limitations, see [Considerations and Limitations](https://helpcenter.veeam.com/docs/vbr/userguide/data_integration_api.html?ver=13#considerations-and-limitations).


