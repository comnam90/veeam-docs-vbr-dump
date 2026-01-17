---
title: "Link Types and XML Schema Definition"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/link_types_and_xml_schema.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Every link to a resource that is returned in a response from the server contains the [Type](attributes_of_a_link_element.md#type) attribute. This attribute defines the type of the related resource. Resource types are described in the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

The Type attribute value may differ from the root element name for the same resource. There are several general rules that help map link types to resource types in the XML schema:

1. Every value of the Type attribute ending with 'ReferenceList' (for example, JobReferenceList, CloudTenantRefernceList) always refers to the EntityReferences element of the XML schema.
2. Every value of the Type attribute ending with 'Reference' (for example, JobReference, CloudTenantRefernce) always refers to the EntityRef element of the XML schema.
3. Values of the Type attribute ending with 'List' (for example, LogonSessionList) are generally transformed into plural element names (for example, LogonSessions).
4. Values of the Type attribute that do not end with 'List', 'Reference' or 'ReferenceList' generally directly match root element names of the XML schema.

For details on resource types mapping, see [Mapping Link Types to XML Schema Elements](mapping_link_types_to_xml_schema.md).

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
