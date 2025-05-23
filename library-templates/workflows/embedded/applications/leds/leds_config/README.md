# LEDs : LEDs Configuration

This template presents the use of functions associated with the LEDs present on the device, through the LEDs API. The functions available in this API are:

 * Error events;
 * Available user LEDs;
 * Toggle LEDs;
 * Set LED state;
 * Blink LEDs;
 * Unconfigure LEDs.

## Error Events

In this API function, error messages related to LEDs that occur during device execution are captured. These messages are published to a specific topic for events.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "errors":[
        "Mensagem de erro 1",
        "Mensagem de erro 2",
        "..."
    ],
    "timestamp":1712842180
}
```


## Available User LEDs

Requesting available user LEDs consists of asking for the tags corresponding to the user LEDs present in the system. This request is made by sending an empty payload to the respective topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "data":{
        "code":200,
        "message":{
            [
                "LED1:green",
                "LED1:red",
                "LED2:red",
                "LED3:green",
                "LED3:red"
            ]
        },
        "service":"RequestUserLeds",
        "success":true
    },
    "timestamp":1712842180
}
```

## Toggle LEDs

This function allows toggling the current state of one or more LEDs by sending a payload containing an array called "leds" with the tags of the LEDs to be toggled.

### Example Request

To make a toggle request, post to the request topic a payload with the following structure:


```
{
    "leds":[
        {
            "tag":"LED:green"
        },
        {
            "tag":"LED:red"
        },
        "..."
    ]
}
```

In this example, the toggle request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "data":{
        "code":200,
        "message":"Led [LED:green] toggled.",
        "service":"RequestLedToggle",
        "success":true
    },
    "timestamp":1712842180
}
```

## Set State

This function allows you to set the state of one or more LEDs to "on" or "off" by sending a payload with an object called "leds", containing the LED tag and the state to be set, to the respective topic.

### Example Request

To make a set state request, post to the request topic a payload with the following structure:

```
{
    "leds":[
        {
            "tag":"LED:green",
            "state":"on"
        },
        {
            "tag":"LED:red",
            "state":"off"
        }
    ]
}
```

In this example, the set state request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "data":{
        "code":200,
        "message":"Led [LED:green] set to 'on' state.",
        "service":"RequestLedSet",
        "success":true
    },
    "timestamp":1712842180
}
```

## Blink LEDs

This function allows configuring one or more LEDs to blink at a specific frequency by sending a payload with an object called "leds", containing the LED tag and the interval time between "on" and "off" states.

### Example Request

To make a blink request, post to the request topic a payload with the following structure:

```
{
    "leds":[
        {
            "tag":"LED:green",
            "blinkInterval":500
        },
        {
            "tag":"LED:red",
            "blinkInterval":500
        },
        "..."
    ]
}
```

In this example, the blink request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:


```
{
    "data":{
        "code":200,
        "message":"Led [LED:green] is blinking.",
        "service":"RequestLedBlink",
        "success":true
    },
    "timestamp":1712842180
}
```

## Unconfigure LEDs

LEDs can have their configurations removed easily with this function. The selected LED will be set to "off" and the trigger will be adjusted to "none". For this, simply send a payload containing an object called "leds", with the tag of the LED to be unconfigured.

### Example Request

To make an unconfigure request, post to the request topic a payload with the following structure:

```
{
    "leds":[
        {
            "tag":"LED:green"
        },
        {
            "tag":"LED:red"
        },
        "..."
    ]
}
```

In this example, the unconfigure request is made via a "Virtual Button" containing the structured payload for the request topic.

### Example Response

When a message is published to the topic, the MQTT Trigger configured for this topic will receive a message structured as follows:

```
{
    "data":{
        "code":200,
        "message":"Led [LED:green] set to 'none'.",
        "service":"RequestLedNone",
        "success":true
    },
    "timestamp":1712842180
}
```

NOTE: The command will send a number of responses equal to the number of specified LEDs.

## Setup

  1. Import this template into the WEGnology platform in the Embedded Workflows section.
  2. Deploy the example to the device.
  3. Use the "Virtual Button" to run the tests.

---

Copyright (c) 2025 WEGnology
