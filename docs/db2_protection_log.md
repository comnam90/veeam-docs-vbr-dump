---
title: "Performing Log Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_log.html"
last_updated: "4/24/2026"
product_version: "13.0.1.2067"
---

# Performing Log Backup


Veeam Plug-In for IBM Db2 supports backup and restore operations of archived logs for IBM Db2 databases. Archive logs contain all transactional changes to enable recovery and point-in-time restores. Set the logarchmeth1 parameter during the configuration of Veeam Plug-In for IBM Db2 to specify the log method and storage destination of archive logs.

You can also set the logarchmeth2 parameter in IBM Db2 databases to specify a secondary archive log method or location. Configure this parameter in addition to setting the logarchmeth1 parameter.

There are two approaches for processing archive logs with Veeam Plug-In for IBM Db2:

* Automatic log processing: Veeam Backup & Replication manages archived log processing automatically and transfers the logs to a Veeam backup repository.

Once the primary database archive method is configured with the logarchmeth1 parameter and an online backup is performed, Veeam Plug-In for IBM Db2 automatically processes and transfers archived logs to the selected backup repository. The Veeam Backup & Replication job configuration controls the log backup frequency and retention. For more information on how to set the logarchmeth1 parameter automatically, see [Configuring Plug-In](db2_configure.md#archive_log).

* Manual log processing: IBM Db2 commands allow manual archiving and transferring of logs to a configured destination.

Manual log processing is an optional action available after the setup of Veeam Plug-In for IBM Db2. By default, automatic log processing is always active unless specifically disabled or modified. Manual log backup or intervention may be required in custom configurations or troubleshooting scenarios. You can archive or copy logs manually using IBM Db2 commands. For more information on how to set the logarchmeth1 and logarchmet2 parameters manually, see [Performing Manual Archive Log Backup](#manual).

|  |
| --- |
| Note |
| You must set Veeam Plug-In to use the logarchmeth1 parameter to enable and run online backups. Otherwise, only offline backups are possible.  If you do not set the logarchmeth1 parameter in the configuration wizard, Veeam Plug-In will do the following, based on the current value of the parameter:   * If logarchmeth1 was already set to Veeam Plug-In, Veeam Plug-In will set it to off for all databases on the host. * If logarchmeth1 is set to a different value, Veeam Plug-In will not modify the parameter. |

Configuring Archive Log Methods

To specify the method and location for archiving database logs, you must use the logarchmeth1 parameter.

* Automatic configuration: During the configuration of Veeam Plug-In for IBM Db2, the setup wizard automatically sets logarchmeth1 to direct logs to the Veeam backup repository. For more information, see [Configuring Plug-In](db2_configure.md#archive_log).
* Manual configuration: You can set logarchmeth1 and logarchmeth2 using IBM Db2 commands.

Performing Manual Archive Log Backup

Manually archive database logs using IBM Db2 commands in the following scenarios:

* To archive all recent transactions before a backup operation.
* To test archive log configuration.
* During troubleshooting or active log processing.

|  |
| --- |
| Note |
| You must configure logarchmeth1 or logarchmeth2 parameters before using the db2 archive log for db <db\_alias> command. Based on this configuration, IBM Db2 sends the archived logs to the specified location.  Manual archive log backup does not replace automatic log backup managed by Veeam Plug-In for IBM Db2. This command only archives the current log file. |

To manually archive the active log file, do the following on the machine running IBM Db2:

1. Log in to the machine using a user account with root or instance owner privileges.
2. Connect to the database instance environment.
3. Run the following command. Replace <db\_alias> with the actual database name.

|  |
| --- |
| db2 archive log for db <db\_alias> |

For example:

|  |
| --- |
| db2 archive log for db db1 |

1. Confirm that the logarchmeth1 parameter is configured correctly.

|  |
| --- |
| db2 GET DATABASE CONFIGURATION FOR db1 |

This command displays database configuration settings. Verify that logarchmeth1 is set to the expected value.

1. Check the archive log backup history to confirm that the log was archived.

|  |
| --- |
| db2 list history archive log all for <db\_alias> |

The output lists archived log entries and their Location. The Location should show Veeam Plug-In for IBM Db2 as the archive destination.

|  |
| --- |
| Note |
| The archive log history confirms that IBM Db2 archived the log file. It does not confirm that the log was successfully transferred to the Veeam Backup & Replication backup repository. To verify that the log backup completed in Veeam Backup & Replication, do one of the following:   * Check the action log of the plug-in job in Veeam Backup & Replication. * Check the Veeam Backup & Replication configuration database. * Perform a restore of the archived log. |

Setting Additional Database Archive Log Configuration

You can use the logarchmeth2 parameter in IBM Db2 databases to specify a secondary archive log method or location. Set this parameter in addition to the primary method defined by logarchmeth1.

To set the logarchmeth2 parameter, do the following on the machine running IBM Db2:

1. Log in to the machine using a user account with root or instance owner privileges.
2. Run the following command to set the logarchmeth2 parameter:

|  |
| --- |
| db2 update database configuration for <db\_name> using logarchmeth2 <value> |

where:

* <db\_name> is the required database name.
* <value> is the required archive log method or location.

For example:

|  |
| --- |
| db2 update database configuration for db1 using logarchmeth2 C:/archive/secondary |

1. Run the following command to verify the new value:

|  |
| --- |
| db2 get database configuration for <db\_name> |

This command displays the updated logarchmeth2 setting.

|  |
| --- |
| Note |
| The value for logarchmeth2 must be compatible with your backup and recovery requirements.  If you use Veeam Plug-In for IBM Db2, ensure that the secondary archive method does not conflict with the backup configuration managed by Veeam Backup & Replication. |


