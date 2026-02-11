# MODBUS : Data Handling

This template demonstrates the use of functions related to data handling and acquisition of data and status. The example is organized into the following sections:

 * Request for publishing peripheral register data;
 * Request for writing data to peripheral registers;
 * Request for peripheral status.

## Data Publication Request

Allows you to request the immediate publication of a peripheral's data by sending a payload containing:

 * Communication protocol;
 * Peripheral UID on the MODBUS network;
 * Timeout;
 * Object containing a list of read instructions.

### Example Request

To make a publication request, you need to post to the request topic a payload with the following structure:

```
{
    "protocol": {
        "modbusRtu":{
        "interface_name": "ttyS0"
        }
    },
    "unit_id": 1,
    "timeout": 10,
    "instructions": [
        {
        "function": "ir",
        "address": 9000,
        "size": 3,
        "registers": [
            {
            "name": "IR0ETH",
            "datatype": "u16",
            "scale": 1.0,
            "on_change": 0.0
            }
        ]
        }
    ]
}
```


In this example, the publication request is made via a "Virtual Button" that contains the structured payload for the request topic.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data": {
        "code": 200,
        "message": {
            "elapsed_time": 1420,
            "protocol": {
                "modbusTcp": {
                    host": "192.168.10.1:502"
                }
            },
            "result": [
                {
                "data": [0, 10, 20],
                "success": true
                }
            ],
            "unit_id": 1
        },
        "service": "RequestMbRead",
        "success": true
    },
    "timestamp": 1712842180
}
```


## Data Write Request

Allows you to request the immediate writing of data to one or more registers of a peripheral by sending a payload similar to that used for publication. The difference is in the object, which must contain a list of information to be written to the register.

### Example Request

To make a write request, you need to post to the request topic a payload with the following structure:

```
{
    "protocol": {
        "modbusTcp":{
            "host": "192.168.10.1:502"
        }
    },
    "unit_id": 1,
    "timeout": 1000,
    "instructions": [
        {
            "function": "hr",
            "address": 1000,
            "size": 3,
            "values": [10, 20, 30]
        },
    ...
    ]
}
```


In this example, the write request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data": {
        "code": 200,
        "message": {
        "elapsed_time": 7062,
        "protocol": {
            "modbusTcp": {
                "host": "192.168.10.1:502"
            }
        },
        "result": [
            {
                "data": "Write succeeded",
                "success": true
            }
        ],
        "unit_id": 1
        },
        "service": "RequestMbWrite",
        "success": true
    },
    "timestamp": 1712842180
}
```


# Status Request

Requests the MODBUS communication status of each registered peripheral, returning an object that contains the following information for each peripheral:

 * Number of errors;
 * Peripheral ID;
 * Last measurement;
 * Number of measurements performed;
 * Peripheral name.

In the example, the request is made via a "Virtual Button" containing an empty payload.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data":{
        "code":200,
        "message":[
            {
                "errors_count":1,
                "id":"65e6023d31e51f658b718c95",
                "last_measure_ts":1723477982588,
                "measures_count":1136,
                "name":"plc410"
            },
            {
                "errors_count":0,
                "id":"95e9e89588d2b523e4b7b8f9",
                "last_measure_ts":1723477983051,
                "measures_count":1137,
                "name":"MMW03"
            }
        ],
        "service":"RequestPeripheralsStatus",
        "success":true
        },
    "timestamp": 1712842180
}
```

## Setup

  1. Import this template into the WEGnology platform under the Embedded Workflows section;
  2. Deploy the example to the device;
  3. Establish a Modbus connection on the device to facilitate visualization;
  4. Use the "Virtual Button" to perform the tests.

---

Copyright (c) 2025 WEGnology
