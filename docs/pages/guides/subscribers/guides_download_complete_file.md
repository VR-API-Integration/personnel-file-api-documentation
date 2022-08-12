---
title: Download complete file
tags: [subscriber, file, download, complete, api, library]
keywords: subscriber, file, download, complete, api, library
summary: This enpoint allows you to download the files that have been delivered to you.
last_updated: 3/31/2021
sidebar: guides_sidebar
permalink: guides_download_complete_file.html
folder: guides/subscribers
topnav: topnav
---

In order to use this download enpoint: 

- Create a Get request to the method's /files/[fileId] URI and add the query parameter role=subscriber

- Add the HTTP header Accept=application/octet-stream

Example - Download Request

```text
GET https://api.raet.com/mft/v1.0/files/[fileId]?role=subscriber

Example - Download Available File. This example shows how to download a file that was delivered to you using the Sandbox Tenant

GET/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=subscriber

HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx

Accept: application/octet-stream
```

If the request succeeds, the response includes a 200 OK HTTP status code, along with the bytes of the file.

Example - Successful response of Download Available File

```text
HTTP/1.1 200

<root>

<company>Visma Raet</company>

<product>File API</product>

<content>Sample File</content>

</root> 
```
