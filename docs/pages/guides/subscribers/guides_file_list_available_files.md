---
title: File list of available files
tags: [subscriber, file, list, download, api, library]
keywords: subscriber, file, list, download, api, library
summary: This endpoint allows you to retrieve a paginated collection of the files that have been delivered to you.
last_updated: 4/22/2021
sidebar: guides_sidebar
permalink: guides_file_list_available_files.html
folder: guides/subscribers
topnav: topnav
---

In order to use this list endpoint: 

- Create a Get request to the method's /files URI and add the query parameter role=subscriber

Example - List Available Files

```text
GET https://api.raet.com/mft/v1.0/files?role=subscriber
```

## Optional Parameters

| Parameter Name | Value   | Description                                                                                               |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------- |
| pageIndex      | integer | The number of the page. (Default:0)                                                                       |
| pageSize       | integer | The maximum number of files to return per page. Acceptable values are 1 to 1000, inclusive. (Default: 20) |
| $filter        | string  | A query for filtering the file results. See the "Search for files" guide for the supported syntax.        |
| $orderBy       | string  | A query for sorting the file results. See the "Sort files" guide for the supported syntax.                |

Example - List Available Files. This example shows how to list the files that have been delivered to you. (role=subscriber) using the sandbox tenant

```text
GET/mft/v1.0/files
?role=subscriber
&pageSize=20
&$filter=businessType eq 8000
&$orderBy=uploadDate desc
HTTP/1.1

Host: api.raet.com
x-raet-tenant-id: sandbox
Authorization: Bearer xxxxxxxxx
```

If the request succeeds, the response includes a 200 OK HTTP status code, along with the paginated collection of the files that are available for you.

By default, only available files are shown. (Not downloaded files). In this case, the "count" field will return the total number of available files considering the query string specified in the parameter $filter. When a file is downloaded, it will not be shown by default anymore in the list, and the "count" field will be decreased to reflect the currently available files.

Example - Response of List Available Files

```text
HTTP/1.1 200
Content-Type: application/json

{
    "data": [
        {
            "downloaded": false,
            "fileId": "d92ffb21-7938-488b-a405-bcbc9e0a9696",
            "fileName": "sandbox_test_file.xml",
            "fileSize": 107,
            "tenantId": "sandbox",
            "businessType": {
                "id": 7101,
                "name": "7101"
        },
            "publisherId": "cfc6678d-06d8-41c7-acb5-7448a14dc917",
            "uploadDate": "2021-03-25T07:30:23.657Z"
        },
        {
            "downloaded": false,
            "fileId": "c5d7438e-5c29-47e7-b518-01e5a39d6711",
            "fileName": "sandbox_test_file.txt",
            "fileSize": 33,
            "tenantId": "sandbox",
            "businessType": {
                "id": 7101,
                "name": "7101"
        },
            "publisherId": "cfc6678d-06d8-41c7-acb5-7448a14dc917",
            "uploadDate": "2021-03-25T07:30:23.657Z"
        },
        {
            "downloaded": false,
            "fileId": "f0d109df-b933-44f9-92d7-cca525ef120a",
            "fileName": "sandbox_test_file.csv",
            "fileSize": 76,
            "tenantId": "sandbox",
            "businessType": {
                "id": 7101,
                "name": "7101"
        },
            "publisherId": "cfc6678d-06d8-41c7-acb5-7448a14dc917",
            "uploadDate": "2021-03-25T07:30:23.657Z"
        }
    ],
    "pageIndex": 0,
    "pageSize": 20,
    "count": 3
}
```
