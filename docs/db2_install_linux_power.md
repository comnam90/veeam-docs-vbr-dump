---
title: "Installing Plug-In for Linux on Power"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_install_linux_power.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In for Linux on Power

In this article

Veeam Plug-In for IBM Db2 for Linux on Power is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

You can install the plug-in using the .RPM package or extract the plug-in files from the .TAR.GZ archive. Depending on the type of package suitable for your OS, perform steps in one of the following subsections:

* [Installing Plug-In from .RPM Package](#rpm)
* [Installing Plug-In from .DEP Package](#dep)
* [Unpacking Plug-In from .TAR.GZ Archive](#tar)

|  |
| --- |
| Important |
| Keep in mind the following:   * IBM Db2 must be installed on the machine. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install the plug-in, use the sudo command or a user with root privileges.  * If you want to install Veeam Plug-In scale-out cluster, repeat the described installation process on all cluster nodes. |

Installing Veeam Plug-In from .RPM Package

To install Veeam Plug-In on a Linux on Power machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the Plugins\IBM Db2\Linux\ppc64le folder, find the VeeamPluginforDB2-13.0.1.180-1.ppc64le.rpm package.

1. Upload the VeeamPluginforDB2-13.0.1.180-1.ppc64le.rpm package to the machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\ppc64le folder, find the VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm package.

1. Upload VeeamPluginforDB2-13.0.1.180-1.ppc64le.rpm package to the machine with IBM Db2.

1. Install Veeam Plug-In with the following command:

|  |
| --- |
| rpm -i VeeamPluginforDB2-13.0.1.180-1.ppc64le.rpm |

Installing Veeam Plug-In from .DEB Package

To install Veeam Plug-In on a Linux on Power machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the Plugins\IBM Db2\Linux\ppc64le folder, find the VeeamPluginforDB2-13.0.1.180-1.ppc64le.deb package.

1. Upload the VeeamPluginforDB2\_13.0.1.180-1\_ppc64le.deb package to the machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\ppc64le folder, find the VeeamPluginforDB2-13.0.1.180-1.ppc64le.deb package.
3. Upload the VeeamPluginforDB2\_13.0.1.180-1\_ppc64le.deb package to the machine with IBM Db2.

1. Install Veeam Plug-In with the following command:

|  |
| --- |
| apt-get install VeeamPluginforDB2\_13.0.1.180-1-ppc64le.deb |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).

Unpacking Veeam Plug-In from .TAR.GZ Archive

To extract plug-in files from the .TAR.GZ archive, perform the following:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. In the \Plugins\IBM Db2\Linux\ppc64le folder, find the VeeamPluginforDB2.tar.gz archive.
2. Upload the VeeamPluginforDB2.tar.gz archive to the machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\ppc64le folder, find the VeeamPluginforDB2.tar.gz archive.
3. Upload the VeeamPluginforDB2.tar.gz archive to the machine with IBM Db2.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Create the /opt/veeam directory.

|  |
| --- |
| mkdir /opt/veeam |

1. In the terminal, open the folder that contains the VeeamPluginforDB2.TAR.GZ archive.
2. Unpack the plug-in files from the archive to the /opt/veeam directory.

|  |
| --- |
| tar -xzvf VeeamPluginforDB2.tar.gz -C /opt/veeam |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
