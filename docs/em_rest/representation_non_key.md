---
title: "Resource Representations for Non-Key Resources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/representation_non_key.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Resource Representations for Non-Key Resources


For non-key resources, Veeam Backup Enterprise Manager REST API provides a reference resource representation. The reference resource representation is used to identify the resource and its relations to other resources.

This type of representation provides the following data about the resource:

* Basic resource information: its ID (if available), name, URL and type
* Information about resources that are related to the current resource

For example, a reference representation for a credentials resource looks similar to the following:

XML Representation

|  |
| --- |
| <CredentialsInfo xmlns="http://www.veeam.com/ent/v1.0" Type="Credentials" Href="https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/credentials/e7592e37-834b-4c69-b505-597c91e9a77e"> |

JSON Representation

|  |
| --- |
| {   "Id": "e7592e37-834b-4c69-b505-597c91e9a77e",   "Username": "tech\\william.fox",   "Description": "tech\\william.fox",   "Password": "",   "Links": [    {     "Rel": "Up",     "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1?format=Entity",     "Name": "appsrv01.tech.local",     "Type": "BackupServer"    },    {     "Rel": "Edit",     "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/credentials/e7592e37-834b-4c69-b505-597c91e9a77e",     "Type": "Credentials"    },    {     "Rel": "Delete",     "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/credentials/e7592e37-834b-4c69-b505-597c91e9a77e",     "Type": "Credentials"    }   ],   "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/credentials/e7592e37-834b-4c69-b505-597c91e9a77e",   "Type": "Credentials"  } |


