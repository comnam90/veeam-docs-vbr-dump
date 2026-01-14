---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/repo_before_you_begin.html"
last_updated: "11/24/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you configure a backup repository, check the following prerequisites.

Dell Data Domain

* Dell Data Domain must meet software and hardware requirements. For more information, see [System Requirements](system_requirements.md#target).
* Dell Data Domain must meet requirements listed in [Considerations and Limitations for Dell Data Domain](dell_dd.md#consider).
* The DD Boost license must be installed on the Dell Data Domain system, DD Boost must be enabled and configured.
* The gateway server that you plan to use for work with Dell Data Domain must be added to the backup infrastructure.
* Check vendor documentation dedicated to integration with Veeam. Some links you can find in [this Veeam KB article](https://www.veeam.com/kb1745#vendordocs).

If the Dell Data Domain storage system does not meet these requirements, you can add it as a SMB (CIFS) folder. In this case, Veeam Backup & Replication will not use the DD Boost technology to work with Dell Data Domain. For more information, see [Dell Data Domain](dell_dd.md).

ExaGrid

* ExaGrid must meet software and hardware requirements. For more information, see [System Requirements](system_requirements.md#target).
* To use ExaGrid as a backup repository, you must configure an ExaGrid share in ExaGrid Manager. For more information on how to configure the share and repository settings, see [ExaGrid](deduplicating_appliance_exgrid.md).

* Check vendor documentation dedicated to integration with Veeam. Some links you can find in [this Veeam KB article](https://www.veeam.com/kb1745#vendordocs).

HPE StoreOnce

* HPE StoreOnce must meet software and hardware requirements. For more information, see [System Requirements](system_requirements.md#target).

* HPE StoreOnce must meet requirements listed in [Considerations and Limitations for HPE StoreOnce](deduplicating_appliance_storeonce.md#consider).

* The HPE StoreOnce Catalyst license must be installed on the HPE StoreOnce system.
* You must use a Catalyst store as a backup target.
* The gateway server that you plan to use for work with HPE StoreOnce system must be added to the backup infrastructure.

* Check vendor documentation dedicated to integration with Veeam. Some links you can find in [this Veeam KB article](https://www.veeam.com/kb1745#vendordocs).

If the HPE StoreOnce storage system does not meet these requirements, you can add it as a shared folder. In this case, Veeam Backup & Replication will perform target-side deduplication. For more information, see [HPE StoreOnce](deduplicating_appliance_storeonce.md).

Quantum DXi

* Quantum DXi must meet software and hardware requirements. For more information, see [System Requirements](system_requirements.md#target).

* To use Quantum DXi as a backup repository, you must configure a Quantum DXi share. For more information, see [Quantum DXi](deduplicating_appliance_quantum.md).

Fujitsu ETERNUS CS800

* Fujitsu ETERNUS CS800 must meet software requirements. For more information, see [System Requirements](system_requirements.md#target).

* To use Fujitsu ETERNUS CS800 as a backup repository, you must configure a Fujitsu share. For more information, see [Fujitsu ETERNUS CS800](fujitsu.md).

* Check vendor documentation dedicated to integration with Veeam. Some links you can find in [this Veeam KB article](https://www.veeam.com/kb1745#vendordocs).

Infinidat InfiniGuard

* Infinidat InfiniGuard must meet software requirements. For more information, see [System Requirements](system_requirements.md#target).

* To use Infinidat InfiniGuard as a backup repository, you must configure a Infinidat InfiniGuard share. For more information, see [Infinidat InfiniGuard](infinidat_infiniguard.md).

* Check vendor documentation dedicated to integration with Veeam. Some links you can find in [this Veeam KB article](https://www.veeam.com/kb1745#vendordocs).

Storage Appliances and Tapes

Storage appliances that are used to store backup data in filer (CIFS/NFS) or block device mode (iSCSI/FC/SAS) are not supported if the backup data is offloaded to tapes and is no longer stored directly on the filer/block device (Hierarchical Storage Management with Tape tier).

To offload data to tapes, make sure that:

* All of the backup data is stored on the appliance altogether (that is, all of the backup chains are stored on the appliance as a whole and not scattered across multiple devices) and only copies are stored on tapes.
* These appliances emulate a tape system (VTL) as an access protocol for.

Page updated 11/24/2025

Page content applies to build 13.0.1.1071
