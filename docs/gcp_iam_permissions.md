---
title: "Google Compute Engine IAM User Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gcp_iam_permissions.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Google Compute Engine IAM User Permissions

In this article

To enable restore of workloads to Google Compute Engine, do the following:

1. Grant the following roles to the IAM user whose credentials you plan to use to connect to Google Compute Engine:

* Compute Admin role (roles/compute.admin)

To avoid granting the Compute Admin role to the IAM user Compute Engine service account for security reasons, you can create a custom role with the following Compute Engine IAM permissions and grant it instead:

|  |
| --- |
| compute.addresses.list |

* Cloud Build Editor role (roles/cloudbuild.builds.editor)
* Project IAM Admin role (roles/resourcemanager.projectIamAdmin)
* Storage Admin role (roles/storage.admin)
* Storage HMAC Key Admin (roles/storage.hmacKeyAdmin)
* Viewer role (roles/viewer)

For more information, see the Prerequisites for importing and exporting VM images section in the [Google Cloud documentation](https://cloud.google.com/compute/docs/import/requirements-export-import-images#grant-user-account-role).

1. [If you recover workloads with helper appliance] Make sure that the [Cloud Build API](https://cloud.google.com/build/docs/api/reference/rest) is enabled. Then grant the following roles to the Cloud Build service account in Google Compute Engine:

* Compute Admin role (roles/compute.admin)

To avoid granting the Compute Admin role to the Cloud Build service account for security reasons, you can use the custom role that you created for the IAM user Compute Engine service account and grant it instead.

* Service Account Token Creator role (roles/iam.serviceAccountTokenCreator)
* Service Account User role (roles/iam.serviceAccountUser)
* [Optional: to export or import images that use shared VPCs] Compute Network User role (roles/compute.networkUser)

For more information, see the Prerequisites for importing and exporting VM images section in the [Google Cloud documentation](https://cloud.google.com/compute/docs/import/requirements-export-import-images#required-roles-cloud-build-sa).

1. Make sure that VM Migration API is enabled. For more information on enabling the API, see the Enable Migrate to Virtual Machines services section in [Google Cloud documentation](https://cloud.google.com/migrate/virtual-machines/docs/5.0/get-started/enable-services).

After you enable VM Migration API, Google Compute Engine creates the default Migrate to Virtual Machines service account. If the account was not created, create it manually as described in the Trigger service agent creation section in [Google Cloud documentation](https://cloud.google.com/iam/docs/create-service-agents#create).

Grant the following roles to the service account:

* Storage Object Viewer (roles/storage.objectViewer)
* VM Migration Service Account (roles/vmmigration.serviceAgent)

The Google Cloud service account specified at the [Account](restore_google_account.md) step must have the VM Migration Administrator (roles/vmmigration.admin) role.

For more information on the required permissions and limitations, see the Import virtual disk images section in the [Google Cloud documentation](https://cloud.google.com/migrate/virtual-machines/docs/5.0/migrate/image_import#supported-formats).

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
