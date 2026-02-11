# BLE : Communication with Devices

This example presents the functions of the service interfaces for communication with BLE (Bluetooth Low Energy) devices, provided by the BLE API, including reading and interpreting received payloads. The API functions are:

 * Read characteristic;
 * Write characteristic;
 * Observe characteristic;
 * Forced disconnection;
 * Nearby devices;
 * Monitor events;
 * Monitor statistics.

## Read Characteristic

This function allows reading a characteristic from a connected device by sending a payload containing the MAC address, as well as the GATT service and characteristic identifiers.

### Example Request

To make a read request, post to the request topic a payload with the following structure:

```
{
    "adress": "38:31:ac:00:00:01",
    "service": "d3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristics": "d3ed1002-6869-7abd-c849-7c46f3c03588"
}
```

In this example, the read request is made through a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "meta":{
        "requester":"",
        "elapsed":0,
        "result":{
            "code":0,
            "message":""
        }
    },
    "address":"38:31:ac:00:00:01",
    "service":"d3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristic":"d3ed1002-6869-7abd-c849-7c46f3c03588",
    "value":""
}
```

## Write Characteristic

This function allows changing a characteristic of a connected device by sending a payload containing the MAC address, the GATT service and characteristic identifiers to be changed, and the new value.

### Example Request

To make a write request, post to the request topic a payload with the following structure:

```
{
    "adress": "38:31:ac:00:00:01",
    "service": "3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristics": "d3ed1001-6869-7abd-c849-7c46f3c03588",
    "value": AAI=
}
```

In this example, the write request is made through a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "meta":{
        "requester":"",
        "elapsed":0,
        "result":{
            "code":0,
            "message":""
        }
    },
    "address":"38:31:ac:00:00:01",
    "service":"d3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristic":"d3ed1001-6869-7abd-c849-7c46f3c03588",
    "value":"AAI="
}
```

## Observe Characteristic

This function requests notification of changes in the value of a device's characteristic by sending a payload containing the MAC address, the GATT service and characteristic identifiers, and options.

Note: The device's characteristic must support the BLE Notify function.

### Example Request

To make a notification request, post to the request topic a payload with the following structure:


```
{
    "adress":"38:31:ac:00:00:01",
    "service":"d3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristics":"d3ed1001-6869-7abd-c849-7c46f3c03588",
    "options":[
        {
            "timeout":10,
            "count":10
        }
    ]
}
```

In this example, the notification request is made through a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "meta":{
        "requester":"",
        "elapsed":0,
        "result":{
            "code":0,
            "message":""
        }
    },
    "address":"38:31:ac:00:00:01",
    "service":"d3ed1000-6869-7abd-c849-7c46f3c03588",
    "characteristic":"d3ed1001-6869-7abd-c849-7c46f3c03588",
    "value":"AAI="
}
```

Note: The characteristic monitoring remains active while the attribute "meta.result" is not present in the response.

## Forced Disconnection

This function allows forced disconnection of a device, interrupting active notification operations. To do this, send a payload containing only the device's MAC address to the respective topic.

### Example Request

To make a disconnection request, post to the request topic a payload with the following structure:

```
{
    "adress":"38:31:ac:00:00:01",
}
```

In this example, the disconnection request is made through a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "meta":{
        "requester":"",
        "elapsed":0,
        "result":{
            "code":0,
            "message":""
        }
    },
    "address":"38:31:ac:00:00:01"
}
```

## Nearby Devices

This function scans for nearby devices, returning a list of those available for connection. To do this, send an empty payload to the request topic and the list of found devices will be published directly to the response topic. In the example, this is done through a configured "Virtual Button".

Note: The result of this operation may impact or be impacted by other operations if executed simultaneously.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "meta":{
        "elapsed":15,
        "result":{
            "code":0
        }
    }"devices":[
        {
            "address":"38:31:ac:00:00:01",
            "name":"1088907897",
            "connected":true,
            "rssi":-78,
            "tx_power":12,
            "manufacturer_data":{
                "1575":[6, 10, 74, 27, 27, 15, 0,
                        0, 0, 2, 2, 1
                ]
            }
        },
        "..."
    ]
}
```

## Monitor Events

This function aims to monitor events performed within the BLE API, returning information whenever there is an update in the topic.

## Monitor Statistics

This function periodically returns API usage statistics, including message counters and the list of connected devices.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "runtime":0,
    "counters":{
        "request":{
            "notify":0,
            "read":0,
            "write":0
        },
        "response":{
            "notify":0,
            "read":0,
            "write":0
        },
        "errors":{
            "notify":0,
            "read":0,
            "write":0
        }
    },
    "adapters":[
        {
            "name":"hci0",
            "bus":"UART",
            "address":"",
            "status":"",
            "rx":0,
            "tx":0
        },
        {
            "name":"hci1",
            "bus":"SPI",
            "address":"",
            "status":"",
            "rx":0,
            "tx":0
        },
    ]
}
```

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish a connection with a Bluetooth device.
  4. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
