---
title: "Special Characters in Responses"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/special_symbols.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Responses from the server may contain special characters that cannot be displayed directly in an XML document. Such characters are replaced with character entity references, or predefined entities. For example, resource representations of VM guest OS file systems and responses from the [query service](query_service.md) and [lookup service](lookup_service.md) contain the '&amp;' character entity reference instead of the ‘&’ character itself.

HTTP responses received from Veeam Backup Enterprise Manager REST API may contain the following character entity references:

| Character | Character Entity Reference | Description |
| --- | --- | --- |
| & | &amp; | Ampersand |
| < | &lt; | Less-than sign |
| > | &gt; | Greater-than sign |
| " | &quot; | Quotation mark |
| ' | &#39; | Apostrophe |
| / | &#x2F; | Slash |

The example below represents a list of links in the paginated response from the query service. The ‘&’ (ampersand) character used as a separator for query parameters in the query string is replaced with the '&amp;' character entity reference.

|  |
| --- |
| <Links> |

When the client parses a response and retrieves a link that contains a character entity reference, the client must replace the character entity reference with the character itself before using the link in a request. If the client sends a request that contains a character entity reference, the server may ignore the subsequent parameter while processing the request or completely fail to process the request.

|  |
| --- |
| Note |
| You do not need to perform this operation when you evaluate and test capabilities of Veeam Backup Enterprise Manager REST API using Veeam Backup Enterprise Manager Web Client. For your convenience, Veeam Backup Enterprise Manager Web Client automatically replaces character entity references with the characters and displays responses in a readable way. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
