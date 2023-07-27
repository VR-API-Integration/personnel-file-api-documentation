---
title: Personnel File Connector Endpoint - Documents
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_connector_endpoint_documents.html
folder: guides/api/personnel_file_connector/endpoints
topnav: topnav
---
<h2>GET /v1.0/documents</h2>
<p>This API endpoint allows you to list all the documents associated with a designated tenant. By default, the endpoint will return a list of all documents in a random order. However, the endpoint also supports advanced functionality, including paging, sorting, and querying.</p>
<p>With paging, you can retrieve the document list in smaller, more manageable chunks. With sorting, you can arrange the documents list according to different criteria, such as alphabetical order or hire date. With querying, you can filter the document list to show only documents that meet certain criteria, such as those with a specific document description or in a certain location.</p>
<table class="relative-table wrapped" style="width: 75.0811%;">
  <colgroup>
    <col style="width: 12.9282%;"/>
    <col style="width: 87.0718%;"/>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <strong>skip=<em>n</em>
        </strong>
      </td>
      <td>By including the "skip" query parameter in your API request, you can skip the first n documents in the results list. This parameter can be useful if you only want to see documents beyond the first few entries, allowing you to focus on a particular subset of the document list.</td>
    </tr>
    <tr>
      <td>
        <strong>top=<em>n</em>
        </strong>
      </td>
      <td>By including the "top" query parameter in your API request, you can limit the results to the top n documents in the list. This parameter can be useful if you only want to see the most important or relevant documents, without having to sift through a large number of entries.</td>
    </tr>
    <tr>
      <td>
        <strong>search=<em>value</em>
        </strong>
      </td>
      <td>By including the "search" query parameter in your API request, you can filter the document list by searching for a given value in any of the applicable attributes, such as employee number, document description or expiration date. This parameter can be useful if you need to quickly find documents that meet certain criteria, without having to manually search through the entire list.</td>
    </tr>
    <tr>
      <td colspan="1">
        <strong>filter=<em>expression</em>
        </strong>
      </td>
      <td colspan="1">
        <p>By including the "filter" query parameter in your API request, you can filter the results of the request based on a specified condition or set of conditions. The "filter" parameter accepts an expression in the <ac:link>
            <ri:page ri:content-title="OData Filter language"/>
            <ac:plain-text-link-body><![CDATA[OData Filter Language]]></ac:plain-text-link-body>
          </ac:link>, which provides a flexible and powerful way to construct filter conditions.</p>
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <strong>sort=<em>attributes</em>
        </strong>
      </td>
      <td colspan="1">
        <p>By including the "sort" query parameter in your API request, you can sort the employee list based on one or more specified attributes. To use this parameter, you will need to provide a comma-separated list of attribute names that you wish to sort on.</p>
        <p>You can also specify a minus prefix to sort the attribute in descending order. For example, if you wanted to sort the document list by description in descending order, you would include the parameter "sort=-description".</p>
      </td>
    </tr>
  </tbody>
</table>
<h2>GET /v1.0/documents/{id}</h2>
<p>With this API endpoint, you can retrieve detailed information about a specific document in the personnel file archive, identified by its unique technical identifier. In the response, you will receive information about the document's content, metadata, and associated employee and employment contract, if applicable. To use this endpoint, simply provide the document identifier in the URL path.</p>
<h2>GET /v1.0/documents/{id}/content</h2>
<p>By using this API endpoint, you can retrieve the content of a specific document identified by its unique technical identifier. To use the endpoint, you will need to provide the identifier in the URL path.</p>
<table class="relative-table wrapped" style="width: 75.2758%;">
  <colgroup>
    <col style="width: 12.6833%;"/>
    <col style="width: 87.3167%;"/>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <strong>pdf</strong>
      </td>
      <td>You can use the "pdf" query parameter in your API request to retrieve the content of the document in PDF format. Simply include "pdf" as a query parameter in your request, and the response will contain the document's content in PDF format. If you don't include the "pdf" parameter, the default response will be in the original format of the document.</td>
    </tr>
  </tbody>
</table>
<h2>POST /v1.0/documents</h2>
<p>With this API endpoint, you can add a new document to the personnel file archive. The attributes 'employeeNumber' and 'contractNumber' need to be used to link the new document to an employee and optionally a specific employment contract of said employee.</p>
<h2>PUT /v1.0/documents/{id}</h2>
<p>With this API endpoint, you can replace the content of an existing document, identified by its unique technical identifier. To use this endpoint, simply provide the document identifier in the URL path. The old content of the document is still available as a previous version of the document.</p>
<h2>DELETE /v1.0/documents/{id}</h2>
<p>With this API endpoint, you can remove a document from the personnel file archiveTo use this endpoint, simply provide the document identifier in the URL path.. The document is identified by its unique technical identifier.</p>
