# EEA : SQL

In this template, the use of registered functions related to the database, available directly on the WEGnology platform, will be demonstrated. These functions are intended to create and manage the database, being divided into:

 * sql_create_db;
 * sql_query.

## Sql_create_db

This function creates a database that will be stored on the device.

### Using the function

To use the function, it is necessary to add a registered function node, enter "sql_create_db" in the function name field, and in the inputs area insert the database name as a string. This information can be provided via a payload or be predefined. In the example presented, the information was predefined.

The function's return consists only of the returnCode, if configured.

### Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: invalid name;
 * 101: the database already exists;
 * 102: failed to create the database.

## Sql_query

This function executes an SQL query, allowing any type of command supported by a query.

### Using the function

To use the function, it is necessary to add a registered function node, enter "sql_query" in the function name field, and in the inputs area (as a string) provide the following information:

 * Database name (db_name);
 * SQL command (sql);
 * Parameters, separated by commas.

This information can be provided via a payload or be predefined. In the example presented, the information was predefined.

In the Outputs area, you must specify the payload in which the information will be loaded, in JSON format.

### Return Example

In this example, the values contained in a table of the database were requested. Otherwise, the return will only present the returnCode with a value.

```
"data":{
    "dtb_output": "[[1,"prim","seg"]]"
    "returnCode": 0
},
```

### Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: invalid or inaccessible database;
 * 101: failed to execute the query;
 * 102: the provided buffer size for the output is insufficient.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example on the device.
  3. Use the "Virtual Button" to perform the tests.

## Observations

The template initializes by creating a database on the device, allowing the manipulation of this database.

---

Copyright (c) 2025 WEGnology
