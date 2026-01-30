# SSU : Data Block

This example demonstrates the service interfaces for reading metrological and billing data in Normal or Extended formats, as specified by the NBR 14522 standard, available in the SSU API. Its main functions include:

 * Data Block
 * Extended Data Block
 * Events
 * Statistics

## Data Block

This function is responsible for receiving the basic data blocks from an SSU communication. Publications are received on the corresponding response topic.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "sec_counter":900,
    "billing_indicator":false,
    "ufer_indicator":false,
    "ufer_dmcr_capacitive":true,
    "ufer_dmcr_inductive":true,
    "season":"Peak",
    "tariff_type":"Blue",
    "reactive_tariff_status":"Activated",
    "active_pulses_counter":10,
    "reactive_pulses_counter":1
}
```

## Extended Data Block

This function is responsible for receiving the extended data blocks from an SSU communication. Publications are received on the corresponding response topic.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "sec_counter":900,
    "billing_indicator":false,
    "ufer_indicator":false,
    "reactive_tariff":"Inductive",
    "active_tariff":1,
    "quadrant":3,
    "reactive_tariff_status":"Activated",
    "active_pulses_counter":10,
    "reactive_pulses_counter":1
}
```

## Events

This function is responsible for receiving, in real time, events related to errors and execution information from the API. The publication of these events occurs asynchronously.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive messages structured as follows:

```
{"description":"accepting commands","type":"info"}
{"description":"invalid checksum","type":"error"}
{"description":"unexpected frame size (16 bytes)","type":"error"}
```

## Statistics

Collects statistical data related to the volume of requests, responses, and errors, providing a counter that records the occurrence of each event. This data can be accessed periodically or by sending a request to the respective topic with an empty payload.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "counters":{
        "error":0,
        "incoming":4,
        "invalid":2,
        "outgoing":6
    },
    "runtime":155
}
```

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Make an SSU connection on the device to facilitate visualization.
  4. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
