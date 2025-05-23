# MODBUS : Events

This template presents the use of functions associated with the events available in the MODBUS API, including reading and interpreting the received payloads. Events are classified as:

 * Periodic;
 * On-change;
 * Alarms;
 * Errors.

## Periodic

These publications, sent periodically by the device, contain all configured information. Messages are sent by the API according to the interval defined on the device. The values published for each register are configurable through the peripherals.json file.

### Example Response

When publishing to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "data": {
        "<peripheral name>": {
            "id": "<peripheral wnology id>",
            "<register name 1>": {
            "avg":18.016666412353516,
            "diff":1.0,
            "last":19.0,
            "max":19.0,
            "min":18.0
            }
        }
    },
    "timestamp": 1712842180
}
```


## On-change

These publications occur when the measured value changes by the percentage configured on the device. The response format is similar to periodic publications, except for the trigger, which indicates which register was responsible for triggering the on-change publication.

## Alarms

The publication occurs when one of the configured values is exceeded. It is possible to configure the exceeding of an upper and/or lower limit, respecting a previously defined hysteresis. The response format is similar to periodic publications, except for the trigger, which indicates which register triggered the alarm publication.

## Errors

A publication occurs whenever an error is registered in the system. The main mapped error types are:

 * Communication error with Modbus device;
 * Timeout error when attempting communication with Modbus device;
 * Register reading error;
 * Timeout error when attempting to read the register;
 * No register to be read error;
 * Service not implemented error for MQTT requests.

### Example Response

Upon detecting an error, the MQTT Trigger registered to the error topic will receive a response in the following format:

```
{
    "errors": [
    "Mensagem de erro 1",
    "Mensagem de erro 2",
    ...
    ],
    "timestamp": 1712842180
}
```

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish a Modbus connection on the device to facilitate visualization.

---

Copyright (c) 2025 WEGnology

