---
title: File download uploaded files
tags: [publisher, file, upload, download, api, library]
keywords: publisher, file, upload, download, api, library
summary: This endpoint allows you to download the files that have been uploaded by you.
last_updated: 21/01/2022
sidebar: guides_sidebar
permalink: guides_file_download_uploaded_files.html
folder: guides/publishers
topnav: topnav
---

In order to use this download endpoint: 
- Create a Get request to the method's /files/[fileId] URI and add the query parameter role=publisher
- Add the HTTP header Accept=application/octet-stream

Example - Download Request

```text
GET https://api.raet.com/mft/v1.0/files/[fileId]?role=publisher
```

Example - Download uploaded file. This example shows how to download a file that was uploaded by you using the Sandbox Tenant

```text
GET/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=publisher

HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx

Accept: application/octet-stream
```

If the request succeeds, the response includes a 200 OK HTTP status code, along with the bytes of the file.

Example - Successful response of Download uploaded File

```text
HTTP/1.1 200

<root>

<company>Visma Raet</company>

<product>File API</product>

<content>Sample File</content>

</root> 
```
