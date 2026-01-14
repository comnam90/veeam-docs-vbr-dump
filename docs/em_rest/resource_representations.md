---
title: "resource_representations"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/resource_representations.html"
last_updated: "8/7/2025"
product_version: "13.0.1.1071"
---


In this article

In REST API, a resource is an abstract notion. When the client and the server communicate with each other, they exchange representations of resources.

The resource representation has the form of an XML or JSON document. For example, if you request information about a backup server connected to Veeam Backup Enterprise Manager, Veeam Backup Enterprise Manager will return a resource representation of the backup server resource similar to the following:

XML Representation

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1" Name="appsrv01.tech.local" UID="urn:veeam:BackupServer:ffa6d4ef-ea63-4fb3-88a1-84706c2430e1"> |

JSON Representation

|  |
| --- |
| {    "Links": [       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/jobs",          "Type": "JobReferenceList"       },       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/repositories",          "Type": "RepositoryReferenceList"       },       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/externalRepositories",          "Type": "ExternalRepositoryReferenceList"       },       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/credentials",          "Type": "CredentialsList"       },       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/passwords",          "Type": "PasswordKeyList"       },       {          "Rel": "Alternate",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1?format=Entity",          "Name": "appsrv01.tech.local",          "Type": "BackupServer"       },       {          "Rel": "Down",          "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1/managedServers",          "Type": "ManagedServerReferenceList"       }    ],    "UID": "urn:veeam:BackupServer:ffa6d4ef-ea63-4fb3-88a1-84706c2430e1",    "Name": "appsrv01.tech.local",    "Href": "https://srv12.tech.local:9398/api/backupServers/ffa6d4ef-ea63-4fb3-88a1-84706c2430e1",    "Type": "BackupServerReference" } |

|  |
| --- |
| Note |
| To request resource representations in a specific format (XML or JSON), you must use request headers. For details, see [Header Format](em_web_api_specifications.md#header_format). |

A resource representation is a document that holds all data you need to know about the resource and its behavior. Typically, a resource representation contains the following data on the resource:

* General information about the resource: name, ID, URL and type
* Information about other resources related to the resource
* Set of actions that can be performed with the resource (if applicable)

Information about related resources and actions available for the resource is presented in the form of [links](links.md).

In This Section

* [Resource Representations for Non-Key Resources](representation_non_key.md)
* [Resource Representation for Key Resources](resource_representation_for_ke.md)
* [Resource Representations for Collections of Resources](representation_collections.md)

Page updated 8/7/2025

Page content applies to build 13.0.1.1071
