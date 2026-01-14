---
title: "attributes_of_a_link_element"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/attributes_of_a_link_element.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

A link element in the XML document usually has the following attributes:

Rel

The Rel attribute defines the type of relationship between the resource and the linked resource or state. The Rel attribute can identify the following relationships:

| Relationship | Description |
| --- | --- |
| Action | Identifies an action that can be performed with the linked object. For example, Create, Edit, Delete, Start, Stop, Retry, Clone and so on. |
| Type of relationship | Identifies the type of relations between the linked resource and the resource. Currently Veeam Backup Enterprise Manager REST API offers two types of relations:   * The Up value indicates that the linked resource is a parent element for the current resource. For example, the backup repository is a parent for the backup stored in this repository. * The Down value indicates that the linked resource is a child element for the current resource. For example, the repository is a child for the backup server to which the repository is connected. |
| Alternate URL | In the entity reference resource representation, the Alternate value in the Rel attribute of the link identifies that the link is a reference to the resource entity. In the entity resource representation, it identifies the link to the reference representation. For details, see [Resource Representation for Key Resources](resource_representation_for_ke.md). |

Type

The Type attribute defines the type of a related resource. The type attribute is used only for linked resources, not actions.

For example, the link below is provided in the representation of the restore point resource:

|  |
| --- |
| <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/d8877ca3-6283-4011-b09a-73696ef34bf0" Name="Exchange Backup" /> |

The link identifies a backup for which the restore point is created:

* Rel attribute defines the relationship between the current resource, restore point, and the linked resource, backup — Up. This means that the linked backup resource is a parent element for the restore point resource.
* Type attribute defines the type of the linked resource — Backup.
* Href attribute contains a URL for the backup resource — /backupServers/21a631e0-af7f-46ba-afbd-273de2e6fd4a.
* Name attribute defines a name for the backup — Exchange Backup.

Href

The Href attribute contains a reference to a related resource or an action in the URL format. The client can use the URL to get a representation of a related resource or perform some action with the resource. The resource URL should be treated as an immutable, opaque string: all URLs are controlled by the server, and the client should only select and use the necessary URL.

Name

The Name attribute defines the human-readable name of the resource. The name attribute is used for key resources and may be skipped in links to resource collections and actions to creating new resources.

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
