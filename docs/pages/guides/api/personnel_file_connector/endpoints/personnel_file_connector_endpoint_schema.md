---
title: Personnel File Connector Endpoint - Schema
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_connector_endpoint_schema.html
folder: guides/api/personnel_file_connector/endpoints
topnav: topnav
---

<h2>GET /v1.0/schema/categories</h2>
<p>This API endpoint allows you to list all the documents associated with a designated tenant. By default, the endpoint will return a list of all documents in a random order. However, the endpoint also supports advanced functionality, including paging, sorting, and querying.</p>
<p>With paging, you can retrieve the document list in smaller, more manageable chunks. With sorting, you can arrange the documents list according to different criteria, such as alphabetical order or hire date. With querying, you can filter the document list to show only documents that meet certain criteria, such as those with a specific document description or in a certain location.</p>

<h2>GET /v1.0/schema/category/{id}</h2>
<p>With this API endpoint, you can retrieve detailed information about a specific document in the personnel file archive, identified by its unique technical identifier. In the response, you will receive information about the document's content, metadata, and associated employee and employment contract, if applicable. To use this endpoint, simply provide the document identifier in the URL path.</p>

<h2>GET /v1.0/schema/folders</h2>
<p>By using this API endpoint, you can retrieve the content of a specific document identified by its unique technical identifier. To use the endpoint, you will need to provide the identifier in the URL path.</p>

<h2>GET /v1.0/schema/employee</h2>
<p>By using this API endpoint, you can retrieve the content of a specific document identified by its unique technical identifier. To use the endpoint, you will need to provide the identifier in the URL path.</p>

<h2>GET /v1.0/schema/document</h2>
<p>By using this API endpoint, you can retrieve the content of a specific document identified by its unique technical identifier. To use the endpoint, you will need to provide the identifier in the URL path.</p>


