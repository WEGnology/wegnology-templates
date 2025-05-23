# IOs : Events

This template presents the use of functions associated with events, statistics, and parameter configurations available in the IOs API, including reading and interpreting the received payloads. Events are classified as:

 * Periodic;
 * On-change;
 * Events.

## Periodic

These publications, performed periodically by the device, present all configured information. The messages are sent by the API according to the interval defined on the device.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

´´´
{
    "ios":[
        {
            "active":false,
            "name":"periodico0",
            "ref_name":"DI0"
        },
        {
            "active":true,
            "name":"onchange0",
            "ref_name":"DI2"
        },
        {
            "active":false,
            "counter":97,
            "name":"contador0",
            "ref_name":"DI1"
        }
    ],
    "timestamp":1651520520
}
´´´

## On-change

These publications occur when the measured value changes by the percentage configured on the device.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "kind": "Rising",
    "name": "nivelOleoBaixo",
    "ref_name": "DI2",
    "timestamp_ns": 1713369139953123548,
    "active": true
}
```

## Events

Receives real-time events related to errors and execution information from the API. The publication is asynchronous.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive messages structured as follows:

```
{"description":"ios-api v0.5.0","type":"info"}
{"description":"accepting commands","type":"info"}
{"description":"periodic reports every 60 second(s)","type":"info"}
{"description":"capturing DI1 -> contador0","type":"info"}
{"description":"capturing DI0 -> periodico0","type":"info"}
{"description":"capturing DI2 -> onchange0","type":"info"}
```

## Statistics

Collects statistical data related to the volume of requests, responses, and errors, providing a counter that records the occurrence of each event. These data can be accessed periodically or by sending a request to the respective topic using an empty payload.

In the presented example, the request is made via a "Virtual Button" configured with the mentioned payload.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

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

## Parameter Configurations

Changes the configuration parameters related to the API on the device. When making a request, the previous configuration is overwritten by the new configuration sent.

IMPORTANT: After configuring, wait for the "accepting commands" message on the ios-api/v1/events topic before sending new commands.

### Example Request

To make a configuration request, post to the request topic a payload with the following structure:

```
{
    "debounce_ms": 2,
    "report_period": 20
}
```

In the example, the configuration request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "result":{
        "sucess":true
    }
}
```

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish an IOs connection on the device and configure it to facilitate visualization.
  4. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
