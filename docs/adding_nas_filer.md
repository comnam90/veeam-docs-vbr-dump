---
title: "Adding Enterprise Storage System as NAS Filer"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/adding_nas_filer.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Adding Enterprise Storage System as NAS Filer

In this article

Before you add an enterprise storage system as a NAS filer to the inventory of the virtual infrastructure, consider the following:

* The NAS device meets requirements listed in section [Supported Platforms, Applications and Workloads](platform_support.md).
* If you plan to use a dedicated backup proxy or cache repository, make sure these components are added in Backup Infrastructure.
* When a storage virtual machine (SVM) has both the NFS and SMB protocols enabled, but the SVM does not export any NFS shares, file backup jobs configured to protect NFS file shares on that SVM fail. To fix this, either disable the NFS protocol on the SVM, or disable NFS protocol for the storage in Veeam Backup & Replication. You can do the latter by clearing the NFS check box at the NAS Filer step of the wizards described in the [Editing NetApp Data ONTAP](netapp_nas_access.md), [Editing Lenovo ThinkSystem DM/DG Series](specify_nas_access.md), [Editing Dell PowerScale (formerly Isilon)](dell_powerscale_add_options.md) or [Editing Nutanix Files Storage](nutanix_add_nas.md) sections.
* [For Microsoft Windows-based backup server] Native changed files tracking (SnapDiff v1) is not supported for NetApp ONTAP versions from 9.10.1 to 9.10.1P10.
* [For Microsoft Windows-based backup server] Native changed files tracking (SnapDiff v1) is not supported for NetApp ONTAP FlexGroup volumes.
* [For Linux-based backup server] If you plan to add NetApp Data ONTAP as a NAS filer, you must enable SnapDiff v3 beforehand. For information on how to enable SnapDiff v3, see [NetApp KB article](https://kb.netapp.com/on-prem/ontap/DP/SnapDiff/SnapDiff-KBs/How_to_enable_SnapDiff_in_ONTAP).

To add an enterprise NAS system as a source of unstructured data, do the following:

1. [Launch the New NAS Filer wizard](nas_filer_wizard_launch.md).
2. [Select a NAS device to use as a NAS filer](nas_filer_nas_device.md).
3. [Specify file share processing settings](nas_filer_processing.md).
4. [Apply file share settings](nas_filer_apply.md).
5. [Finish working with the wizard](nas_filer_summary.md).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
