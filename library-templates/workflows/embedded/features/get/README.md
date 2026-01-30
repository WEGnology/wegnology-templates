# EEA : Get

In this template, the use of the registered function get, available directly on the WEGnology platform, will be demonstrated. This function is intended to request system attributes and return the information to the user. The main information that can be obtained through this command includes:

 * Manufacturing details;
 * System statistics;
 * Connection networks;
 * Broker information;
 * Etc.

## Using the function

To use the function, you need to add a registered function node, enter "get" in the function name field, and in the inputs area as a string, specify the information to be returned. This information can be provided via a payload or be predefined. In the examples presented, the information was predefined.

The following commands can be used for input:

 * manufacturing-details;
 * broker-bridge;
 * system-statistics;
 * networks;
 * packages;
 * services.

In the Outputs area, you must specify the payload where the information will be loaded, in string format.

NOTE: It is necessary to previously set a character limit for the payload. If this limit is exceeded, the function will not return the desired information.

## Return Example

The following return was obtained through the "system-statistics" command in the registered "get" function.

```
"output":{
        "json":"{\"time\":1746191188,\"uptime\":8513,\"kernelVersion\":\"5.10.198-rockchip-standard\",\"cpuTemperature\":40.45,\"cpuUsage\":15.58,\"loadAverage\":0.71,\"diskUsage\":23,\"ramUsage\":26.309998}",
        "man":{
            "cpuTemperature":40.45,
            "cpuUsage":15.58,
            "diskUsage":23,
            "kernelVersion":"5.10.198-rockchip-standard",
            "loadAverage":0.71,
            "ramUsage":26.309998,
            "time":1746191188,
            "uptime":8513
        }
}
```

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: invalid input;
 * 101: data not available;
 * 102: the provided buffer size for the output is insufficient.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
