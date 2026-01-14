---
title: "Upgrading Plug-In for SAP HANA"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_saphana_plugin.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Upgrading Plug-In for SAP HANA

In this article

Periodically, Veeam releases a new version of Veeam Backup & Replication that contains new features and bug fixes. The release package also contains a new version of Veeam Plug-Ins.

Veeam Backup & Replication 13 supports different versions of Veeam Plug-In depending on which OS is running on the backup server:

* Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported.
* Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.

Note that Veeam Backup & Replication must be the same or later than the version of Veeam Plug-In. If you want to use the latest functionality, you must upgrade both Veeam Backup & Replication and Veeam Plug-In to the latest version. If you use an earlier Veeam Plug-In build, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474).

|  |
| --- |
| Important |
| Consider the following:   * You must upgrade Veeam Backup & Replication before you upgrade Veeam Plug-Ins. To learn how to upgrade Veeam Backup & Replication, see [Upgrade and Update](vbr_updating.md).  * Operations in the terminal of the Linux machine require root privileges. * If you want to upgrade Veeam Plug-In for SAP HANA scale-out cluster, repeat the described upgrade process on all cluster nodes. |

Before You Begin

Veeam Plug-In installation files are included in the installation image of Veeam Backup & Replication and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins). You must get the installation files on the SAP HANA server. To do this, perform the following steps:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. [For Linux] In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\SAP HANA\x64 folder, find the Veeam Plug-In installation file that suits your OS.

1. Upload packages that you need to the SAP HANA server.

Using veeam.com

1. Download the current setup archive for Veeam Plug-In for SAP HANA from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. [For Linux] In the \VeeamPluginForSAPHANA-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForSAPHANA-13.0.1.180\x64 folder, find the Veeam Plug-In installation file that suits your OS.

1. Upload packages that you need to the SAP HANA server.

After you uploaded the files, you can upgrade Veeam Plug-In. The upgrade procedure depends on the type of package and OS that you use:

* [Upgrading Plug-In on Linux (.RPM)](#rpm)
* [Upgrading Plug-In on Linux (.TAR.GZ)](#tar)

Upgrading Plug-In on Linux (.RPM)

To upgrade Veeam Plug-In for SAP HANA from the .RPM package, perform the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm packages to the SAP HANA server.
2. To upgrade Veeam Plug-In, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Upgrade Veeam Plug-In:

|  |
| --- |
| rpm -U VeeamPluginforSAPHANA-13.0.1.180-1.x86\_64.rpm |

|  |
| --- |
| Tip |
| To find out which version of Veeam Plug-In is installed on your server, you can use the following command: rpm -qa | grep VeeamPlugin |

Upgrading Plug-In on Linux (.TAR.GZ)

To upgrade Veeam Plug-In for SAP HANA on a Linux machine from the .TAR.GZ archive, do the following:

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforSAPHANA.tar.gz files to the SAP HANA server.
2. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. In the terminal, open the folder that contains the VeeamPluginforSAPHANA.TAR.GZ archive.
2. Unpack the plug-in files from the archive to the /opt/veeam directory. Old Veeam Plug-In files will be replaced by new files.

|  |
| --- |
| tar -xzvf VeeamPluginforSAPHANA.tar.gz -C /opt/veeam |

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
