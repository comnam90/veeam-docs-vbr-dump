---
title: "Antivirus Configuration File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/av_scan_xml.html"
last_updated: "12/15/2025"
product_version: "13.0.1.1071"
---

# Antivirus Configuration File


The antivirus software that you plan to use for scanning backups is described in the AntivirusInfos.xml file. By default, the file contains predefined settings for the following antivirus solutions:

* Microsoft Windows:

+ Sophos Endpoint Protection
+ Symantec Protection Engine
+ ESET Server Security (formerly ESET File Security)
+ ESET Security
+ Windows Defender
+ Bitdefender Endpoint Security Tools
+ Trellix (formerly McAfee)

* Linux:

+ ClamAV
+ Sophos Protection for Linux
+ ESET Server Security (formerly ESET File Security)

Veeam Backup & Replication creates the AntivirusInfos.xml file in the %ProgramFiles%\Common Files\Veeam\Backup and Replication\Mount Service folder or in the /var/lib/veeam/mount/AntivirusInfos.xml directory on every machine with the mount server role. During a Scan Backup or secure restore session, Veeam Backup & Replication reads settings from the file and triggers the antivirus to scan backup files. If you use several antivirus software on the mount server, Veeam Backup & Replication will trigger the antivirus whose configuration is defined first in the file.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)See the default configuration file

