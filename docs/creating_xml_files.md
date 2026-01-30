---
title: "XML Files with Machine Roles Description"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/creating_xml_files.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# XML Files with Machine Roles Description


Machine roles that you can assign to verified machines and machines from the application group are described in XML files. These XML files are stored in the /var/lib/veeam/sbroles folder on the backup server.

To add a new role, you must create a new XML file and save it to the SbRoles subfolder on the backup server. Do not save the XML file on the machine where the Veeam Backup & Replication console is installed — this will not affect the list of roles in Veeam Backup & Replication.

XML files describing machine roles have the following structure:

|  |
| --- |
| <SbRoleOptions>   <Role>     <SbRole>       <Id>4CDC7CC4-A906-4de2-979B-E5F74C44832F</Id>       <Name>Web Server</Name>     </SbRole>   </Role>   <Options>     <SbVerificationOptions>       <ActualMemoryPercent>100</ActualMemoryPercent>       <MaxBootTimeoutSec>300</MaxBootTimeoutSec>       <AppInitDelaySec>120</AppInitDelaySec>       <TestScripts>         <TestScripts>           <TestScript>             <Name>Web Server</Name>             <Type>Predefined</Type>             <TestScriptFilePath>Veeam.Backup.ConnectionTester.exe</TestScriptFilePath>             <Arguments>%vm\_ip% 80</Arguments>           </TestScript>         </TestScripts>       </TestScripts>       <HeartbeatEnabled>True</HeartbeatEnabled>       <DisableWinFirewall>True</DisableWinFirewall>       <PingEnabled>True</PingEnabled>     </SbVerificationOptions>   </Options>  </SbRoleOptions> |

The XML file with the role description contains the following tags and parameters:

| Tag | Required/ | Description |
| --- | --- | --- |
| <SbRoleOptions> | Required | Encapsulates the machine role file. |
| <Role> | Required | Parent tag for a role assigned to a machine. <SbRole>, <Id> and <Name> are children of this tag. |
| <SbRole> | Required | Encapsulates basic information for a machine role: ID and name. |
| <Id> | Required | Unique identifier of a machine role. |
| <Name> | Required | Name of a machine role. The machine role name is displayed in the roles list on the Role tab. |
| <Options> | Required | Parent tag for startup and test script options to be used for the defined role. <SbVerificationOptions>, <ActualMemoryPercent>, <MaxBootTimeoutSec>, <AppInitDelaySec>, <TestScripts>, <Name>, <Type>, <TestScriptFilePath>, <Arguments>, <HeartbeatEnabled>, <PingEnabled> are children of this tag. |
| <SbVerificationOptions> | Required | Encapsulates options data for a machine role. |
| <ActualMemoryPercent> | Optional | Percent of the original memory level that must be pre-allocated to a verified machine on the system boot. |
| <MaxBootTimeoutSec> | Optional | Maximum allowed time to boot a machine. |
| <AppInitDelaySec> | Optional | Duration of time for which Veeam Backup & Replication must wait after the machine is successfully booted in the virtual lab. After this time elapses, Veeam Backup & Replication will run test scripts. Time is specified in seconds. |
| <TestScripts> | Optional | Encapsulates test script data for a machine role. |
| <Name> | Optional | Name of a machine role. The machine role name is displayed on the Test Scripts tab. |
| <Type> | Optional | Type of the test script: Predefined or Custom. |
| <TestScriptFilePath> | Optional | Path to an executable file of the test script to be performed. The path can be absolute or relative. |
| <Arguments> | Optional | Arguments to be passed to the script. You can use the following variables:   * %vm\_ip% — IP address of a verified machine.   or  %vm\_fqdn% — a fully qualified domain name of a verified machine.   * %log\_path% — path to a log file to which verification results are stored. |
| <HeartbeatEnabled> | Required | Must a heartbeat test be enabled for this machine role: True or False. |
| <DisableWinFirewall> | Required | Must a firewall be disabled for this machine role: True or False. |
| <PingEnabled> | Required | Must a ping test be enabled for this machine role: True or False. |


