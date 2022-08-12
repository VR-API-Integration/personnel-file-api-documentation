---
title: File delete
tags: [subscriber, file, delete, api, library]
keywords: subscriber, file, delete, api, library
summary: This endpoint allows to delete a file you are subscribed to. This will not delete the file for everyone, just for the app that is requesting it.
last_updated: 3/26/2021
sidebar: guides_sidebar
permalink: guides_delete_file.html
folder: guides/subscribers
topnav: topnav
---

In order to use this endpoint: 

- Create a Delete request to the method's /files/[fileId] URI and add the query parameter role=subscriber
- Add the HTTP header Accept=application/octet-stream

Example - Delete File

```text
DELETE https://api.raet.com/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=subscriber

HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx

If the request succeeds, the response includes a 204 No Content HTTP status code.

Example - Response of Delete File

HTTP/1.1 204
```