|  |
| --- |
| <Antiviruses>   <!-- ClamAV -->   <AntivirusInfo Type='Linux' Name='ClamAV' IsPortableSoftware='true' ExecutableFilePath='/usr/bin/clamscan' CommandLineParameters='-i -r %Path%' RegPath='' ServiceName='' ThreatExistsRegEx='FOUND$' IsParallelScanAvailable='false' OutputSupported='true'>     <ExitCodes>       <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>       <ExitCode Type='Infected' Description='Virus threat was detected'>1</ExitCode>       <ExitCode Type='Error' Description='An error occured'>2</ExitCode>     </ExitCodes>   </AntivirusInfo>   <!-- Sophos Windows -->   <AntivirusInfo Type='Windows' Name='Sophos' IsPortableSoftware='false' ExecutableFilePath='%ProgramFiles%\Sophos\Endpoint Defense\SophosInterceptXCLI.exe' CommandLineParameters='scan --noui %Path%' RegPath='HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\Sophos Endpoint Defense Service' ServiceName='Sophos Endpoint Defense Service' ThreatExistsRegEx='Detections:\s+[^0]\d\*' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <!-- https://docs.sophos.com/esg/endpoint/help/en-us/help/Scan-from-CLI/index.html#error-codes -->     <ExitCode Type='Success' Description='Scan finished'>0</ExitCode>     <ExitCode Type='Error' Description='Error during command handling or scan might have been interrupted'>1</ExitCode>     <ExitCode Type='Error' Description='Unexpected error during CLI setup'>2</ExitCode>       <ExitCode Type='Infected' Description="A threat was detected in one or more files">3</ExitCode>       <ExitCode Type='Warning' Description="One or more files encountered an error during the scan">4</ExitCode>       <ExitCode Type='Warning' Description="One or more files were encrypted">5</ExitCode>       <ExitCode Type='Warning' Description="One or more files have an unsupported format">6</ExitCode>       <ExitCode Type='Warning' Description="One or more files were inaccessible">7</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Sophos Linux -->   <AntivirusInfo Type='Linux' Name='Sophos' IsPortableSoftware='true' ExecutableFilePath='/opt/sophos-spl/plugins/av/bin/avscanner' CommandLineParameters='%Path% --log-level warn' RegPath='' ServiceName='' ThreatExistsRegEx='WARN\s+Detected' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <!-- https://docs.sophos.com/esg/spl/en-US/help/ServerProtectionAgent/index.html#on-demand-scan-return-codes -->     <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>     <ExitCode Type='Warning' Description='Scan completed with warnings. Check av.log for more information.'>8</ExitCode>     <ExitCode Type='Warning' Description='Password-protected file found'>16</ExitCode>     <ExitCode Type='Error' Description='Invalid command line argument'>2</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>36</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was canceled'>40</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>24</ExitCode>       <ExitCode Type='Error' Description='Unknown internal error during scan'>41</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Symantec -->   <AntivirusInfo Type='Windows' Name='Symantec' IsPortableSoftware='false' ExecutableFilePath='Veeam.Backup.Antivirus.Scan.exe' CommandLineParameters='/p:%Path%' RegPath='HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\symcscan' ServiceName='symcscan' ThreatExistsRegEx='Threat\s+found' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>     <ExitCode Type='Error' Description='Invalid command line argument'>1</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>2</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was canceled'>4</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>3</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Eset File Security -->   <AntivirusInfo Type='Windows' Name='ESET File Security' IsPortableSoftware='true' ExecutableFilePath='%ProgramFiles%\ESET\ESET File Security\ecls.exe' CommandLineParameters='%Path% /clean-mode=None /no-symlink' RegPath='' ServiceName='' ThreatExistsRegEx='result\s\*=\s\*["&apos;](?!is OK["&apos;])[^"&apos;]+["&apos;]' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>1</ExitCode>     <ExitCode Type='Warning' Description='Some files were not scanned'>10</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>50</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>100</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Eset File Security for Linux -->   <AntivirusInfo Type='Linux' Name='ESET File Security for Linux' IsPortableSoftware='true' ExecutableFilePath='/opt/eset/efs/bin/odscan' CommandLineParameters='--scan --profile="@In-depth scan" --readonly %Path%' RegPath='' ServiceName='' ThreatExistsRegEx='' IsParallelScanAvailable='false' OutputSupported='false'>     <ExitCodes>       <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>       <ExitCode Type='Infected' Description='Virus threat was detected'>1</ExitCode>       <ExitCode Type='Warning' Description='Some files were not scanned'>10</ExitCode>       <ExitCode Type='Infected' Description='Virus threat was detected'>50</ExitCode>       <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>100</ExitCode>     </ExitCodes>   </AntivirusInfo>   <!-- ESET Antivirus -->   <AntivirusInfo Type='Windows' Name='ESET Antivirus' IsPortableSoftware='true' ExecutableFilePath='%ProgramFiles%\ESET\ESET Security\ecls.exe' CommandLineParameters='%Path% /clean-mode=None /no-symlink' RegPath='' ServiceName='' ThreatExistsRegEx='result\s\*=\s\*["&apos;](?!is OK["&apos;])[^"&apos;]+["&apos;]' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>1</ExitCode>     <ExitCode Type='Warning' Description='Some files were not scanned'>10</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>50</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>100</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Windows Defender -->   <AntivirusInfo Type='Windows' Name='Windows Defender' IsPortableSoftware='false' ExecutableFilePath='%ProgramFiles%\Windows Defender\mpcmdrun.exe' CommandLineParameters='-Scan -ScanType 3 -File %Path% -DisableRemediation -BootSectorScan' RegPath='HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\WinDefend' ServiceName='WinDefend' ThreatExistsRegEx='Threat\s+information' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='No threats detected'>0</ExitCode>     <ExitCode Type='Error' Description='Antivirus scan was completed with errors'>2</ExitCode>     <ExitCode Type='Infected' Description='Virus threat was detected'>2</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Bitdefender -->   <AntivirusInfo Type='Windows' Name='Bitdefender Endpoint Security Tools' IsPortableSoftware='true' ExecutableFilePath='%ProgramFiles%\Bitdefender\Endpoint Security\product.console.exe' CommandLineParameters=' /c FileScan.OnDemand.RunScanTask custom path=%Path%' RegPath='' ServiceName='' ThreatExistsRegEx='Remaining issues:\s[1-9]\d\*|Resolved issues:\s[1-9]\d\*' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='Command executed successfully'>0</ExitCode>     <ExitCode Type='Error' Description='Invalid Parameter'>87</ExitCode>     <ExitCode Type='Error' Description='Bad Arguments'>160</ExitCode>     <ExitCode Type='Error' Description='Function Failed – an error occurred while executing the command'>1627</ExitCode>     <ExitCode Type='Infected' Description='A threat was detected on the system'>-526</ExitCode>    </ExitCodes>   </AntivirusInfo>   <!-- Trellix -->   <AntivirusInfo Type='Windows' Name='Trellix Command Line Scanner' IsPortableSoftware='true' ExecutableFilePath='scan.exe' CommandLineParameters='%Path% /NOMEM /ALL /SUB /PROGRAM /RECURSIVE /UNZIP /ANALYZE /MANALYZE /PANALYZE' RegPath='' ServiceName='' ThreatExistsRegEx='Found' IsParallelScanAvailable='false' OutputSupported='true'>    <ExitCodes>     <ExitCode Type='Success' Description='No viruses found'>0</ExitCode>     <ExitCode Type='Infected' Description='Virus found'>13</ExitCode>     <ExitCode Type='Infected' Description='Virus found in memory'>10</ExitCode>     <ExitCode Type='Error' Description='Unexpected Error has occurred'>1</ExitCode>     <ExitCode Type='Error' Description='Self-integrity check failed'>15</ExitCode>     <ExitCode Type='Error' Description='DAT file not found'>8</ExitCode>     <ExitCode Type='Error' Description='There has been a problem with scan'>6</ExitCode>     <ExitCode Type='Error' Description='DAT file integrity check failed'>2</ExitCode>    </ExitCodes>   </AntivirusInfo>  </Antiviruses> |

Antivirus Configuration File Structure

The AntivirusInfos.xml file contains the following elements:

* Antiviruses. Encapsulates the file with antivirus settings.
* AntivirusInfo. Describes the antivirus software.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)See AntivirusInfo attributes

