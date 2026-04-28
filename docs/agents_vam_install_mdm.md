---
title: "Installing and Configuring Veeam Agent for Mac with MDM Solution"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_vam_install_mdm.html"
last_updated: "4/27/2026"
product_version: "13.0.1.2067"
---

# Installing and Configuring Veeam Agent for Mac with MDM Solution


You can install and configure Veeam Agent for Mac with a Mobile Device Management (MDM) solution. With an MDM solution, you can connect Veeam Agent to Veeam backup server and include Veeam Agent computer in a protection group.

Veeam Agent for Mac provides the installation package that can be used in the following MDM solutions:

* Jamf Pro
* Microsoft Intune
* SimpleMDM

Veeam Agent for Mac installation and configuration includes the following operations:

1. Installing Veeam Agent.

Only the Veeam Agent for Mac installation package is required.

For details how to deploy a .pkg package, refer to the documentation of your MDM solution.

1. Granting full disk access to Veeam Agent.

To grand full disk access and perform other configuration tasks, you need to use the following Veeam Agent parameters:

* Application ID: NX3JU8SRVL
* Bundle ID: com.veeam.Agent

For other details, refer to the documentation of your MDM solution.

1. Configuring Veeam Agent.

The configuration is required to set up connection between the Veeam Agent computer and the Veeam backup server. To configure Veeam Agent, deploy the device profile for the Veeam backup server on the Veeam Agent computer.

