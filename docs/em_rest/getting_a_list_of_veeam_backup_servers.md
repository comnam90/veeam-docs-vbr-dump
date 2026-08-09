---
title: "Step 3. Get a List of Backup Servers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/getting_a_list_of_veeam_backup_servers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Get a List of Backup Servers


To get a list of all backup servers, you need to retrieve a resource representation of the /backupServers resource. This resource contains a collection of backup servers connected to Veeam Backup Enterprise Manager.

1. In the resource representation of the logon session created at the previous step, find a link to the /backupServers resource. The Rel attribute within the link component has the Down value and the Type attribute is set to BackupServerReferenceList or BackupServerList:

|  |
| --- |
| <Link Rel="Down" Type="BackupServerReferenceList" Href="https://localhost:9398/api/backupServers> |

1. Get the URL for the backup servers collection. The URL is provided in the Href attribute of the link component:

|  |
| --- |
| https://localhost:9398/api/backupServers |

1. Send the GET HTTP request to the retrieved URL. Veeam Backup Enterprise Manager will return a representation of all connected backup servers:

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540" Name="backupserver" UID="urn:veeam:BackupServer:f62624c1-8462-4747-8bd4-d686f99b0540">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540?format=Entity" Name="backupserver" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/managedServers" />     </Links>   </Ref>   <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c" Name="localhost" UID="urn:veeam:BackupServer:50a1b2fb-b90a-4e05-816f-e298eb2f995c">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c?format=Entity" Name="localhost" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/managedServers" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

