# Create Measurements Table

Ensures the measurements table is created during device initialization or reconnection.

## Dependencies

This template assumes you have an Edge Compute device that is connected to the WEGnology Broker and is currently running Edge workflows.
If you are new to Edge Compute, we recommend starting with the [Edge Compute Walkthrough](https://~exportplaceholderid-docs-url~/edge-compute/gateway-edge-agent/walkthrough/) before working with this template.


## Table Creation Routine

This routine ensures that the measurements table exists:

### What It Does
Opens a SQL connection
Executes an idempotent table creation statement

### SQL Statement

```sql
CREATE TABLE IF NOT EXISTS measures (
  id INTEGER PRIMARY KEY,
  timestamp INTEGER NOT NULL,
  attribute TEXT DEFAULT NULL,
  value REAL DEFAULT NULL
);
```

### Result

On success, the database is ready to receive measurement data.

## Licenca

Copyright © 2022 WEGnology.

Licensed under the [MIT](https://github.com/WEGnology/wegnology-templates/blob/master/LICENSE.txt) license.