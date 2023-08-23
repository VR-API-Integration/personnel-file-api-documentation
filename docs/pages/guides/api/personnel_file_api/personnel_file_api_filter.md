---
title: Personnel File API - Filtering
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector, searhc
last_updated: 2023-08-16
sidebar: guides_sidebar
permalink: personnel_file_api_filter.html
folder: guides/api/personnel_file_api
topnav: topnav
---

## Overview

The `GET /v10/employees` endpoint provides a comprehensive mechanism to filter employee data using filtering expressions. While similar to some known filtering syntaxes, it's tailored to offer precise, effective filtering for this API. This document provides an in-depth guide for crafting these filter expressions.

## Basic Filtering

The foundational expression is structured as: `<property> <op> <value>`

Where:
- `<property>` is the name of a property, e.g., `surname` or `dateOfBirth`.
- `<op>` is the operator, which can be one of the following: 
  - `eq`: equals
  - `ne`: not equal
  - `lt`: less than
  - `le`: less than or equal to
  - `ge`: greater than or equal to
  - `gt`: greater than
- `<value>` is a literal value. It can be:
  - `null`
  - `true` or `false`
  - A number: e.g., `42`
  - A quoted string: e.g., `'John'`
  - A date (formatted as `YYYY-MM-DD`): e.g., `2023-04-15`
  - A date/time (formatted as `YYYY-MM-DD hh:mm:ss`): e.g., `2023-04-15 14:30:00`

**Example**:
```
GET /v10/employees?filter=surname eq 'Doe'
```
This fetches all employees with the surname 'Doe'.

When including a quote character (') within a quoted string, it's escaped by using two consecutive quotes (''). This convention allows parsers to differentiate between the end of a string and a double quote that's part of the string itself. For instance, to represent a value like a'b, you'd express it as 'a''b'. In the context of filtering a property named name for the value a'b, the complete filter would appear as name eq 'a'b'.

## Combining Expressions

### The `or` and `and` Operators
You can chain multiple filter expressions using the `or` and `and` operators:

**Example**:
```
GET /v10/employees?filter=surname eq 'Doe' or dateOfBirth lt 1990-01-01
```
This retrieves employees named 'Doe' or those born before January 1, 1990.

### The `not` Operator
The `not` operator negates a given filter expression:

**Example**:
```
GET /v10/employees?filter=not(surname eq 'Doe')
```
This will get employees whose surname isn't 'Doe'.

## Operator Precedence and Brackets

In filter expressions, operator precedence determines the order in which operators are evaluated when more than one exists in a query. By default, the `and` operator has higher precedence than the `or` operator. This means that in expressions like `A or B and C`, the `B and C` portion will be evaluated first, followed by the `or` operation. However, to alter the natural order of precedence or to make your queries more readable and explicit, you can use brackets. For instance, `(A or B) and C` ensures that the `or` operation is evaluated before the `and` operation. By incorporating brackets, you have the flexibility to craft complex queries while ensuring clarity and precision in the filter's intent.

## Supported Functions

We offer a select set of functions to enhance your filtering:

1. **startswith(<property>, 'string')**: Checks if a property starts with a given string.

   **Example**:
   ```
   GET /v10/employees?filter=startswith(surname, 'Jo')
   ```
   This will retrieve employees whose surname starts with 'Jo'.

2. **endswith(<property>, 'string')**: Checks if a property ends with a specified string.

   **Example**:
   ```
   GET /v10/employees?filter=endswith(surname, 'son')
   ```
   This fetches employees whose surname ends with 'son'.

3. **contains(<property>, 'string')**: Assesses if a property contains a particular string.

   **Example**:
   ```
   GET /v10/employees?filter=contains(organizationUnit, 'ICT')
   ```
   This brings up employees with the organization unit containing 'ICT' in its name.
