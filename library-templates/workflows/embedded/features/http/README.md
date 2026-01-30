# EEA : HTTP POST

In this template, the use of the registered function http_post, available directly on the WEGnology platform, will be demonstrated. This function is intended to perform HTTP requests using the POST method.

## Using the function

To use the function, you need to add a registered function node, enter "http_post" in the function name field, and in the inputs area, provide the following information:

 * header0: Header to include in the request;
 * header1: Header to include in the request;
 * header2: Header to include in the request;
 * body: Data to send in the request;
 * uri: Request URI.

This information can be provided via a payload or be predefined. In the example presented, the information was provided via a payload.

In the Outputs area, it is necessary to define a responseCode with u16 format, which represents the response code, and a responseContent in string format, which corresponds to the response content of the request.

## Response Example

The following return was obtained through the registered function http_post, containing the responseCode equal to "200" indicating success and responseContent of the requested page.

```
"data":{
    "responseCode": 200
    "responseContent": "{\"args\":{},\"data\":\"Teste=teste\",\"files\":{},\"form\":{},\"headers\":{\"host\":\"postman-echo.com\",\"x-request-start\":\"t1746200680.758\",\"connection\":\"close\",\"content-length\":\"11\",\"x-forwarded-proto\":\"https\",\"x-forwarded-port\":\"443\",\"x-amzn-trace-id\":\"Root=1-6814e868-3061bc8a371079a758d318ee\",\"accept\":\"*/*\",\"content-type\":\"application/json\"},\"json\":null,\"url\":\"https://postman-echo.com/post\"}"
}
```

## Possible returnCode

The function's return can be configured in a payload to be sent to the user. The following codes may be obtained:

 * 0: operation successful;
 * 100: invalid URI;
 * 101: failed to send the request;
 * 102: the provided buffer size for the output is insufficient;
 * 103: failed to process response;
 * 104: invalid file path for upload;
 * 105: failed to read the file for upload.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to perform the tests.
---

Copyright (c) 2025 WEGnology
