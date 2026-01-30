# EEA : String Compression and Base64 Conversion

In this template, the use of the registered functions for compressing a string and converting a hexstring to base64, available directly on the WEGnology platform, will be demonstrated. The functions are divided as follows:

 * compress_string;
 * decompress_string;
 * hexstr_to_base64;

## Compress_string

This function compresses a string using the zstd algorithm and returns the result in base64 format.

### How to use the function

To use the function, you must add a registered function node, enter "compress_string" in the function name field, and in the inputs area (string format), provide the information to be compressed. This information can be provided via payload or predefined. In the example, the information is predefined.

In the Outputs area, you must specify the payload where the information will be loaded, in string format with sufficient size.

Note: You must previously set a character limit for the payload. If this limit is exceeded, the function will not return the desired information.

### Example of Return

The following return was obtained using the registered function compress_file:
In data, "string" is the original message to be compressed, while "compressed" refers to the compressed message. The "returnCode" field represents the operation return code.

```
"data":{
    "compressed": "KLUv/QBYOQAAZXhlbXBsbw=="
    "returnCode": 0
    "string": "exemplo"
}
```

### Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes can be obtained:

 * 0: operation successful.
 * 100: failed to compress data.
 * 102: the provided buffer size for the output is insufficient.

## Decompress_string

This function decompresses a string that was compressed by the "compress_string" function, returning a decompressed string.

### How to use the function

To use the function, you must add a registered function node, enter "decompress_string" in the function name field, and in the inputs area (string format), provide the string to be decompressed. This information can be provided via payload or predefined. In the example, the information is provided via payload.

In the Outputs area, you must specify the payload where the information will be loaded, in string format with sufficient size.

### Example of Return

The following return was obtained using the registered function decompress_string:
"compressed_var" is the string to be decompressed, while "decompressed" is the decompressed string. The "returnCode" field represents the operation return code.

```
"data":{
    "compressed_var": "KLUv/QBYOQAAZXhlbXBsbw=="
    "decompressed": "exemplo"
    "returnCode": 0
}
```

### Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes can be obtained:

 * 0: operation successful.
 * 102: the provided buffer size for the output is insufficient.

## Hexstr_to_base64

This function encodes a hexstring to base64, returning a string containing the message in base64.

### How to use the function

To use the function, you must add a registered function node, enter "hexstr_to_base64" in the function name field, and in the inputs area (string format), provide the hexadecimal message (as a string) to be encoded. This information can be provided via payload or predefined. In the example, the information is sent via payload.

In the Outputs area, you must specify the payload where the information will be loaded, in string format with sufficient size.

### Example of Return

The following return was obtained using the registered function hexstr_to_base64:
"hexstr" is the message to be encoded to base64, "base64" is the resulting base64 string, and "output" is the decoded message. The "returnCode" field represents the operation return code.

```
"data":{
    "base64": "ZXhlbXBsbw=="
    "hexstr": "6578656d706c6f"
    "output": "exemplo"
    "returnCode": 0
},
```

### Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes can be obtained:

 * 0: operation successful.
 * 100: not a valid hexstring.
 * 102: the provided buffer size for the output is insufficient.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
