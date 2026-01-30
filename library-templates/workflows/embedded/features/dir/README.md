# EEA : DIR

In this template, the use of the registered directory-related functions, available directly on the WEGnology platform, will be demonstrated. These functions are intended to perform manipulations in the device's directory. The directory-related functions are:

 * read_dir;
 * dir_size;
 * create_dir;

## Read_dir

This function reads a specified directory, returning a list containing the files and subdirectories within the directory.

Note: The “size” and “created” attributes may not be available for some file types.  
Note: The size of subdirectories is not computed, always returning 4096.

### How to use the function

To use the function, you must add a registered function node, enter "read_dir" in the function name field, and in the inputs area (string format), specify the directory name to be read. This information can be provided via payload or predefined. In the example, the information is predefined.

In the Outputs area, you must specify the payload where the information will be loaded, in JSON format with sufficient size.

Note: You must previously set a character limit for the payload. If this limit is exceeded, the function will not return the desired information.

### Example of Return

The following return was obtained using the registered function read_dir: the "directory" list contains the files in the specified directory. The "returnCode" represents the operation return code.

```
 "data":{
        "directory":[
            {
                "created":1743687827,
                "is_dir":false,
                "name":"compress_test.txt",
                "size":0
            },
            {
                "created":1743590918,
                "is_dir":true,
                "name":"subdir2",
                "size":4096
            },
            {
                "created":1743529206,
                "is_dir":true,
                "name":"subdir1",
                "size":4096
            }
        ],
        "returnCode":0
    },
```

## Dir_size

This function measures a specified directory, returning the directory size in bytes.

Note: A valid path must be specified, otherwise the function will fail.

### How to use the function

To use the function, you must add a registered function node, enter "dir_size" in the function name field, and in the inputs area (string format), specify the directory name to be measured. This information can be provided via payload or predefined. In the example, the information is predefined.

In the Outputs area, you must specify the payload where the information will be loaded, in u64 format.

### Example of Return

The following return was obtained using the registered function dir_size. The "directory" list contains the files in the specified directory. The "returnCode" represents the operation return code.

```
 "data":{
        "size":
        "returnCode":0
    },
```

## Create_dir

This function creates a directory in the specified path and all its ancestor components if they do not exist.

Note: A valid path must be specified, otherwise the function will fail.

### How to use the function

To use the function, you must add a registered function node, enter "create_dir" in the function name field, and in the inputs area (string format), specify the directory name to be created. This information can be provided via payload or predefined. In the example, the information is predefined.

The function's return consists only of the returnCode, if configured.

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes can be obtained:

 * 0: operation successful;
 * 100: invalid path;
 * 102: the provided buffer size for the output is insufficient.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.

## Observations

The template starts by creating a directory on the device, allowing it to be read with the reading function.

---

Copyright (c) 2025 WEGnology
