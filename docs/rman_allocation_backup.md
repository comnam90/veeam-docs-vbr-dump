---
title: "Oracle RMAN Channel Allocation"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_allocation_backup.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Oracle RMAN Channel Allocation

In this article

You can manually allocate RMAN channels by using the ALLOCATE CHANNEL command. This approach helps optimize backup operations and resource allocation. Specify the Veeam backup repository universal unique identifier (UUID) in the channel parameters to direct backup operations to the intended backup repository.

|  |
| --- |
| Important |
| Keep in mind that the ALLOCATE CHANNEL command must be issued only within a RUN block for a specific backup operation. |

To manually allocate RMAN channels, do the following:

1. Open the RUN block.
2. Use the ALLOCATE CHANNEL command and specify the following parameters:

1. Specify the channel ID. For example: ch1.
2. Specify the SBT\_TAPE option for the DEVICE TYPE parameter.
3. Specify PARMS to define other parameters for the sbt\_tape channel.
4. Specify which media library must be used for this sbt\_tape channel.

* [For Linux and Unix] Set the path to the libOracleRMANPlugin.so file as the SBT\_LIBRARY.
* [For Microsoft Windows] Set the path to %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\OracleRMANPlugin.dll.

1. Specify the Veeam backup repository UUID in the argument for the FORMAT parameter. You can find the required backup repository UUID in the rman\_config.txt file or in log files.

* [For Linux and Unix] If you have exported Veeam Plug-In configuration files, run the following command to see the contents of the configuration file.

|  |
| --- |
| cat /tmp/rman\_config.txt |

Alternatively, you can find the repository UUID in log files:

|  |
| --- |
| grep "received repos" /tmp/veeam\_plugin\_logs/oracle/OracleRMANConfigTool.log | tail |

* [For Microsoft Windows] If you have exported Veeam Plug-In configuration files, find the channel allocation definition in the configuration file.

Alternatively, you can find the repository UUID in log files. Go to the %\ProgramData\Veeam\Backup\RmanPluginLogs\SERV\_NAME directory and search for "received repos id" in the OracleRMANConfigToolLib.log file.

1. Use the BACKUP DATABASE command to create a database backup.
2. [Optional] Use the RELEASE CHANNEL command. By default, RMAN automatically releases all channels when the RUN command terminates.
3. Close the RUN block.

To learn more about channel allocation, see [Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/21/rcmrf/ALLOCATE-CHANNEL.html#GUID-9320BFF7-0728-4B3D-85B9-2184557ECDCE).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Allocating Single Channel for Backup Operations

|  |  |
| --- | --- |
| In this example, the RUN block contains the following commands:   * ALLOCATE CHANNEL: this command allocates channel ch1 to the Veeam backup repository with UUID d8338780-1aec-4c36-b17c-e1ea3ea2ca93. * BACKUP DATABASE: this command backs up the specified database. * RELEASE CHANNEL: this command releases the allocated channel ch1 to optimize resources.   |  | | --- | | RUN {      ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE        PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT 'd8338780-1aec-4c36-b17c-e1ea3ea2ca93/RMAN\_%I\_%d\_%T\_%U.vab';      BACKUP DATABASE;      RELEASE CHANNEL ch1;  }  EXIT; | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Allocating Multiple Channels for Backup Operations

|  |  |
| --- | --- |
| In this example, the RUN block contains the following commands:   * ALLOCATE CHANNEL: this command allocates channels ch1 and ch2 simultaneously to the Veeam backup repository with UUID d8338780-1aec-4c36-b17c-e1ea3ea2ca93. * BACKUP DATABASE: this command backs up the specified database. * RELEASE CHANNEL: this command releases the allocated channels ch1 and ch2 to optimize resources.   |  | | --- | | RUN {      ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE        PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT 'd8338780-1aec-4c36-b17c-e1ea3ea2ca93/RMAN\_%I\_%d\_%T\_%U.vab';      ALLOCATE CHANNEL ch2 DEVICE TYPE SBT\_TAPE        PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT 'd8338780-1aec-4c36-b17c-e1ea3ea2ca93/RMAN\_%I\_%d\_%T\_%U.vab';      BACKUP DATABASE;      RELEASE CHANNEL ch1;      RELEASE CHANNEL ch2;  }  EXIT; | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Allocating Single Channel and Using Multiple Repositories for Backup Operations

|  |  |
| --- | --- |
| In this example, the RUN block contains the following commands:   * ALLOCATE CHANNEL: this command allocates channel ch1 to two Veeam backup repositories with UUIDs d8338780-1aec-4c36-b17c-e1ea3ea2ca93 and 4f85d62e-bd3c-46da-9cdd-53873faf4214 simultaneously. * BACKUP DATABASE: this command backs up the specified database. * RELEASE CHANNEL: this command releases the allocated channel ch1 to optimize resources.   |  | | --- | | RUN {       ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE        PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT 'd8338780-1aec-4c36-b17c-e1ea3ea2ca93/RMAN\_%I\_%d\_%T\_%U.vab','4f85d62e-bd3c-46da-9cdd-53873faf4214/RMAN\_%I\_%d\_%T\_%U.vab';      BACKUP DATABASE;      RELEASE CHANNEL ch1;  }  EXIT; | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Allocating Single Channel for Backup Operations in Microsoft Windows Environment

|  |  |
| --- | --- |
| In this example for Microsoft Windows environments, the RUN block contains the following commands:   * ALLOCATE CHANNEL: this command allocates channel ch1 to the Veeam backup repository with UUID d8338780-1aec-4c36-b17c-e1ea3ea2ca93. * BACKUP DATABASE: this command backs up the specified database. * RELEASE CHANNEL: this command releases the allocated channel ch1 to optimize resources.   |  | | --- | | RUN {     ALLOCATE CHANNEL ch1 DEVICE TYPE SBT\_TAPE       PARMS 'SBT\_LIBRARY=%PROGRAMFILES%\Veeam\VEEAMP~2\ORACLE~2.DLL' FORMAT 'd8338780-1aec-4c36-b17c-e1ea3ea2ca93/RMAN\_%I\_%d\_%T\_%U.vab';     BACKUP DATABASE;     RELEASE CHANNEL ch1;  }  EXIT; | |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
