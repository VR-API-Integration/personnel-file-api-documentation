The Personnel File API allows you to filter the results of endpoints returning employees and documents using a filter language. The API supports the following features:

**Comparisons**
To filter on a specific attribute, you can use the name of the attribute followed by a comparison operator and the value to compare against. For example, to filter on employees with the last name "Smith", you could use the expression ?filter=lastName eq 'Smith'. The OData Filter Language supports a wide range of comparison operators, including "eq" (equals), "ne" (not equals), "gt" (greater than), "lt" (less than), "ge" (greater than or equal to), and "le" (less than or equal to). By using these operators in combination with attribute values, you can quickly and easily filter the data you need from your API.

**Logical operators** 
In addition to comparisons, you can use logical operators such as "and", "or", and "not" to construct more complex filter expressions. For example, to filter on employees with the last name "Smith" and a date of birth after January 1, 1990, you could use the expression $filter=lastName eq 'Smith' and dateOfBirth gt 1990-01-01. By using logical operators to combine comparison conditions, you can filter on multiple attributes simultaneously, allowing you to retrieve the exact data you need from your API.

**Pattern matching**
The filter language also supports several wildcard operators that can be used for string comparisons. These include "contains", "startswith", and "endswith". For example, to filter on employees with the initials "JL", you could use the expression $filter=startswith(initials,'J') and endswith(initials,'L'). By using these operators, you can filter on attribute values that match a specific pattern or substring, making it easy to search for specific data within your API.

lastName eq 'Smith'	Filters employees with the last name "Smith".
dateOfBirth gt 1990-01-01	Filters employees with a date of birth after January 1, 1990.
lastName eq 'Smith' and dateOfBirth gt 1990-01-01	Filters employees with the last name "Smith" and a date of birth after January 1, 1990.
contains(initials, 'JL')	Filters employees whose initials contain the substring "JL".
endswith(lastName, 'son')	Filters employees whose last name ends with the string "son".
nr eq '12345' or nr eq '67890'	Filters employees with employee number equal to either "12345" or "67890".

Overall, by using the filter language to filter your API results, you can quickly and easily retrieve the employees and documents you need based on specific conditions. Whether you need to filter on a single attribute or multiple attributes simultaneously, the Youforce Dossier API makes it easy to filter and retrieve the exact employees and documents you need in your application.