If you use Jamf Pro, Microsoft Intune or SimpleMDM, see detailed instructions in the [Deploying Device Profile with MDM Solution](#profile) subsection. If you use another MDM solution, refer to the documentation of your MDM solution.

Deploying Device Profile with MDM Solution

With an MDM solution, you can connect Veeam Agent to Veeam backup server and include Veeam Agent computer in the protection group in Veeam Backup & Replication. To do this, you must deploy the protection group configuration file as a device profile.

The example below can be used to install Veeam Agent for Mac with Jamf Pro, Microsoft Intune or SimpleMDM. If you use another MDM solution, instructions may differ. For details, refer to the documentation of your MDM solution.

In the example below, the following color coding is applied:

* The yellow parts can be replaced with any values of your choice. Note that UUIDs must be in the UUID format.
* The green part must be copied from the configuration file.

Depending on the MDM solution that you use, select one of the following configuration files:

1. <protection\_group\_name>\_escaped.xml
2. <protection\_group\_name>.xml

where <protection\_group\_name> is the name of the protection group for pre-installed Veeam Agents.

* All other parts must not to be edited.

|  |
| --- |
| <?xml version="1.0" encoding="UTF-8"?> <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "<http://www.apple.com/DTDs/PropertyList-1.0.dtd>"> <plist version="1.0">     <dict>         <key>PayloadIdentifier</key>         <string>com.veeam.Agent.managedsettings</string>         <key>PayloadRemovalDisallowed</key>         <false />         <key>PayloadScope</key>         <string>System</string>         <key>PayloadType</key>         <string>Configuration</string>         <key>PayloadUUID</key>         <string>fa4b7334-c696-000-87d0-0242ac130003</string>         <key>PayloadOrganization</key>         <string>Veeam</string>         <key>PayloadVersion</key>         <integer>1</integer>         <key>PayloadDisplayName</key>         <string>Veeam Agent for Mac Managed Settings</string>          <key>PayloadContent</key>         <array>             <dict>                 <key>PayloadType</key>                 <string>com.apple.ManagedClient.preferences</string>                 <key>PayloadUUID</key>                 <string>d463e322-c696-0000-87d0-0242ac130003</string>                 <key>PayloadIdentifier</key>                 <string>com.veeam.Agent.managedsettings.d463e322-c696-11ea-0000-0242ac130003</string>                 <key>PayloadEnabled</key>                 <true />                 <key>Identifier</key>                 <string>com.veeam.Agent</string>                 <key>IdentifierType</key>                 <string>bundleID</string>                 <key>PayloadContent</key>                 <dict>                     <key>com.veeam.Agent</key>                     <dict>                         <key>Forced</key>                         <array>                             <dict>                                 <key>mcx\_preference\_settings</key>                                 <dict>                                     <key>CatchAllConfig</key>                                     <string>&lt;?xml version=&quot;1.0&quot;?&gt;&lt;ManagementServerConfiguration Version=&quot;2&quot; VbrInstallationId=&quot;XXXXXXXX-XXXX-45ed-abb3-7f72e53546c0&quot; CertificatePem=&quot;-----BEGIN CERTIFICATE-----&amp;#xA;MIIDCzCCAfOgAwIBAgIQmhoOZimULbZFJLx4aErSJDANBgkqhkiG9w0BAQsFADAq&amp;#xA;MSgwJgYDVQQDEx9WZWVhbSBCYWNrdXAgU2VydmVyIENlcnRpZmljYXRlMB4XDTI0&amp;#xA;MDIyNjE2MDUxN1oXDTM0MDIyNzE2MDUxN1owLzEtMCsGA1UEAxMkZTAxNDg4Nzkt&amp;#xA;NTA4NS00MWYyLWFmMTMtYmRkOThkNjViZWM5MIIBIjANBgkqhkiG9w0BAQEFAAOC&amp;#xA;AQ8AMIIBCgKCAQEAvMeqQ5WlZNRJel5PtdRtTQo4s4Zdwu0Af+pVxuFDaoqkVuGB&amp;#xA;S8QvDQoXXeCjd50tNf/+V+DRbdfmIxXGS8xI8b61dJvec3MK7spNuLmvHswEJF6O&amp;#xA;hjDqAqnWAtkt71m7TBabtB6dPdZNpwZfITXtQAinek4XPhouOf66WmzAueJxD86r&amp;#xA;EmtyVcF+fQeVewKbO9KBjz5DbP+SzVw7GJoHzsB9Pjn+xmFanQlC1NMzanfOhTYO&amp;#xA;4/MXxyV3qGBwh/pyR6/mY0Mkp/21+sfWa3bIJXWoSVxFrXh/uQ1btmeNdaw6oOXD&amp;#xA;y4Lryd5U/bKjS/S+79v3LoQSEw9aYCJRXSeeQwIDAQABoygwJjAMBgNVHRMBAf8E&amp;#xA;AjAAMBYGA1UdJQEB/wQMMAoGCCsGAQUFBwMCMA0GCSqGSIb3DQEBCwUAA4IBAQCU&amp;#xA;gjJ7zLSBtHS9dh7gxrXRKruJOer2AdJSDP9L460PXLoza/kDEpfvsyZ9BKOX8I+B&amp;#xA;7ssx8UEXdDBBlJYQma83C++uNjfRT3XMVd2mSPVZJJLhNFC7LU4B2gCB1YlKD3mm&amp;#xA;urc+lDZNUHw4cT7w/yokA79BICm/OvpAzS0eQwEuXEDLpjbNeNoKBZs4yBVZuVq9&amp;#xA;m1oyKjQzetZGjWFnLLDncAVj5zmwYhplraTBZTfQ/XXigZIBXVpexpgCCGi640cU&amp;#xA;4uft9DcXq5XUWtpeuRisGJ5GhtkoCmQ1vsy69648Rm9EGAyq0+6ll3DBO2jGRWll&amp;#xA;dQ9yqSg8UwY40oh5QgIW&amp;#xA;-----END CERTIFICATE-----&amp;#xA;-----BEGIN ENCRYPTED PRIVATE KEY-----&amp;#xA;MIIFNjBgBgkqhkiG9w0BBQ0wUzAyBgkqhkiG9w0BBQwwJQQQQs5AynoMhKlL4zZy&amp;#xA;CPPTugIDCSfAMAwGCCqGSIb3DQIJBQAwHQYJYIZIAWUDBAEqBBBjFQGETs80gE5l&amp;#xA;0gR63bk2BIIE0Fhv/9zUSRc7OqCJChl5nXm8NxHUWOTU0Yue0fvKSUhj0Iof7MQP&amp;#xA;Y5Wr/bfcZUIy7dg+3p8VhSnLU9ZCbbkx0QcDnhy+L6cRSWHwwniAVUYhTMQIDrGB&amp;#xA;eaNg6bT4mQrl8hX+n9iOfvAiINqVtoAvGwvop6smXagD9YBbfTinUvTfLhb+1gIE&amp;#xA;uyXV2S218AJWkbTFy2HkR6C4MsMjBzkb57IM4twM9JlEq+lGuKOP0i2VIb6MePc5&amp;#xA;dLEPeszYQkA2yI7KOaeXBmISErvstd1cg4Z3oeG9xr4afm86ndloYJFaJD4Ge5wb&amp;#xA;WPEqMmE/TSC1cuqKTAPMCHuLwgVt80LljR4Cq4HZw1epNuLVBhIvFNREkkwkdvGA&amp;#xA;6YEtswlPQORuob5/panZP6icfqPkAaDjheZgsQVgGD9F57faXAmMSa4u5Qhqshfi&amp;#xA;dIf37pVHRIk6IgeJgqPZA4vZUumyBHHuFPzpV5DrcDUYL9gVIYyXMYFXZAS+O4tx&amp;#xA;z5ClHlN4m3AVLqmui9cDylQdEyaDhPMq+tb1+3jLm+VRha5MRTqnbIoU0TjhNrYy&amp;#xA;79c3sfF6l0k4aSfWU+tePoRqWxqHTaUm+z+qR4qS7t3dL2WyohYFgf8sGrh21Jub&amp;#xA;mlrUBOWmWO2KiQAHtqeIHDSuoHMHOt2C+T7NKUK4oslaYfH/3RBMFrWXeJImlyP2&amp;#xA;kF6Up2orgW5f0jMoUs0pByLfHLiRPdz1YNMV9xFuPwRmAocTW6AZ2EzrAvAZ1iIK&amp;#xA;sq43PYWqbpku+L5JtPQz4dS82YN5FNxMJfKQGSjmBmMYi9Ux7bDI2sFVxD1T9Cui&amp;#xA;c2+Gdfc9s19NeLm9pM3rKDuLytLIi2u4Hn7ZDr/KodRH61UjChRuB4xZ2MyFf+s2&amp;#xA;Oric+VBXZC/ZGf5fmdtzY9z7Nz61MN3su5Lpk7e1HhfJKGjIUqjUSIS92q9lpkV9&amp;#xA;vxKh7mH3BY5Bkjra9DSmVI3hSsZosaNZGtn0Q7VraRsVYcI2MyEyzZbNElFWOoAE&amp;#xA;Xr2yAdZVYV43DawTwMzJQ3IclgSXy+bXlhYplCFSoMaeO/utBeZzZQEFSIQF8KU3&amp;#xA;9yVfvvGLQcw0WZxAjhQ2cD0eUNEcx+UGo3QE+ZOXBOxZNho4ZhEiqRKSzjqe1+0D&amp;#xA;vjDtkHu7SJSfdYDWSJwzgL0kTCmx+KfKjxjzAZhatA1VqKrn+WwrOjGEcTmFWJHy&amp;#xA;h8cUt2nVUf9pBEIMSi+DpJbjRPTjZ6bpc2vEv4NJqlkHmfEszexauPXUQVkhm4rc&amp;#xA;9Iz8hhHOV8OnozneAmP8uaNhuTFE/fbEmD1w2qQyyjwhHy/NinBDcWl+lqB2ICvW&amp;#xA;5pTnNnk2RQlWEuEyC0Qql/5shmngVIJxMf/BapljxRvgSLS/jDkyNOHEnUlp1Uqh&amp;#xA;SOPdDaS6bgqJOuU0s9l+IR55tXqE09LIaSGUcGJIGjgMJlmun+cDORAlhMXKQ0Pv&amp;#xA;Qo+mLrtUz2lWWNCaU8KggoXO0swr1YElbR7BTdbN8+P0wwp3FgoGzwv6Dc3cqaEt&amp;#xA;jpOtudTfKkOfg/XNwkRpAHNRGCbaBwscDYCUtmYuAQvzqgM8AuwhKNtOWYdVL7TT&amp;#xA;1RKgtsYCJF0RUd9bI7oxgeuW+huSBxXcNdw+nlLoyh22Cy8wKgXw61q3&amp;#xA;-----END ENCRYPTED PRIVATE KEY-----&quot; VbrVersion=&quot;13.0.1.2067&quot;&gt;&lt;VbrConnectionInfo ServerName=&quot;winvbrserver&quot; Port=&quot;10006&quot;&gt;&lt;IpAddresses&gt;&lt;String value=&quot;172.XX.XX.XX&quot; /&gt;&lt;/IpAddresses&gt;&lt;/VbrConnectionInfo&gt;&lt;VBRConnectionInfoIpV6Compatible ServerName=&quot;winvbrserver&quot; Port=&quot;10006&quot;&gt;&lt;IpAddresses&gt;&lt;String value=&quot;fd00:ac19:0:19c0:0:f333:3656:7a3a&quot; /&gt;&lt;String value=&quot;172.XX.XX.XX&quot; /&gt;&lt;/IpAddresses&gt;&lt;/VBRConnectionInfoIpV6Compatible&gt;&lt;SelfDiscoveryOptions /&gt;&lt;VbrCatchAllInfo /&gt;&lt;/ManagementServerConfiguration&gt;</string>                                 </dict>                             </dict>                         </array>                     </dict>                 </dict>             </dict>         </array>     </dict> </plist> |

After the device profile is deployed on the Veeam Agent computer, Veeam Agent will use the settings from the profile to connect to the Veeam backup server.

Consider that the connection between Veeam backup server and Veeam Agent computer is not persistent. Veeam Agent synchronizes with Veeam Backup & Replication every 6 hours. To synchronize Veeam Agent with Veeam Backup & Replication immediately, run the following command on the Veeam Agent computer:

|  |
| --- |
| veeamconfig mode syncnow |


