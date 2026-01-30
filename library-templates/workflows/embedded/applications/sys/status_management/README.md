# SYS : State Management

This example demonstrates the service interfaces for reading status and system configuration, related to the SYS API. These interfaces are divided into:

 * Request Last Status;
 * Periodic Status;
 * Change Periodic Status Interval.

## Request Last Status

The last status published to the topic can be retrieved at any time using this function. To do so, simply publish an empty payload to the specific topic. In this example, this action is performed using a "virtual button".

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "system":{
        "board":"BT500CB.00_P03",
        "build_id":"",
        "cpu_avg":3.4313700199127197,
        "cpu_freq":996,
        "cpu_max":3.4313700199127197,
        "cpu_min":3.4313700199127197,
        "cpu_usage":3.4313700199127197,
        "data_disk_total":1404379136,
        "data_disk_usage":831102976,
        "..."
    }
}
```

## Periodic Status

The status is published periodically by this API, with the publication interval defined by the API's own configuration file. The published payload is identical to that shown in the last status request, but in this case, no request is required to receive it.

## Change Periodic Status Interval

The publication interval can be changed by this function, requiring a payload containing only the desired interval in seconds.

### Example Request

To request a change, you must post to the request topic a payload with the following structure:

```
{"interval":20}
```

In this example, the change request is made using a "Virtual Button", which contains the payload structured for sending to the request topic.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "success": true,
    "interval": 20
}
```

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
