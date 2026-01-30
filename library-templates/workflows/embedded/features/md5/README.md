# EEA : MD5

In this template, the use of the registered function md5sum, available directly on the WEGnology platform, will be demonstrated. This function is intended to generate the MD5 hash of any string entered in the "input" field.

## Using the function

To use the function, you need to add a registered function node, enter "md5sum" in the function name field, and in the inputs area as a string, specify the string to be hashed. This information can be provided via a payload or be predefined. In the example presented, the information was provided via a payload.

In the Outputs area, you must specify the payload where the information will be loaded, in string format.

NOTE: It is necessary to previously set a character limit for the payload. If this limit is exceeded, the function will not return the desired information.

## Return Example

The following return was obtained through the registered function md5sum: the variable "hash" contains the "password" after encoding, while "returnCode" represents the operation's return code.

```
"data"{
    "hash":"d41d8cd98f00b204e9800998ecf8427e"
    "returnCode": 0
    "senha": "senha@123"
}
```

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 102: the provided buffer size for the output is insufficient.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
