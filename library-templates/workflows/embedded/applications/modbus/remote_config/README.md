# MODBUS : Remote Configuration

This template demonstrates the use of the MODBUS API to remotely configure peripherals and the system. The functions are divided into:

 * Request to check currently configured peripherals
 * Request to add new peripherals
 * Request to remove configured peripherals
 * Serial port configuration request
 * Runtime configuration request

## Currently Configured Peripherals

When using the API function that checks the peripherals configured on the device, an object will be returned containing the following information for each peripheral:

 * Peripheral ID;
 * Peripheral Name;
 * Communication Protocol;
 * Registers;
 * MODBUS UID.

In the example, the request is made using a "Virtual Button" containing an empty payload.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data":{
        "code": 200,
        "message": [
            {
                "endianess":"big",
                "id": "<peripheral_wnology_id>",
                "name": "<peripheral_name1>",
                "protocol":{
                "modbusRtu":{
                "interface_name": "ttySX"
                }
            },
            "registers":[
                {
                    "address": 9000,
                    "dtype": "u16",
                    "events": null,
                    "function": "ir",
                    "information":{
                        "alarm_high": null,
                        "alarm_low": null,
                        "avg": true,
                        "diff": true,
                        "last": true,
                        "max": true,
                        "min": true
                     },
                    "name": "reg1",
                    "scale": 1.0
                },
            ...
            ],
            "unitId": 5
            },
            ...
        ],
        "service": "RequestPeripheralsGet",
        "success": true
    },
    "timestamp": 1730392842
}
```


## Add New Peripherals

This API function allows you to add new peripherals (modbus-rtu or modbus-tcp) to communicate via API.

### Example Request

To add a new peripheral, you must post to the request topic a payload with the following structure:

```
[
    {
        "name":"API_Test",
        "id":"67efd1de83876974d1ee2280",
        "protocol":{
            "modbusTcp":{
                "host":"192.168.2.11:502"
            }
        },
        "registers":[
            {
                "address":9000,
                "function":"ir",
                "name":"IR0ETH",
                "dtype":"u16",
                "scale":1,
                "events":{
                    "on_change":0.0
                },
                "information":{
                    "max":true,
                    "min":true,
                    "avg":true,
                    "last":true,
                    "diff":true
                }
            },
            {
                "address":9001,
                "function":"ir",
                "name":"IR1ETH",
                "dtype":"u16",
                "scale":1,
                "events":{
                    "alarms":{
                        "hys":1.0,
                        "high":100.0,
                        "low":20.0
                    }
                },
                "information":{
                    "max":false,
                    "min":false,
                    "avg":true,
                    "last":true,
                    "diff":false
                }
            },
            {
                "address":900,
                "function":"ir",
                "name":"IR1ETH",
                "dtype":"u16",
                "scale":1,
                "information":{
                    "max":true,
                    "min":true,
                    "avg":true,
                    "last":false,
                    "diff":false
                }
            }
        ],
        "endianess":"big",
        "unitId":2
    }
]
```


In the example, the addition request is performed via a "Virtual Button", which contains the structured payload for the request topic.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data":{
        "data":{
            "code": 200
            "message": "Peripheral(s) added successfully",
            "service": "ResponsePeripheralsAdd",
            "success": true
        },
        "timestamp": 1745945556
    }
}
```


## Remove Peripherals

This function allows deleting an existing peripheral from the device by informing only the peripheral's name.

### Example Request

The request is made by publishing to the corresponding topic, sending a payload in the following format:

```
{"dispositivo" : ["API_Test"]}
```


The removal is performed via a "Virtual Button" configured to send the corresponding payload to the designated topic.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "data":{
        "code":200,
        "message":"Peripheral(s) removed successfully",
        "service":"ResponsePeripheralsRemove",
        "success":true
    },
    "timestamp":1730392564
}
```


## Serial Port Configuration

This function allows you to remotely configure the device's serial port (rs485). The function is able to set the following options:

 * Baud rate;
 * Data bits;
 * Stop bits;
 * Parity.

### Example Request

The request in the example is made through a "Virtual Button" containing a payload with the following message format:

```
{
    ...
    "interface": "rs485",
    "path": "/dev/ttyS0",
    "baud_rate": 38400,
    "data_bits": "8",
    "stop_bits": "1",
    "parity": "E"
    ...
}
```


### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "code":200
    "message": "Serial patch done."
    "service": "ResponseSerialSetup"
    "success": true
}
```


## Runtime Configuration

The runtime configuration of the device's MODBUS client can be performed by this function. The configurable parameters are:

 * Periodic readings report interval (s);
 * Limit of peripherals that can be connected simultaneously;
 * Interval between readings (ms);
 * Time between publication time checks (ms);
 * Slave device connection timeout (ms);
 * Limit of on-change publications within a periodic cycle;
 * Interval between on-change messages (s).

### Example Request

The request must contain at least one configuration to be changed in its payload; it is not necessary to inform the other variables.
An example of a request is shown below:

```
 {
    "report_period": 10,
    "peripherals_limit": 5
 }
```


In the example, the request is made through a "Virtual Button" containing the payload.

### Example Response

After the request, the MQTT Trigger configured for this topic will receive a payload with the following structure:

```
{
    "code":200,
    "message": "Runtime configuration updated.",
    "service": "ResponseRuntimeSetup",
    "success": true
}
```

## Setup

  1. Import this template into the WEGnology platform under the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish a Modbus connection on the device to facilitate visualization.

---

Copyright (c) 2025 WEGnology
