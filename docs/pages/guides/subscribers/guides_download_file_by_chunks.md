---
title: Download file by chunks
tags: [subscriber, file, download, chunk, api, library]
keywords: subscriber, file, download, chunk, api, library
summary: These endpoints allow you to download chunks of files that have been delivered to you. 
last_updated: 3/31/2021
sidebar: guides_sidebar
permalink: guides_download_file_by_chunks.html
folder: guides/subscribers
topnav: topnav
---

In order to download files by chunks you need to use these endpoints:

- Retrieve file size with a Head request

- Retrieve chunks of the file.

## Retrieve file size

File API allows you to download chunks of files that have been delivered to you. This endpoint will be used to check if this capability is in place for the resource.

- Create a Head request to the method's /files/[fileId] URI and add the query parameter role=subscriber

Example - Check Available File can be downloaded by chunks

```text
HEAD/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=subscriber

HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx
```

If the request succeeds, the response includes a 200 OK HTTP status code, along with the headers:

- Content-Length with the size of the requested file
- Accept-Ranges with the range unit accepted

Example - Successful response of Check Available File can be downloaded by chunks

```text
HTTP/1.1 200

Content-Length:107

Accept-Ranges:bytes
```

## Retrieve chunks of a file

File API allows you to download chunks of files that have been delivered to you.

- Create a Get request to the method's /files/[fileId] URI and add the query parameter role=subscriber
- Add the HTTP header Accept: application/octet-stream
- Add the HTTP header Range: bytes=firstByte-lastByte where firstByte is the first byte of the chunk you want to download and lastByte is the last one.

Example - Download first 50 bytes of an Available File. This example shows how to download a chunk of a file that was delivered to you using the Sandbox Tenant

```text
GET/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=subscriber HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx

Accept: application/octet-stream

Range: bytes=0-49
```

If the request succeeds, the response includes a 206 Partial Content HTTP status code, along with the bytes of the chunk and the headers:

- Content-Range with the range retrieved and total file size
- Content-Disposition with the value attachment; filename=name of the file

Example - Successful response of Download first 1024 bytes of an Available File

```text
HTTP/1.1 206

Content-Length: 50

Content-Range: bytes 0-49/107

Content-Disposition:attachment; filename=sandbox_test_file.xml

<root>
<company>Visma Raet</company>
<product>Fi
```

### Not satisfiable range

When the lower limit of the range is bigger than the last byte of the file, the request will retrieve a 416 error.
Example - Request not satisfiable range when Download Range out of Available File bounds

```text
GET/mft/v1.0/files/d92ffb21-7938-488b-a405-bcbc9e0a9696

?role=subscriber HTTP/1.1

Host: api.raet.com

x-raet-tenant-id: sandbox

Authorization: Bearer xxxxxxxxx

Accept: application/octet-stream

Range: bytes=107-110
```

The response includes a 416 Range Not Satisfiable HTTP status code, along with the header:

- Content-Range with the accepted range unit and the file size

Example - Response - Error not satisfiable range when Download Range out of Available File bounds

```text
HTTP/1.1 206

Content-Range: bytes */107

{
    "correlationId": null,
    "message": "Range not satisfiable.",
    "errorCode": "416",
    "exception": null
}
```
