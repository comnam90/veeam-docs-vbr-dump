---
title: "Installing Plug-In on Linux"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_install_linux.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Installing Plug-In on Linux


Veeam Plug-In for IBM Db2 is an additional component of Veeam Backup & Replication. The installation package of the plug-in is included in the Veeam Backup & Replication installation ISO file and available for download from [veeam.com](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).

|  |
| --- |
| Important |
| Keep in mind the following:   * IBM Db2 must be installed on the machine. * The /opt/veeam directory must be writable.  * The NOEXEC mount option must be disabled for the /var and /tmp directories.  * To install the plug-in, use the sudo command or a user with root privileges.  * If you want to install Veeam Plug-In scale-out cluster, repeat the described installation process on all cluster nodes. |

You can install Veeam Plug-In using the .RPM package, the .DEB package or extract the plug-in files from the .TAR.GZ archive. Installation steps depend on the type of installation file suitable for your OS:

* [Installing plug-in from .RPM package](#rpm)
* [Installing plug-in from .DEB package](#deb)
* [Unpacking plug-in from .TAR.GZ archive](#tar)

Installing Plug-In from .RPM Package

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. In the \Package folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\IBM Db2\Linux\x64 folder, find the VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm packages to the Linux machine with SAP MaxDB database.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for SAP MaxDB from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginForIBMDb2-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\x64 folder, find the VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm package.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm packages to the Linux machine with IBM Db2.

1. To install Veeam Plug-In, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Install Veeam Plug-In:

|  |
| --- |
| rpm -ivh VeeamPluginforDB2-13.0.1.180-1.x86\_64.rpm |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).

Installing Plug-In from .DEB Package

To install Veeam Plug-In on a Linux machine, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following packages:

1. In the \Packages folder, find the veeam-openssl3\_3.0.0.31\_amd64.deb package.
2. In the \Plugins\IBM Db2\Linux\x64 folder, find the VeeamPluginforDB2\_13.0.1.180-1\_amd64.deb package.

1. Upload veeam-openssl3\_3.0.0.31\_amd64.deb and VeeamPluginforDB2\_13.0.1.180-1\_amd64.deb packages to the Linux machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following packages:

1. In the \VeeamPluginForIBMDb2-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3\_3.0.0.31\_amd64.deb package.
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\x64 folder, find the VeeamPluginforDB2\_13.0.1.180-1\_amd64.deb package.

1. Upload veeam-openssl3\_3.0.0.31\_amd64.deb and VeeamPluginforDB2\_13.0.1.180-1\_amd64.deb packages to the Linux machine with IBM Db2.

1. To install Veeam Plug-In, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| apt-get install veeam-openssl3\_3.0.0.31\_amd64.deb |

1. Install Veeam Plug-In:

|  |
| --- |
| apt-get install VeeamPluginforDB2\_13.0.1.180-1\_amd64.deb |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).

Unpacking Plug-In from .TAR.GZ Archive

To extract plug-in files from the .TAR.GZ archive and install Veeam Plug-In, perform the following steps:

1. Export installation packages to the machine with a database that you plan to protect. You can do it in the following ways:

Using the Veeam Backup & Replication installation image

1. Mount the Veeam Backup & Replication installation image.

You can download the latest version of the Veeam Backup & Replication installation image from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html).

1. Open the mounted image and find the following files:

1. In the \Packages folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \Plugins\IBM Db2\Linux\x64 folder, find the VeeamPluginforDB2.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforDB2.tar.gz files to the Linux machine with IBM Db2.

Using veeam.com

1. Download the setup archive for Veeam Plug-In for IBM Db2 from [this Veeam webpage](https://www.veeam.com/products/data-platform-trial-download.html?tab=application-plugins).
2. Open the setup archive and find the following files:

1. In the \VeeamPluginForIBMDb2-13.0.1.180\veeam-openssl3 folder, find the veeam-openssl3-3.0.0.31-1.x86\_64.rpm package.
2. In the \VeeamPluginForIBMDb2-13.0.1.180\DB2Linux\x64 folder, find the VeeamPluginforDB2.tar.gz archive.

1. Upload veeam-openssl3-3.0.0.31-1.x86\_64.rpm and VeeamPluginforDB2.tar.gz files to the Linux machine with IBM Db2.

1. Install Veeam Plug-In. To do this, run the following commands:

1. Install the veeam-openssl3 package that is required for the Veeam Plug-In functioning:

|  |
| --- |
| rpm -i veeam-openssl3-3.0.0.31-1.x86\_64.rpm |

1. Create the /opt/veeam directory with the following command:

|  |
| --- |
| mkdir /opt/veeam |

|  |
| --- |
| Tip |
| The /opt/veeam directory is the default directory for the Veeam Plug-In installation. This directory is used in relevant command examples in this guide. |

1. Unpack Veeam Plug-In files from the archive to the /opt/veeam directory with the following command:

|  |
| --- |
| tar -xzvf VeeamPluginforDB2.tar.gz -C /opt/veeam |

Once Veeam Plug-In is installed, you must configure the plug-in settings. For details, see [Configuring Plug-In](db2_configure.md).


