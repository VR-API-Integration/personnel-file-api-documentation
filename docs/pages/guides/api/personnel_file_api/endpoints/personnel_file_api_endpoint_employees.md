---
title: Personnel File API Endpoint - Employees
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_api_endpoint_employees.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---

<h2>GET /v1.0/employees</h2>
<p>This endpoint provides a list of all the employees and employments associated with a designated tenant. By default, the endpoint will return a list of all employees in a random order. However, the endpoint also supports advanced functionality, including paging, sorting, and querying.</p>
<p>With paging, you can retrieve the employee list in smaller, more manageable chunks. With sorting, you can arrange the employee list according to different criteria, such as alphabetical order or hire date. With querying, you can filter the employee list to show only employees that meet certain criteria, such as those with a specific job title or in a certain location.</p>
<table class="wrapped relative-table" style="width: 75.0811%;">
  <colgroup>
    <col style="width: 12.9282%;"/>
    <col style="width: 87.0718%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>query parameter</th>
      <th>
        <br/>
      </th>
    </tr>
    <tr>
      <td colspan="1">
        <strong>active</strong>
      </td>
      <td colspan="1">By including the "active" query parameter in your API request, you can exclude any employees from the results that are no longer employed by the company. This parameter can be useful if you only want to see a list of current employees, without including former employees who are no longer part of the workforce.</td>
    </tr>
    <tr>
      <td>
        <strong>skip=<em>n</em>
        </strong>
      </td>
      <td>By including the "skip" query parameter in your API request, you can skip the first n employees in the results list. This parameter can be useful if you only want to see employees beyond the first few entries, allowing you to focus on a particular subset of the employee list.</td>
    </tr>
    <tr>
      <td>
        <strong>top=<em>n</em>
        </strong>
      </td>
      <td>By including the "top" query parameter in your API request, you can limit the results to the top n employees in the list. This parameter can be useful if you only want to see the most important or relevant employees, without having to sift through a large number of entries.</td>
    </tr>
    <tr>
      <td>
        <strong>search=<em>value</em>
        </strong>
      </td>
      <td>By including the "search" query parameter in your API request, you can filter the employee list by searching for a given value in any of the applicable attributes, such as employee number, name, department, or function. This parameter can be useful if you need to quickly find employees who meet certain criteria, without having to manually search through the entire list.</td>
    </tr>
    <tr>
      <td colspan="1">
        <strong>filter=<em>expression</em>
        </strong>
      </td>
      <td colspan="1">
        <p>By including the "filter" query parameter in your API request, you can filter the results of the request based on a specified condition or set of conditions. The "filter" parameter accepts an expression in the <a href="/personnel_file_api_filtering.html">Filter Language<a>, which provides a flexible and powerful way to construct filter conditions.</p>
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <strong>sort=<em>attributes</em>
        </strong>
      </td>
      <td colspan="1">
        <p>By including the "sort" query parameter in your API request, you can sort the employee list based on one or more specified attributes. To use this parameter, you will need to provide a comma-separated list of attribute names that you wish to sort on.</p>
        <p>You can also specify a minus prefix to sort the attribute in descending order. For example, if you wanted to sort the employee list by last name in descending order, you would include the parameter "sort=-lastName".</p>
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <strong>include=contracts</strong>
      </td>
      <td colspan="1">By including the "include" query parameter in your API request, you can choose to include additional information in the search results. Specifically, including the "contracts" value for the "include" parameter will cause the endpoint to also return a list of all the employment contracts associated with the employee(s) in the search results.</td>
    </tr>
  </tbody>
</table>

<h2>GET /v1.0/employees/{nr}</h2>
<p>By using this API endpoint, you can retrieve detailed information about a specific employee, using their technical employee number. To use this endpoint, you will need to provide the employee number in the URL path.</p>
<p>Additionally, you can include query parameters to retrieve additional information about the employee. If you include the query parameter "include=contracts", the endpoint will return a list of all the employment contracts associated with the employee. If you include the query parameter "include=documents", the endpoint will return a list of all the documents that are linked to the employee's personnel file.</p>
<table class="wrapped">
  <colgroup>
    <col/>
    <col/>
  </colgroup>
  <tbody>
    <tr>
      <th>query parameter</th>
      <th>
        <br/>
      </th>
    </tr>
    <tr>
      <td colspan="1">
        <strong>include=contracts,documents</strong>
      </td>
      <td colspan="1">Include this query parameter to include contracts, documents or both in the search results</td>
    </tr>
  </tbody>
</table>
