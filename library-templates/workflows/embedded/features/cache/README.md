# EEA : Cache

In this template, you will find how to use commands related to the device's cache, including manipulation and data retrieval. The cache can be used to store values for predefined periods within the device's RAM. After this period ends, the values are automatically removed from the cache. Additionally, the cache can also be used to share information between different system Workflows. The cache commands are:

 * cache_insert;
 * cache_insert_with_random_key;
 * cache_get;
 * cache_remove;
 * cache_pop;
 * cache_clear;
 * cache_capacity;
 * cache_count.

## Cache_insert

This function inserts a new item into the cache.

### How to use the function

To use this function, add a registered function node, enter "cache_insert" in the function name field, and in the inputs area provide:

 * The unique identification key (str);
 * The value to be stored (str);
 * Expiration time in seconds (u32).

This information can be provided via payload or predefined. In the example, the information is predefined.

The function's return consists only of the returnCode, if configured.

Note: The cache is shared among workflows. Be careful with key naming to avoid accidental overwriting.

## Cache_insert_with_random_key

This function inserts a new item into the cache using a randomly generated key.

### How to use the function

To use this function, add a registered function node, enter "cache_insert_with_random_key" in the function name field, and in the inputs area provide:

 * The value to be stored (str);
 * Expiration time in seconds (u32).

This information can be provided via payload or predefined. In the example, the information is predefined.

In the Outputs area, specify the payload where the information will be loaded, in string format with sufficient size.

### Example of Return

The following return was obtained using the registered function cache_insert_with_random_key:
"key" is the randomly generated key, and the "returnCode" field represents the operation return code.

```
"data":{
    "key": "Knvcg1ISEo3jp7vXBK9OrQQf"
    "returnCode": 0
}
```

## Cache_get

This function returns the value of a cache item, without removing it.

### How to use the function

To use this function, add a registered function node, enter "cache_get" in the function name field, and in the inputs area (string format), enter the unique identification key.
This information can be provided via payload or predefined.
In the example, the information is predefined.

In the Outputs area, specify the payload where the information will be loaded, in string format with sufficient size.

### Example of Return

The following return was obtained using the registered function cache_get:
The "value" field represents the cache value and the "returnCode" field represents the operation return code.

```
"data":{
    "value": "value60"
    "returnCode": 0
}
```

## Cache_remove

This function removes information from the cache.

### How to use the function

To use this function, add a registered function node, enter "cache_remove" in the function name field, and in the inputs area (string format), enter the unique identification key.
This information can be provided via payload or predefined.
In the example, the information is predefined.

The function's return consists only of the returnCode, if configured.

## Cache_pop

This function retrieves the next value from the cache and then removes it.

### How to use the function

To use this function, add a registered function node, enter "cache_pop" in the function name field, and execute.

In the Outputs area, specify the payload where the information will be loaded, in string format with sufficient size.

### Example of Return

The following return was obtained using the registered function cache_pop:
The "value" field represents the cache value, "key" is the unique cache key, and the "returnCode" field represents the operation return code.

```
"data":{
    "key": "wIzziXKwphwwN8VtvMeah7eR"
    "returnCode": 0
    "value": "value90"
}
```

## Cache_clear

This function forces all items to be removed from the cache, clearing it completely.

### How to use the function

To use this function, add a registered function node, enter "cache_clear" in the function name field, and execute.

The function's return consists only of the returnCode, if configured.

## Cache_capacity

This function returns the maximum number of items that can be stored in the cache, which depends on the hardware.

### How to use the function

To use this function, add a registered function node, enter "cache_capacity" in the function name field, and execute.

In the Outputs area, specify the payload where the information will be loaded, in u64 format with sufficient size.

### Example of Return

The following return was obtained using the registered function cache_capacity:
The "capacity" field represents the capacity value in u64, and the "returnCode" field represents the operation return code.

```
"data":{
    "capacity": 180
    "returnCode": 0
}
```

## Cache_count

This function returns the number of items currently present in the cache.

### How to use the function

To use this function, add a registered function node, enter "cache_count" in the function name field, and execute.

In the Outputs area, specify the payload where the information will be loaded, in u64 format with sufficient size.

### Example of Return

The following return was obtained using the registered function cache_count:
The "count" field represents the number of caches present in u64 and the "returnCode" field represents the operation return code.

```
"data":{
    "count": 2
    "returnCode": 0
}
```

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: Invalid information;
 * 101: cache access error;
 * 102: the provided buffer size for the output is insufficient;
 * 110: no space in cache.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
