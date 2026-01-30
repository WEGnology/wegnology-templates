# AIOS : Analog Inputs and Outputs

This template presents the use of functions available in the AIOs API. It covers basic functions, such as reading inputs and configuring outputs, as well as informative functions, such as events and statistics. The functions are divided into:

 * Read inputs;
 * Configure output;
 * API events;
 * Statistics.

## Read Inputs

This function aims to obtain readings from the device's inputs, returning a list with the available inputs and their respective values. The request is made by sending an empty payload to the corresponding topic. In the example, this is done through a configured "Virtual Button".

Note: To read current, the "ShuntEnable" tag must be set to True.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
[
    {
        "group":"AI0",
        "values":[
            {
                "tag":"Current",
                "value":0,
                "unit":"uA"
            },
            {
                "tag":"CurrentPercent",
                "value":0,
                "unit":"%"
            }{
                "tag":"MaxCurrent",
                "value":25000,
                "unit":"mA"
            },
            {
                "tag":"RefCurrent",
                "value":20000,
                "unit":"mA"
            },
            {
                "tag":"ShuntEnable",
                "value":false
            }
        ]
    },
    {
        "group":"AI1",
        "values":[
            {
                "tag":"Voltage",
                "value":9000,
                "unit":"mV"
            },
            {
                "tag":"VoltagePercent",
                "value":100,
                "unit":"%"
            },
            {
                "tag":"MaxVoltage",
                "value":11750,
                "unit":"mV"
            },
            {
                "tag":"RefVoltage",
                "value":10000,
                "unit":"mV"
            }
        ]
    }
]
```

## Configure Output

This function allows writing a value to a tag, if the tag allows user writing, such as the "ShuntEnable" tag.

### Example Request

To make a change request, post to the request topic a payload with the following structure:

```
{
    "group":"AI0",
    "tag":"ShuntEnable",
    "value":1
}
```

In the example, the change request is made through a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
[
    {
        "group":"AI0",
        "tag":"ShuntEnable",
        "value":true,
        "result":{
            "sucess":true
        }
    }
]
```

## API Events

Receives, in real time, events related to errors and execution information from the API. The publication is asynchronous.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{"description":"accepting commands","type":"info"}
```

## Statistics

Collects statistical data related to the volume of requests, responses, and errors, providing a counter that records the occurrence of each event. This data can be accessed periodically or by sending a request to the respective topic using an empty payload.

In the example, the request is made through a "Virtual Button" configured with the specified payload.

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

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish an AIOs connection on the device and configure it to facilitate visualization.
  4. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
