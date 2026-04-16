# Aggregate & Publish Routine (5m)

Template responsible for aggregating stored measurements from the local SQL database and publishing processed values every 5 minutes.

## Overview

This template handles:

* Querying stored measurements from the database
* Aggregating data over a 5-minute window
* Selecting values based on configured aggregation rules
* Publishing processed state back to the device
* Cleaning up old data from the database

## Dependencies

This template assumes you have an Edge Compute device that is connected to the WEGnology Broker and is currently running Edge workflows.

If you are new to Edge Compute, we recommend starting with the [Edge Compute Walkthrough](https://~exportplaceholderid-docs-url~/edge-compute/gateway-edge-agent/walkthrough/) before working with this template.

## Applied Aggregations

For each attribute, different types of aggregation are calculated within a 5-minute window:

inst: instant value (latest value available in the period)
max: highest value recorded in the period
min: lowest value recorded in the period
avg: average value over the period

## Result

* Measurements are aggregated into meaningful metrics
* Device state is updated with processed values
* Old data is removed from the database

## License

Copyright © 2022 WEGnology. All rights reserved.

Licensed under the [MIT](https://github.com/WEGnology/wegnology-templates/blob/master/LICENSE.txt) license.