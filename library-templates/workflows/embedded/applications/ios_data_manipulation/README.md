# IOs : Data Handling

This template demonstrates the use of functions related to data handling and acquisition in the IOs API. The example is organized into the following sections:

 * Counter reset;
 * Output activation;
 * Multiple outputs activation;
 * Inputs.

## Counter Reset

Performs the reset of counters configured for inputs designated as counters. The reset can be performed using an object containing either the user-defined custom name ("name") or the hardware default name ("ref_name").

### Example Request

To make a reset request, you must post to the request topic a payload with the following structure:

```
{"msg":
    {
     "ref_name":"DI1"
    }
}
```

In this example, the reset request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

{
    "ref_name": "DI1",
    "result" : {
        "success" : true,
    }
}

## Output Activation

This API function changes the state of the digital output to on or off, depending on the payload sent.

### Example Request

To make a state change request, you must post to the request topic a payload with the following structure:

```
{
    "msg":{
        "ref_name":"OUT0",
        "active":true
    }
}
```

In this case, the request aims to change the digital output state to on. If the goal was to turn it off, set the "active" variable to "false".
In the example, the change request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "ref_name":"OUT0",
    "active":true,
    "result":{
        "success":true
    }
}
```

## Multiple Outputs Activation

This API function allows changing the states of digital outputs to on or off, as per the payload sent. The message format is similar to that used for a single output, with the difference that in this case, an array is sent containing all the outputs to be changed.

## Inputs

The function returns a list containing the configured inputs and their respective values, along with the values of their counters, whenever requested. The request is made by publishing an empty payload to the related topic.

### Example Response

```
{
    [
        {
            "active":true,
            "name":"myInput0",
            "ref_name":"DI0"
        },
        {
            
            "active":true,
            "name":"myInput1",
            "ref_name":"DI1",
            "counter": 17
        },
    ]
}
```

## Setup

  1. Import this template into the WEGnology platform under the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Establish an IOs connection on the device and configure it to facilitate visualization.

---

Copyright (c) 2025 WEGnology
