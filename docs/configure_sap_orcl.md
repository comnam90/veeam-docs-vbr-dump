---
title: "Configuring Veeam Plug-In for SAP on Oracle"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configure_sap_orcl.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Configuring Veeam Plug-In for SAP on Oracle

In this article

When you configure Veeam Plug-In settings, you set up integration settings between the SAP on Oracle server, Veeam Backup & Replication server and backup repositories where backup files will be stored.

Veeam Plug-In uses the SapOracleBackintConfigTool wizard to configure the integration settings. The wizard searches for all SAP on Oracle systems deployed on the server and creates the veeam\_initSID.sap file for each system. Then, this file is used as an initialization profile for brbackup, brrestore and brarchive tools.

Depending on the version of Oracle Database, Veeam Plug-In stores the configuration file in one of the following directories:

* For Oracle 12 and later, the configuration file is stored at SAPDATA\_HOME/sapprof.
* For Oracle 11, the configuration file is stored at ORACLE\_HOME/dbs.

|  |
| --- |
| Important |
| Veeam Plug-In may not be able to detect SAP instances during the configuration if the Oracle Database and SAP central instance are running on different hosts. If you work with Veeam Plug-In in the managed mode, this configuration is not supported. If you work with Veeam Plug-In in the standalone operation mode, you can do the following:   1. Complete all the steps of the Veeam Plug-In configuration wizard described in the [Veeam Plug-In Configuration](#conf) section. As a result, Veeam Plug-In will create a new veeam\_initSID.sap initialization profile and save it in the /tmp/ directory. 2. Manually copy all lines from the new initialization profile to the default initialization profile. You can also specify the path to the veeam\_initSID.sap file in each BRBACKUP, BRRESTORE and BRARCHIVE command.   Note that this approach applies only for Veeam Plug-In in the standalone operation mode. To learn more about operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md#modes). |

Veeam Plug-In Configuration

To configure Veeam Plug-In, do the following:

|  |
| --- |
| Note |
| The configuration of Veeam Plug-In must be performed by a user with database administrator rights on the Oracle Database server. |

1. Log in to the Oracle Database server as a user with database administrator rights and run the following command to launch the Veeam Plug-In configuration tool. You do not need root privileges if you have configured group access as described in the [Permissions](permissions_sap_orcl.md) section.

|  |
| --- |
| SapOracleBackintConfigTool --wizard |

If you have extracted files form the .TAR.GZ archive, go to the /opt/veeam/VeeamPluginforSAPOracle folder and run the following command:

|  |
| --- |
| ./SapOracleBackintConfigTool --wizard |

1. Specify the DNS name or IP address of the Veeam Backup & Replication server that you want to use.

|  |
| --- |
| Enter backup server name or IP address: serv02.tech.local |

1. Specify the port which will be used to communicate with the Veeam Backup & Replication server. Default port: 10006.

|  |
| --- |
| Enter backup server port number: 10006 |

For details about other required ports, see [Ports](permissions_sap_orcl.md).

1. Specify credentials to authenticate against the Veeam Backup & Replication server.

|  |
| --- |
| Enter username: serv02\administrator  Enter password for serv02\administrator: |

|  |
| --- |
| Important |
| Consider the following:   * You can work with backups created by Veeam Plug-In only with the account used for creating the backups. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account.   For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).   * The account must have access permissions on the required backup repository. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Repositories](repository_permissions.md). |

1. If you connect to the specified Veeam Backup & Replication server for the first time, provide the following confirmations:

1. Review the Veeam Backup & Replication server fingerprint and press y to confirm the connection to the specified server.

|  |
| --- |
| Veeam Backup & Replication server fingerprint: XX986XX6X6106XXXXX765X574X72X5X11502XXX8 |

1. Review requirements for the credentials and press y to confirm the connection using the specified credentials.

|  |
| --- |
| Please ensure the following roles are assigned to the user in Users and Roles settings on the backup server: Backup Administrator, or Backup Operator and Restore Operator  Alternatively, select a backup repository that does not have existing application backups created from this server under another user account.  Proceed anyway? (y/n): |

