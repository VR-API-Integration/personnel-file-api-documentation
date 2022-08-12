---
title: File list of uploaded files
tags: [publisher, file, list, upload, api, library]
keywords: publisher, file, list, upload, api, library
summary: This endpoint allows you to retrieve a paginated collection of the files that have been uploaded by you.
last_updated: 3/26/2021
sidebar: guides_sidebar
permalink: guides_file_list_uploaded_files.html
folder: guides/publishers
topnav: topnav
---

In order to use the list endpoint:

- Create a Get request to the method's /files URI and add the query parameter role=publisher

Example - List Uploaded Files

```text
GET https://api.raet.com/mft/v1.0/files?role=publisher
```

## Optional Parameters

| Parameter Name | Value   | Description                                                                                               |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------- |
| pageIndex      | integer | The number of the page. (Default:0)                                                                       |
| pageSize       | integer | The maximum number of files to return per page. Acceptable values are 1 to 1000, inclusive. (Default: 20) |

Example - List Uploaded Files. This example shows how to list the files that have been uploaded by you. (role=publisher) using the sandbox Tenant

```text
GET/mft/v1.0/files
?role=publisher
&pageSize=10
HTTP/1.1

Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
```

If the request succeeds, the response includes a 200 OK HTTP status code, along with the paginated collection of the files that were uploaded by you.

By default, the paginated collection of files will be ordered by date descending.

Example - Response of List Uploaded Files

```text
HTTP/1.1 200
Content-Type: application/json

{
    "data": [
    {
        "fileId": "4a31f004-aab8-4419-9072-077c35074553",
        "fileName": "TestFile1.txt",
        "fileSize": 209715222,
        "tenantId": "sandbox",
        "businessType": {
            "id": 7100,
            "name": "7100"
        },
        "publisherId": "1b604f7e-d40f-466d-b9b0-ddeb3945df14",
        "uploadDate": "2021-01-10T21:05:41.937"
    },
    {
        "fileId": "62777c81-e83f-4888-8202-cf35ea2ca38b",
        "fileName": "TestFile2.txt",
        "fileSize": 2048,
        "tenantId": "sandbox",
        "businessType": {
            "id": 7100,
            "name": "7100"
        },
        "publisherId": "1b604f7e-d40f-466d-b9b0-ddeb3945df14",
        "uploadDate": "2021-01-10T08:07:41.113"
    }
    ],
    "pageIndex": 0,
    "pageSize": 20,
    "count": 2
}
```
