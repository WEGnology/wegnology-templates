# Read Measurements Routine (30s)
Template responsible for reading measurements from an Edge Compute device every 30 seconds and preparing them for local SQL storage.

## Overview

This template handles:

* Dynamic assembly of read instructions
* Execution of periodic data collection (every 30 seconds)
* Conversion of raw device data into meaningful values

## Dependencies

This template assumes you have an Edge Compute device that is connected to the WEGnology Broker and is currently running Edge workflows. It also assumes the user has a basic understanding of the JavaScript programming language.

If you are new to Edge Compute, we recommend starting with the [Edge Compute Walkthrough](https://~exportplaceholderid-docs-url~/edge-compute/gateway-edge-agent/walkthrough/) before working with this template.


## How It Works

Every 30 seconds, the workflow:

* Builds a list of read instructions
* Sends the instructions to the device
* Receives raw data
* Converts the data into readable values
* Prepares an SQL statement to persist the measurements

### Result

* Measurements are collected from the device
* Values are properly converted
* Data is stored in the measures table

## License

Copyright &copy; 2022 WEGnology.

Licensed under the [MIT](https://github.com/WEGnology/wegnology-templates/blob/master/LICENSE.txt) license.