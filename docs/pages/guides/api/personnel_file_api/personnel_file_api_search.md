# Searching with Expressions in the `GET /v10/employees` Endpoint

The `GET /v10/employees` endpoint supports a versatile and powerful mechanism to search through employee data using search expressions. This document provides a detailed guide to help you construct effective search expressions.

## Basic Searching
At its simplest, a search expression can be a single word you're looking for.

**Example**: 
```
GET /v10/employees?search=john
```
This searches for all employees with the term "john".

## Operators

### The `OR` Operator
To search for records that match one of several terms, use the `OR` operator. It must be in uppercase.

**Example**:
```
GET /v10/employees?search=jan OR klaas
```
This retrieves all employees with the term "jan" or "klaas".

### The `AND` Operator
The `AND` operator retrieves records that match both terms.

**Example**:
```
GET /v10/employees?search=developer AND senior
```
This will look for employees who are both "developer" and "senior".

### The `NOT` Operator
The `NOT` operator excludes records that match the specified term.

**Example**:
```
GET /v10/employees?search=developer NOT junior
```
This retrieves employees who are "developers" but not "juniors".

## Operator Precedence with Brackets
You can control the order of operation using brackets. Expressions inside brackets will be evaluated first.

**Example**:
```
GET /v10/employees?search=john AND (developer OR designer)
```
This searches for employees named "john" who are either "developers" or "designers".

## Searching for Phrases
If you want to look for a word that contains a space, or if the term you are looking for is also a keyword (like "AND", "OR", "NOT"), you can enclose the term in double quotes.

**Example**:
```
GET /v10/employees?search="product manager"
```
This retrieves all employees with the term "product manager".

**Another Example**:
```
GET /v10/employees?search="AND"
```
This searches specifically for the term "AND", and not as a keyword.

## Conclusion
The `GET /v10/employees` search expressions offer robust and flexible searching capabilities. Make sure to use the right combination of terms and operators to refine and optimize your queries. Happy searching!