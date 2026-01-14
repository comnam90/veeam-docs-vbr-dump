---
title: "Merging Licenses"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/license_merge.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Merging Licenses

In this article

Merging licenses is an option for customers who have a Perpetual Socket license. If you have a Perpetual Socket license, and want to also protect, for example, your cloud or physical workloads, or work with Veeam Plug-Ins, you can obtain an instance license and merge it with the socket license.

|  |
| --- |
| Tip |
| Merging licenses is a built-in mechanism that allows you to merge two different license types (Socket and Instance). If you want to merge several licenses of the same type (Socket and Socket, Instance and Instance) to obtain a single license key file, you can use the merge tool in the Customer Portal. For more information on merging licenses in the Customer Portal, see [this Veeam KB article](https://www.veeam.com/kb3116). For more information on merge rules and exceptions for the Customer Portal merging process, see the [License Key Merge](https://www.veeam.com/licensing-policy.html) section of the Veeam Licensing Policy. |

Under the merged license, the following workloads will consume a Socket license:

* VMware vSphere and Microsoft Hyper-V VMs
* Application servers protected by Veeam Plug-Ins (only for application servers running in VMs of a virtual infrastructure registered with Veeam Backup & Replication)
* VMs protected by Veeam Agents (only for VMs of a virtual infrastructure registered with Veeam Backup & Replication)

Other workloads are processed per instance.

License Types Available for Merging

You can merge licenses of the following types:

* Perpetual Socket license and Subscription Instance license
* Perpetual Socket license and Perpetual Instance license

License Packages Available for Merging

You can merge licenses of the following packages:

| Type of license | Essentials | Backup | Suite Socket | ONE Socket |
| --- | --- | --- | --- | --- |
| Essentials Instance | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) |
| Backup Instance | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/no.webp) |
| Suite Instance | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/yes.webp) | ![Merging Licenses](images/no.webp) |
| ONE Instance | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) | ![Merging Licenses](images/no.webp) |

Support Terms in Merged Licenses

If the licenses that you want to merge have different support expiration date, the merged license will take the support that expires first.

Merging Licenses

Before you merge licenses, check the following prerequisites:

* The license type and package allow merging.
* The company names are identical in both licenses. Company name check is case sensitive.

To merge licenses, install a new license over the already installed license. For more information, see [Installing License](install_license.md).

|  |
| --- |
| Important |
| If the license types do not allow merging, the newly installed license will replace the previous license. |

Splitting Licenses

To split licenses, contact [Veeam Customer Support](https://www.veeam.com/support.html).

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
