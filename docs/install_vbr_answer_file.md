---
title: "Installing Veeam Backup & Replication in Silent Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/install_vbr_answer_file.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Installing Veeam Backup & Replication in Silent Mode


You can install Veeam Backup & Replication in the silent automated mode with a special XML answer file by using the command line interface. The answer file contains all the necessary installation settings in the proper order and their thorough description.

Before You Begin

Before starting the installation of Veeam Backup & Replication in the unattended mode with the answer file, consider the following:

* The user account that you use to run the silent installation must be in the local Administrators group on the machine where the silent installation will run. The silent installation cannot be run under the LocalSystem and NetworkService accounts.
* If the user account that you use to run the unattended installation is logged on the machine using the [network logon](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-logon-scenarios#BKMK_NetworkLogon) method, the unattended installation will fail. To avoid this, use an additional /SkipNetworkLogonErrors command line key. For example, it is required when the unattended installation is started within a remote PowerShell session.
* When configuring the answer file, remove or comment out unused [Optional] parameters. Otherwise, the installation session will fail.

Installing Veeam Backup & Replication

To install Veeam Backup & Replication in the silent mode with the answer file, take the following steps:

1. Copy the VbrAnswerFile\_install.xml file to your local drive.

You can find the template answer file on the Veeam Backup & Replication installation disk in the \Setup\Silent\AnswerFiles\VBR folder. This folder contains the following templates of answer files used for installing, uninstalling, and upgrading Veeam Backup & Replication:

* VbrAnswerFile\_install.xml — for installing Veeam Backup & Replication
* VbrAnswerFile\_uninstall.xml — for uninstalling Veeam Backup & Replication
* VbrAnswerFile\_upgrade.xml — for upgrading Veeam Backup & Replication

1. Configure installation parameters according to your needs. For details, see [Configuration Parameters](#ConfigurationParameters).

Check that the answer file has the correct bundle (Vbr) and mode (install) specified in line 2:

|  |
| --- |
| <unattendedInstallationConfiguration bundle="Vbr" mode="install" version="1.0"> |

1. After you make all the necessary changes in your answer file, start the installation by running the Veeam.Silent.Install.exe file located on the Veeam Backup & Replication installation disk in the \Setup\Silent folder. Use the following command line keys in your installation command:

|  |
| --- |
| D:\Setup\Silent\Veeam.Silent.Install.exe /AnswerFile E:\MyAnswerFileVBRInstall.xml /SkipNetworkLogonErrors |

where:

* /AnswerFile — required key for specifying the path to your custom answer file, for example: E:\MyAnswerFileVBRInstall.xml.
* /SkipNetworkLogonErrors — optional key that allows skipping additional pre-installation validations that do not work under the network logon, which will block the silent installation from running.
* /LogFolder — optional key for specifying the path where the setup should save log files if it is different from the default path. The default path is: C:\ProgramData\Veeam\Setup\Temp.

Configuration Parameters

The configuration file contains the following parameters:

| Parameter | Required? | Default | Description |
| --- | --- | --- | --- |
| ACCEPT\_EULA | Yes |  | Specify 1 to accept the Veeam license agreement. |
| ACCEPT\_LICENSING\_POLICY | Yes |  | Specify 1 to accept the Veeam licensing policy. |
| ACCEPT\_THIRDPARTY\_LICENSES | Yes |  | Specify 1 to accept the license agreement for 3rd party components that Veeam incorporates. |
| ACCEPT\_REQUIRED\_SOFTWARE | Yes |  | Specify 1 to accept all required software license agreements. |
| VBR\_LICENSE\_FILE | No |  | Specify the path to the license file on the machine where you want to install Veeam Backup & Replication. If you do not specify this parameter (or leave it empty value), Veeam Backup & Replication will be installed using the current license file. To install the Community Edition, set the parameter to 0. |
| VBR\_LICENSE\_AUTOUPDATE | No | 1 | Specify 1 to enable automatic license update and usage reporting. Specify 0 if you want to update the license manually. For Community Edition, NFR and Evaluation licenses, specify 1. For licenses without ID information, specify 0. |
| VBR\_SERVICE\_USER | No |  | Specify the user account under which the Veeam Backup Service will run. If you do not specify this parameter, the service will run under the LocalSystem account. |
| VBR\_SERVICE\_PASSWORD | No |  | Specify the password for the account under which the Veeam Backup Service will run. |
| VBR\_SQLSERVER\_INSTALL | Yes | 1 | Specify 0 to use an existing SQL server instance or specify 1 to create a new SQL server instance. |
| VBR\_ENTRAID\_DATABASE\_INSTALL | No | 1 | Specify 1 to install a bundled PostgreSQL server for the Microsoft EntraID backup functionality. If set to 0, PostgreSQL database will not be installed for Microsoft EntraID backup. |
| VBR\_SQLSERVER\_ENGINE | No | 1 | Specify 1 to use PostgreSQL engine or specify 0 to use Microsoft SQL engine. Note that if you want to create a new SQL server instance, you can only choose the PostgreSQL engine, that is, set the parameter to 1. |
| VBR\_SQLSERVER\_SERVER | No | localhost:5432 | Specify the SQL server and instance (for Microsoft SQL) or the SQL server and port (for PostgreSQL) to be used for deploying the configuration database. Note that if you want to create a new SQL instance, you can only connect to a local host. |
| VBR\_SQLSERVER\_DATABASE | No | VeeamBackup | Specify a configuration database name. If you do not specify this parameter, the default VeeamBackup name is used. |
| VBR\_SQLSERVER\_AUTHENTICATION | No | 0 | Specify the authentication mode to connect to the SQL Server where the Veeam Backup & Replication configuration database is deployed. Specify 1 to use the SQL Server authentication mode or specify 0 to use the Microsoft Windows authentication mode. |
| VBR\_SQLSERVER\_USERNAME | No |  | Specify the LoginID to connect to the SQL Server in the SQL Server authentication mode. |
| VBR\_SQLSERVER\_PASSWORD | No |  | Specify the password to connect to the SQL Server in the SQL Server authentication mode. |
| VBRC\_SERVICE\_PORT | No | 9393 | Specify the TCP port to be used by the Veeam Guest Catalog Service. If you do not specify this parameter, the default 9393 port is used. |
| VBR\_SERVICE\_PORT | No | 9392 | Specify the TCP port to be used by the Veeam Backup Service. If you do not specify this parameter, the default 9392 port is used. If the specified port number is already occupied, the setup will assign the next available port number to the component. |
| VBR\_SECURE\_CONNECTIONS\_PORT | No | 9401 | Specify the TCP port to be used for communication between the mount server and the backup server. If you do not specify this parameter, the default 9401 port is used. |
| VBR\_RESTSERVICE\_PORT | No | 9419 | Specify the TCP port to be used for communication with REST API service. If you do not specify this parameter, the default 9419 port is used. |
| INSTALLDIR | No | %ProgramFiles%\Veeam\Backup and Replication | Specify the path to the directory where Veeam Backup & Replication will be installed. If you do not specify this parameter, the default %ProgramFiles%\Veeam\Backup and Replication installation path is used. |
| VM\_CATALOGPATH | No | C:\VBRCatalog | Specify the path to the catalog folder where index files will be stored. If you do not specify this parameter, a path is selected based on the free space across all available disks. |
| VBR\_IRCACHE | No | C:\ProgramData\Veeam\Backup\IRCache | Specify the path to the folder where the instant recovery cache will be stored. If you do not specify this parameter, a path is selected based on the free space across all available disks. |
| VBR\_CHECK\_UPDATES | No | 1 | Specify 1 to automatically check for new product versions and updates. Specify 0 if you do not want Veeam Backup & Replication to check for updates automatically. |
| AHV\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Nutanix AHV. Specify 0 if you do not want to install the plugin. |
| KVM\_INSTALL | No | 1 | Specify 1 if you want to install oVirt KVM Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| PVE\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Proxmox VE. Specify 0 if you do not want to install the plugin. |
| SCP\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Plug-In for Scale Computing HyperCore. Specify 0 if you do not want to install the plugin. |
| AWS\_INSTALL | No | 1 | Specify 1 if you want to install AWS Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| AZURE\_INSTALL | No | 1 | Specify 1 if you want to install Microsoft Azure Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| KASTEN\_INSTALL | No | 1 | Specify 1 if you want to install Veeam Kasten Plug-In for Veeam Backup & Replication. Specify 0 if you do not want to install the plugin. |
| REBOOT\_IF\_REQUIRED | No | 0 | Specify 1 if you want to reboot the machine where you install Veeam Backup & Replication after the installation finishes. Specify 0 if you do not want to reboot the machine. |

Note that you must specify "1" in ACCEPT\_EULA, ACCEPT\_LICENSING\_POLICY, ACCEPT\_THIRDPARTY\_LICENSES and ACCEPT\_REQUIRED\_SOFTWARE parameters to proceed with the installation.

Installation Result Codes

The installation result is written into the installation log file located at your selected log folder. It may show one of the following result codes:

| Result Code | Result |
| --- | --- |
| 0 | success |
| 1603 | install failure |
| 3010 | reboot required |
| 3011 | logoff required |

Installation Error Codes

The installation error codes accompanied by their detailed description are displayed in the command line dialog. They can also be found in the UnattendedInstallationResult\_%DATE%\_%TIME%.xml file in the log folder (by default, C:\ProgramData\Veeam\Setup\Temp). You can use such an XML file for retrieving installation results from the scripts or utilities that are used to run the installation. The error message may show one of the following error codes:

| Error Code | Description |
| --- | --- |
| 0 | Installation has been completed successfully. |
| 1 | Product is already installed. |
| 2 | Uninstallation has been completed successfully. |
| 11 | Unable to start the setup program, because machine reboot is pending. |
| 12 | Reboot is required to finalize prerequisites installation. |
| 13 | Reboot is required to finalize the product installation. |
| 14 | Logoff is required to finalize the product installation. |
| 101 | Failed to start the installer. |
| 102 | Invalid answer file provided. |
| 103 | Invalid launch conditions. |
| 104 | Failed to initialize setup properties. |
| 105 | Failed to validate setup properties. |
| 106 | System configuration check detected some issues. |
| 107 | Failed to install prerequisites. |
| 108 | Failed to install a database server. |
| 109 | Failed to install the product. |
| 110 | Failed to update the product. |
| 111 | Failed to change a service status. |
| 112 | Failed to uninstall the product. |
| 113 | Unexpected error occurred. |