| Attribute | Description |
| --- | --- |
| Name | Specifies the antivirus name. Veeam Backup & Replication will display this name in Scan Backup or restore session logs. |
| IsPortableSoftware | Indicates if antivirus software is portable:   * If you set this attribute to True, Veeam Backup & Replication will treat the antivirus software as portable. Before performing secure restore, Veeam Backup & Replication will verify if the antivirus executable file exists. The path to the file is specified by the [ExecutableFilePath](#path) attribute. * If you set this attribute to False, Veeam Backup & Replication will treat the antivirus software as non-portable. Before performing secure restore, Veeam Backup & Replication will verify if the antivirus registry value or configuration parameter exists and if the antivirus service is running. |
| ExecutableFilePath | Specifies the full path to the antivirus executable file.  Note: Some antivirus software uses separate installation folders for different versions. Make sure that you add the full path to the antivirus executable file you use. |
| CommandLineParameters | Specifies antivirus commands that you want to execute during the scan. Make sure that the antivirus supports the specified commands. For example, the list of commands for ESET is available in [this ESET KB article](https://support.eset.com/kb3417/).  Note: The %Path% variable is required for this attribute. During Scan Backup or Secure Restore, Veeam Backup & Replication substitutes this variable for the path to the directory with mounted disks (C:\VeeamFLR\<machinename> or  /tmp/Veeam.Mount.FS/<UUID>/). |
| ServiceName | Specifies the name of the antivirus service. The service must be responsible for data scanning. The attribute value can be an empty string if the value of the IsPortableSoftware attribute is set to True and the value of the ExecutableFilePath attribute is not empty. |
| RegPath | Specifies the registry value of the anitivirus service. The attribute value can be empty in the following cases:   * If the value of the IsPortableSoftware attribute is set to True and the value of the ExecutableFilePath attribute is not empty. * If the antivirus solution is used in a Linux environment. |
| ThreatExistsRegEx | Specifies regular expressions. A regular expression is a sequence of characters that form a search pattern. Veeam Backup & Replication will search the antivirus output messages for the specified regular expression. If any of the output messages match the expression, Veeam Backup & Replication will notify you on detected threat.  Note: You must have a good understanding of the regular expression language to specify this attribute properly. For more information on the regular expression language, see [Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference). |
| IsParallelScanAvailable | Indicates if the antivirus will run multiple jobs to scan files on mounted disks simultaneously.  When using the default False value, Veeam Backup & Replication will lock the antivirus to perform the scan for the current Scan Backup or restore session. The antivirus will not be available for other Scan Backup or Secure Restore sessions until the scan completes.  The default value for antivirus lock timeout is 24 hours. If the scan does not complete after this period, Veeam Backup & Replication will finish other restore sessions as specified in the restore wizard: abort restore sessions or restore machines (or its disks) with restrictions.  Note: For Microsoft Windows-based antivirus solutions, you can change the lock timeout using registry values. To do this, contact Veeam Support.  If the antivirus CLI does not support multiple scan jobs, set this attribute to False. |
| OutputSupported | Indicates if the antivirus software displays output messages in the scan results. The value of this attribute depends on the antivirus software.  If this attribute is set to True, scan results will contain an exit code message and log messages generated by the antivirus software.  If this attribute is set to False, scan results will contain only an exit code message and a default log message generated by Veeam Backup & Replication. |

* ExitCodes. Encapsulates messages that Veeam Backup & Replication displays on scan results.
* ExitCode. Describes the subject and the body of the message that Veeam Backup & Replication displays on scan results.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)See ExitCode attributes

| Attribute | Description |
| --- | --- |
| Type | Specifies the subject of the message that Veeam Backup & Replication will display on scan results:   * Success * Infected * Warning * Error |
| Description | Specifies the body of the message that Veeam Backup & Replication will display on scan results. |

Customizing Antivirus Configuration File

If you want to scan machine data with other antivirus software, make sure that it supports the command line interface (CLI). Then, add configuration for this software to the AntivirusInfos.xml file. The configuration must contain the AntivirusInfo element with all nested elements and attributes.

You can edit the AntivirusInfos.xml file in the following ways:

* On Microsoft Windows-based mount servers, you can:

* Edit the AntivirusInfos.xml file directly.

* Use the [Copy-VBRAntivirusConfigurationFile](https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrantivirusconfigurationfile.html?ver=13) cmdlet to copy a version of the AntivirusInfos.xml file to your mount servers.

* On Linux-based mount servers, you can:

* Use the Files view in Veeam Backup & Replication console. For more information, see [Copying Files and Folders Manually](copying_files_and_folders.md).
* Use the [Copy-VBRAntivirusConfigurationFile](https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrantivirusconfigurationfile.html?ver=13) cmdlet to copy a version of the AntivirusInfos.xml file to your mount servers.

|  |
| --- |
| Note |
| Consider the following:   * If you made changes to the antivirus configuration file, you do not need to restart Veeam services on the backup server — Veeam Backup & Replication will perform the next malware scan with new settings. * During the upgrade, the customized AntivirusInfos.xml file is replaced by the default one. Do not forget to make necessary changes to it. * If the mount server is a [Veeam Software or Infrastructure Appliance](deployment_options.md), you cannot edit the AntivirusInfos.xml file. If you want to use third-party antivirus software, you must assign the mount server role to a non-Appliance server. |