|  |
| --- |
| Tip |
| If you want to skip this step when connecting to the Veeam Backup & Replication server for the first time, you can disable it. For details, see [Configuration Tool Parameters](#disable). |

1. Select a backup repository where you want to store backups.

In the wizard dialog, you will see a list of available repositories. Enter the number of the target repository from the list.

|  |
| --- |
| Available backup repositories:  1. serv10\_repo |

|  |
| --- |
| Important |
| The account used to connect to the Veeam Backup & Replication server must have access to the target backup repositories. Otherwise, backup repositories will not be listed as available. To learn how to configure access on repositories, see [Access and Encryption Settings on Repositories](repository_permissions_sap_orcl.md). |

1. Specify the number of parallel data streams for each backup repository.

|  |
| --- |
| Enter number of data streams (From 1 to 32) to run in parallel: 4    Configuration result:  An auxiliary initialization profile has been successfully created for SAP system "ODB": /oracle/ODB/sapprof/veeam\_initODB.sap  The created profile must be leveraged to perform backup and restore tasks by BR\*Tools. |

Note that this parallelism setting applies only to backup and restore of Oracle datafiles. If you want to configure parallel channels for backup and restore of redo logs, see [Configuring Parallelism for Redo Logs](sap_orcl_parallelism.md).

Configuration Tool Parameters

Apart from running a configuration wizard, you can use the SapOracleBackintConfigTool tool to change a specific parameter in the veeam\_config.xml file or enable/disable Veeam Plug-In features.

|  |
| --- |
| Important |
| When you work with the command-line tool, use one configuration parameter per command. The tool does not support commands with multiple parameters. |

The following table lists available parameters for SapOracleBackintConfigTool.

| Parameter | Description |
| --- | --- |
| --help | Shows the list of tool parameters. |
| --show-config | Shows configuration parameters. |
| --wizard | Starts the wizard to configure the plug-in settings. The wizard edits the Veeam Plug-In configuration file (veeam\_config.xml) or creates a new one if the configuration file was removed from the /opt/veeam/VeeamPluginforSAPOracle directory on the machine where Veeam Plug-In is installed. |
| --set-credentials <"serv\username"> <password> | Specifies credentials to log in to the Veeam Backup & Replication server. |
| --set-host <hostname> | Specifies the IP address or hostname of the Veeam Backup & Replication server. |
| --set-port <port\_number> | Specifies a port number that will be used to communicate with the Veeam Backup & Replication server. |
| --set-repository | Launches a wizard to select a backup repository. A backup repository is selected from repositories which are available in the connected Veeam Backup & Replication instance. |
| --set-backup-for-restore | [For System Copy] Specifies the backup that will be used for restore operations. You can use this parameter if you want to restore a database to another server or to restore a database from a backup copy.  When you run the SapBackintConfigTool command with this parameter, Veeam Plug-In will prompt you to select an authentication method to access a backup created for the original server and then select the backup from which you want to restore a database.  For more information, see [Restore to Another Server (System Copy)](restore_sap_orcl_other_server.md). |
| --map-backup | Maps the imported backup. |
| --set-force-delete | Deletes backup files after specified days. |
| --promote-backup-copy-to-primary | Maps the imported backup copy to a regular Veeam Plug-In backup chain. |
| --set-parallelism <number\_of\_channels> | Define the number of parallel channels that must be used to transfer Oracle datafiles during the backup and restore operations.  You can set up to 32 channels.  Note that the parallelism for redo logs is configured separately. For details, see [Configuring Parallelism for Redo Logs](sap_orcl_parallelism.md). |
| --disable-fingerprint-confirmation | Use the --disable-fingerprint-confirmation parameter only with the --set-credentials parameter.  Disables a step of the Veeam Plug-In configuration process intended to confirm the first connection to the Veeam Backup & Replication server. During this step, Veeam Plug-In provides a fingerprint for the server for the user review. |
| --show-preferred-networks | Shows the list of preferred networks set for Veeam Plug-In data traffic to the remote backup repository.  The list shows set preferred networks in descending order of priority. If the list is empty, no networks are set as preferred and Veeam Plug-In routes data traffic to the preferred networks set in Veeam Backup & Replication. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](preferred_network_sap_orcl.md). |
| --add-preferred-network <network\_IP\_address> <position\_in\_list> | Adds a network to the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository.  To select to which network Veeam Plug-In connects first, you can set the order number of the network in the list. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](preferred_network_sap_orcl.md). |
| --remove-preferred-network <network\_IP\_address> | Removes a specified network from the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository. |

Example

The following example shows how to specify credentials that will be used to log in to the Veeam Backup & Replication server.

|  |
| --- |
| SapOracleBackintConfigTool --set-credentials "serv02\Administrator" "password" |

Page updated 12/3/2025

Page content applies to build 13.0.1.1071
