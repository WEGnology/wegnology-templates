# EEA : Compress File

In this template, the use of the registered function compress_file, available directly on the WEGnology platform, will be demonstrated. This function is intended to compress files on the device.

## How to use the function

To use the function, you need to add a registered function node, enter "compress_file" in the function name field, and in the inputs area, provide the following information:

 * The path of the file to be compressed (input_file), in string format;
 * The path of the file that will be generated after compression (output_file), also in string format;
 * A boolean value (keep) indicating whether the input file should be retained after compression (True for yes or False for no).

This information can be provided via payload or predefined. In the example, the information is provided via payload.

The function's return consists only of the returnCode, if configured.

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: invalid path;
 * 101: unsupported compression format;
 * 102: input path does not exist in the system;
 * 103: failed to read input file;
 * 104: failed to create output file;
 * 105: failed to generate compressed file;
 * 106: failed to remove input file.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
