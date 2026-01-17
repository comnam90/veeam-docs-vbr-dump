---
title: "Step 3. Get a List of Backup Servers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/getting_a_list_of_veeam_backup_servers.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| Request:  GET https://localhost:9398/api/backupServers    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
