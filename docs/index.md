---
title: "File API Introduction"
keywords: index introduction
tags: [getting_started, file, api, library]
sidebar: guides_sidebar
permalink: index.html
summary: The File API allows you to download or upload files directly from Youforce, over HTTPS using the tool of your choice.
---

{% include important.html content="This API is controlled available and has consumption limitations. See API [statuses](guides_api_statuses.html)" %}

## Concepts

| Concept            | Description                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| File API           | Public endpoint to upload/list/download the files. In the request to File API, application id, business type and tenant are being identified. Once the files are uploaded to File API by a publisher application, the authorized subscriber application can list, download and delete the files.                                                                                                                                        |
| Business Type      | The files which are related to the same “business” are functionally grouped in File types called “Business types”.  File types are represented by an integer called Business Type Id.                                                                                                                                                                                                                                                     |
| Client Application | Client Applications are the users of the system. They are identified by an application Id. Client Applications are also authorized to tenantId(s).Client application needs to obtain a authentication token by using credentials (client id and client secret).The token includes application id, tenant and permission of the application. Client Applications could be authorized either as publisher or subscriber of a business type. |
| Publisher          | Publisher is a Client Application that can upload files of authorized business types and authorized tenants.                                                                                                                                                                                                                                                                                                                              |
| Subscriber         | Subscriber is a Client Application that can download/list the files of authorized business types and authorized tenants.                                                                                                                                                                                                                                                                                                                  |
| Tenant             | HR Core Client. Tenants are represented by tenant ids.                                                                                                                                                                                                                                                                                                                                                                                    |


## Authentication

We follow current industry standards and best practices. Authentication/authorization is not an exception. As part of the Identity and Access Management Strategy for system-to-system integrations, the File API is based on OAuth 2.0 and the authorization grant Client Credentials. Every API consumer system will be provisioned in our API Gateway as a Client Application (App). Client ID and Client Secret will be provided to be used by Apps as credentials. Thus, Apps will be able then to authenticate and get an access token (JWT) within the response payload. Subsequent requests authorization will be based on that access token previously retrieved.

## Tenant Authorization

Client Applications (apps) need to be authorized to the corresponding Tenant (HR Core Client) in order to consume the API.
By default, the applications are authorized to TenantId: **sandbox**.

## File Type Authorization

Client applications (apps) need to be authorized as publisher or subscriber of business types

By default,sandbox apps are authorized to the Sandbox File Types. 

## Supported File Types

The File API has been designed to support a specific set of use cases. This may be extended over time, based on customer feedback. See list of [Supported File Types](guides_file_supported_file_types.html).

## Retention Period
The files will be physically deleted from Storage automatically after the retention period expires (1 month).

The metadata of the files (FileName, tenantId , BusinessTypeId, etc) is deleted after 6 months.

## Curl Example

Here is an example of downloading a file using curl, available on most operating systems:

```shell
curl.exe https://api.raet.com/mft/v1.0/files/%fileid%?role=subscriber ^
--header "Authorization: Bearer eyJhbGciOiJSUzI1NiIs..." ^
--header "x-raet-tenant-id: 1234567" ^
--header "Accept: application/octet-stream"  ^
--output @C:/Youforce/somefile.xml
```

See complete [examples](https://github.com/VR-API-Integration/file-api-integration-examples) for curl (Batch) and .Net in Github.
