---
title: "GET /security/accounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_accounts_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /security/accounts/{ID}


Returns an account having the specified ID. The account is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Request

To get an account having the specified ID, send the GET HTTP request to the /security/accounts/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/accounts/{ID} |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Query Parameters

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /security/accounts/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the account that has a specific security role in Veeam Backup Enterprise Manager, for example: urn:veeam:EnterpriseAccount:9570aed1-7eff-4684-b77a-7735bdbe820d. |
| Name | String | Name of the account that has a specific security role in Veeam Backup Enterprise Manager, for example: BACKUPSERVER\Operator. |
| AccountType | String | Type of the account that has a specific security role in Veeam Backup Enterprise Manager. Possible values:   * User * Group * ExternalUser * ExternalGroup   Accounts of the ExternalUser and ExternalGroup type are created for users that will access Veeam Backup Enterprise Manager using a single sign-on service. For details, see the [SAML Authentication Support](https://helpcenter.veeam.com/docs/backup/em/em_saml.html?ver=120) section in the Veeam Backup Enterprise Manager Guide. |
| AllowRestoreAllVms | Boolean | Defines whether the account must have permissions to restore all VMs or not. Possible values:   * True * False |
| FlrSettings | FileRestoreSettingsInfoType | File-level restore restrictions assigned to the added account. For details, see [File-Level Restore Settings](#flr). |
| SqlSettings | SqlRestoreSettingsInfoType | SQL restore restrictions assigned to the added account. For details, see [SQL restore settings](#sql). |

File-Level Restore Settings

| Element | Type | Description |
| --- | --- | --- |
| FlrInplaceOnly | Boolean | Defines whether the account has permissions to restore only files with specific filename extensions or not. |
| FlrExtentionRestrictions | String | Filename extensions for files that are permitted for restore separated by comma, for example: doc,pptx,pdf. |

SQL Restore Settings

| Element | Type | Description |
| --- | --- | --- |
| DenyInPlaceRestore | Boolean | Defines whether the account is prevented from overriding production databases at restore. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /security/accounts/{ID} | Alternate | Alternate URL of the [/security/roles/{ID}](security_roles_id.md) resource. |
| /security/accounts/{ID}/roles | Down | URL of the [/security/accounts/{ID}/roles](security_accounts_id_roles.md) resource — a collection of security roles assigned to the account. |
| /security/accounts/{ID}/roles | Create | URL for the [POST /security/accounts/{ID}/roles](post_security_accounts_id_roles.md) request. |
| /security/accounts/{ID}/scopes | Down | URL of the [/security/accounts/{ID}/scopes](security_accounts_id_scopes.md) resource — a collection of restore scopes defined for the account. |
| /security/accounts/{ID}/scopes | Create | URL for the [POST /security/accounts/{ID}/scopes](post_security_accounts_id_scopes.md) request. |
| /security/accounts/{ID} | Delete | URL for the [DELETE /security/accounts/{ID}](delete_security_accounts_id.md) request. |
| /security/accounts/{ID} | ToggleRestoreScopesEnabled | URL for the [POST /security/accounts/{ID}](post_security_accounts_id.md) request. |

Example

A sample request below returns an account having ID 605cff11-7437-42dc-bd1e-262222cfdddc:

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/605cff11-7437-42dc-bd1e-262222cfdddc    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


