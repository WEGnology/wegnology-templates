# Features : Data Persistence

This template explores how to perform data persistence after losing connection with the WEGnology platform, ensuring data is stored even without a connection.

## Workflow

The presented example will create a local database on the device, called "Persistence". In this database, a table named "Received" will be created to store the received information. All messages published to the persistence topic will be processed by the workflow, which will determine whether or not there is a connection to the WEGnology platform. If a connection exists, the configured messages will be published as usual.

When a disconnection from the platform is detected, the workflow will store the messages in the device's database. Every 30 seconds, a timer will trigger a signal to check if the device has re-established its connection to the platform. If reconnection is confirmed, all stored messages will be gradually published to the platform, thus ensuring the preservation of device messages during the period of lost connection.

## Setup

  1. Import this template into the WEGnology platform in the Application Workflows section.
  2. Deploy the workflow to the device.
  3. Use another workflow to receive messages through MODBUS, IOs, etc.
  4. Publish the received messages to the "persistence" topic.

---

Copyright (c) 2025 WEGnology
